### Chapter 17 – Providing Internet Access to Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Learn key remote access scenarios and when to apply them.
* Provide remote access to your Microsoft® Visual Studio® 2005 Team Foundation Server (TFS) over the Internet.
* Improve remote access performance by using the Team Foundation Server Proxy.

### Overview
This chapter explains how to provide remote access to TFS over the Internet. You can choose from one of the following three options in order to provide remote access:
* You can provide access to TFS over a virtual private network (VPN).
* You can provide access to TFS through a reverse proxy such as Microsoft Internet Security and Acceleration (ISA) Server.
* You can host your TFS server on an extranet.

Versions of TFS prior to Service Pack 1 (SP1) support only VPN access. TFS SP1 adds support for Basic authentication. This enables the extranet and reverse proxy solutions as well as VPN.
**How to Use This Chapter**
Use this chapter to set up your TFS server for remote access over the Internet. To gain the greatest benefits from this chapter, you should:
* **Use the scenarios list.** Consult the scenarios list to determine quickly which approach you should adopt to provide external Internet access to your server.
* **Use the referenced walkthroughs.** Use the walkthroughs in this chapter for step-by-step guidance on installing and configuring the certificates and Secure Sockets Layer (SSL) access to be used with Basic and Digest authentication.
* **Use the “Improving Remote Access Performance” section.** Read the “Improving Remote Access Performance” section**** to identify ways to reduce the amount of traffic that needs to be sent over the Internet.

### Key Strategies
The following are solution strategies for providing remote access to a TFS server:
* **Use a VPN connection.** Your TFS sits inside the internal network, and external users access it over a VPN. Internal users access a TFS directly.
* **Publish your TFS through a reverse proxy.** Your TFS sits inside the internal network, and one or more reverse proxy machines, such as ISA Server, bring in client requests from the Internet to your TFS.
* **Locate your TFS in the extranet (“hosted scenario”).** Only external clients access your TFS, and it is located outside of the firewall on an extranet.

### Common Scenarios
* **Remote office.** If you are supporting remote users with VPN access, use the VPN solution. This is the easiest solution to enable, provides well-understood security, allows remote access to all TFS features, and allows you to use the TFS Proxy to improve performance.
* **Offshore team.** If you are supporting remote users without VPN access or without access to the domain, use the reverse proxy scenario. This solution is more difficult to set up, but it enables remote users to access an internally located TFS without the need for VPN.
* **Hosted community.** If you are supporting a set of remote users who will be using a TFS installation dedicated to their use, such as a community development site, use the extranet scenario. This solution gives you the most separation between the remote users and your internal network resources.

### Using a VPN connection
[Image:Fig17.1.GIF)(Image_Fig17.1.GIF) 

With this approach, your remote development team uses a direct VPN connection to your TFS on your internal network. If you have TFS without SP1, or if you require Integrated Windows authentication, then using a VPN connection is your only option. TFS is designed to work in low-bandwidth situations, such as VPN access, and provides acceptable performance when used in this scenario.

#### Advantages
* All TFS features work, including the TFS Proxy.
* This approach supports the use of Integrated Windows authentication and enables you to leverage existing enterprise infrastructure.
* If you already have a VPN set up, this is the easiest solution to adopt.

#### Disadvantages
* A VPN solution might not be set up for your infrastructure, or might not be available to your remote users.

For more information about creating a VPN, see [http://support.microsoft.com/kb/324747](http://support.microsoft.com/kb/324747).

### Publishing TFS Through a Reverse Proxy
With this approach, you install a TFS server on your internal network and use the ISA Server Web publishing functionality to expose it to the external network. Remote users access TFS over SSL and use Basic authentication. This option will not work unless you have TFS SP1 installed.

#### Networks without a domain controller on the perimeter

[Image:Fig17.2.GIF)(Image_Fig17.2.GIF)

If you do not have a domain controller on your perimeter network, you can open a port on the firewall to allow a Lightweight Directory Access Protocol (LDAP) connection from the ISA Server to your internal domain controller, specifically to authenticate external TFS users.

#### Networks with a domain controller on the perimeter 

[Image:Fig17.3.GIF)(Image_Fig17.3.GIF)  
If you do have a domain controller on your perimeter network, remote users can authenticate directly against the perimeter domain controller. One-way trust between the internal and perimeter domain controllers allows external users to access the TFS server. Internal users access the TFS server directly, using Integrated Windows authentication. 

##### Advantages
* Reverse proxies, such as ISA Server, authenticate users and inspect traffic.
* Your remote users do not need access to the domain.
* Your remote users do not need VPN access.

##### Disadvantages
* You cannot use the TFS Proxy at the remote location.
* Your remote users cannot add users to TFS groups.
* Your remote users cannot add Microsoft Active Directory® groups to folders in source control.
* Your remote users will not be able to initiate or manage builds remotely.
* Your remote users cannot create new team projects.
* Your remote users cannot publish test results to your TFS.

**Note**: Whenever you use Basic authentication, use SSL. Basic authentication transmits credentials in clear text. Use SSL to protect this information.

### Locating TFS in an Extranet (“Hosted Scenario”)
[Image:Fig17.4.GIF)(Image_Fig17.4.GIF)
   
With this approach, you install your complete TFS infrastructure?both application tier and data tier?inside your perimeter network, off of your internal intranet. All connections to your TFS come over the Internet, whether they are from external or internal users. TFS can work with or without a domain controller (DC). If your perimeter network does not have access to a DC, the Active Directory service features of TFS will not work. For example, adding users to TFS groups, or adding an Active Directory group to folders in source control, will not work without a DC. This option will not work unless you have TFS SP1 installed.

#### Advantages
* Your TFS users are cleanly segregated from your internal network.
* Your remote users do not need access to the domain.

#### Disadvantages
* You cannot use the TFS Proxy at the remote location.
* Your remote users cannot initiate or manage builds.
* Your remote users cannot create new team projects.
* Your remote users cannot publish test results to the TFS.
* Internal users must connect to the extranet TFS over SSL just like external users.

**Note:** Whenever you use Basic authentication, use SSL. Basic authentication transmits credentials in clear text. Use SSL to protect this information.

### Basic Authentication / SSL
If you are using TFS SP1 and want to support the extranet or reverse proxy scenario, you need to enable Basic authentication over SSL by configuring IIS on your TFS application tier. With Basic authentication, logon credentials are passed over the Internet using an unprotected Base64 encoded format. To protect your client’s credentials, use only Basic authentication over a Secure HTTP (HTTPS) connection that uses SSL.

Use an Internet Server API (ISAPI) filter so that remote clients connect using Basic authentication over SSL, while local clients still connect using Integrated Windows authentication. The ISAPI filter looks for clients that you have configured as “external/Internet” and strips out NTLM authentication on the 401 response to force these clients to use other authentication methods, such as Basic authentication.

#### More information
* For more information about how to configure your TFS server to require Basic authentication and HTTPS over remote connections, see “Walkthrough: Setting up Team Foundation Server to Require HTTPS and Secure Sockets Layer (SSL)” at +http://msdn2.microsoft.com/en-us/library/aa833873(VS.80).aspx+
* For more information about setting up the ISAPI filter, see “Walkthrough: Setting up Team Foundation Server with Secure Sockets Layer (SSL) and an ISAPI Filter” at +http://msdn2.microsoft.com/en-us/library/aa833872(VS.80).aspx+
* For more information about ISAPI filters for TFS, see James Manning’s blog post “The TFS extranet ISAPI filter mechanics” at [http://blogs.msdn.com/jmanning/archive/2006/10/27/the-tfs-quot-extranet-quot-isapi-filter-mechanics.aspx](http://blogs.msdn.com/jmanning/archive/2006/10/27/the-tfs-quot-extranet-quot-isapi-filter-mechanics.aspx)

### Team Foundation Server Proxy
 
[Image:Fig17.5.GIF)(Image_Fig17.5.GIF)
The TFS Proxy is not required to enable remote access but is an optional cache for source control files. To help improve the performance that your remote team experiences, you can install a TFS Proxy in remote offices that connect to your TFS through a VPN. This improves performance by caching source control files on the remote office’s proxy server. Whenever the remote client needs access to source code in the source control repository, it will request the source from the TFS Proxy. The proxy will then return a local version from its cache if it is available. If the source is not in the cache, the proxy will request the source from the remote TFS server. This reduces network traffic and improves source control responsiveness at the remote location.

#### Tips to improve proxy performance
Consider the following recommendations for improving proxy performance:
* Ensure that caching is enabled, and monitor the performance of your cache. Monitor the performance counters (installed by default) and event logs (for errors and warnings) on your proxy server regularly, to see how your proxy is performing. Note that the TFS Proxy saves cache performance statistics to an Extensible Markup Language (XML) file named ProxyStatistics.xml, and that you can change the interval for saving these statistics. The ProxyStatistics.xml file is located in the App_Data folder in the proxy installation directory.
* Run a scheduled task regularly to retrieve the latest files to the proxy server. This helps to ensure that the latest versions of the files are available in the proxy cache, and that subsequent client requests for these files result in a cache hit.
* If you know that large files are going to be downloaded over a low-bandwidth (< 3 megabits per second [Mbps](Mbps)) network, set the **executionTimeout** configuration to an appropriate value in Web.config. The default value is one hour <httpRuntime executionTimeout="3600"/>.
* If the proxy is going to be down for an extended time, disable the proxy on the clients to prevent fruitless reconnections. By default, reconnections are attempted every five minutes.
* Consider using workspace cloaking to hide specific workspaces from being viewed and to prevent unnecessary file transfers. Cloaking hides specified workspace folders from view, increases performance bandwidth, and conserves local disk space by preventing folders and files that you do not currently need from being copied to your local workspace. Although you can cloak an existing folder mapping in your workspace, a better approach is to create a new folder mapping that is specifically intended to be cloaked.

For more information about these performance optimization guidelines, see “Distributed / Remote Development” in “Guidelines: Source Control Guidelines” in this guide.

#### Mirrored Accounts
The TFS Proxy is supported in remote offices only over a VPN connection. However, if you have deployed your TFS using the extranet or reverse proxy scenario for a small remote team that requires the TFS Proxy, you can use mirrored accounts to enable the proxy.

To enable the proxy, you can use workgroup accounts with matching usernames and passwords on the TFS, the TFS Proxy, and each of the remote client computers. The fact that you need to maintain the exact username/password match for all users in three different locations increases administration time and restricts this workaround to small remote teams.

##### More information*
* To learn more about the TFS Proxy, see “Team Foundation Server Proxy and Source Control” at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)
* For more information about managing the TFS Proxy, see “Managing Remote Connections to TFS Proxy” at [http://msdn2.microsoft.com/en-us/library/ms253156(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms253156(VS.80).aspx)
* For more information about troubleshooting the TFS Proxy, see “Troubleshooting TFS Server Proxy” at [http://msdn2.microsoft.com/en-us/library/ms400681(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400681(VS.80).aspx)

### Remote Build Server

[Image:Fig17.6.GIF)(Image_Fig17.6.GIF) 

To improve remote team performance further, you can set up a build server in the remote office. If you have a TFS Proxy installed in the remote office, it will act like any other source control client and get code from the proxy before each build. A remote build server has the following advantages:
* Team builds from the remote team impact that team’s build server, rather than increasing load on the internal build server.
* Remote builds provide binaries to the remote team, without the need to transmit the binaries over the network.

Don’t use the remote build server as a complete replacement for builds generated on the internal build server. Even if the remote build is generated from the same source code version as the internal build, you might see different behavior because of build or source configuration differences between the servers.  As a guideline, base important testing on the internal build, especially when you’re nearing a release.    

**Note:** The application tier communicates with the build server on port 9191. If you have a remote build server, set up your firewall so that the application tier can connect on this port.

### Summary 
If you are using TFS without SP1, use a VPN to provide remote access. If you are using TFS SP1, then you can use Basic authentication over SSL to locate your TFS in your extranet, or you can give access through a reverse proxy.

If you want to improve remote access performance, especially in the VPN scenario, you can install and configure the TFS Proxy to cache source control files in the remote location.

### Additional Resources
* For more information about setting up TFS for remote development, see “Walkthrough: Setting up TFS for a Remote Development Location” at [http://msdn2.microsoft.com/en-us/library/ms242919(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242919(VS.80).aspx)
* For more information about setting up TFS with SSL, see “Walkthrough: Setting up Team Foundation Server with Secure Sockets Layer (SSL)” at [http://msdn2.microsoft.com/en-us/library/ms242875(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242875(VS.80).aspx)
* For more information about TFS Basic and Digest authentication, see “Team Foundation Server, Basic Authentication, and Digest Authentication” at [http://msdn2.microsoft.com/en-us/library/aa833874(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa833874(VS.80).aspx)
* For more information about the TFS Proxy, see “Team Foundation Server Proxy and Source Control” at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)
* For more information about managing the TFS Proxy, see “Managing Remote Connections to TFS Proxy” at [http://msdn2.microsoft.com/en-us/library/ms253156(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms253156(VS.80).aspx)
* For more information about troubleshooting the TFS Proxy, see “Troubleshooting TFS Server Proxy” at [http://msdn2.microsoft.com/en-us/library/ms400681(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400681(VS.80).aspx)
* For more information about examining TFS Proxy performance, see [http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx)