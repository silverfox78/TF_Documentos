### Chapter 18 - What’s New in Visual Studio Team System 2008 Team Foundation Server 
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

Microsoft® Visual Studio® Team System 2008 Team Foundation Server introduces a number of new features and capabilities. The primary changes have been:
* **Administration, Operations & Setup.** Team Foundation Server 2008 installation has been simplified to reduce setup time and improved to support more deployment scenarios.
* **Build.** Team Foundation Server 2008 build includes Continuous Integration, scheduled builds, and build queuing solutions out of the box. Build management and extensibility has been simplified with more functionality available from the UI.
* **Version Control.** Team Foundation Server 2008 version control includes much better support for offline work and has improved performance.
* **Work Item Tracking.** Team Foundation Server 2008 work item tracking includes an improved query builder and improved support for work item attachments.

These product changes are listed and briefly described below, followed by a table explaining how the changes will impact the guidance in this guide. Use this chapter to aid in your Microsoft Visual Studio Team Foundation Server upgrade planning.

### Administration, Operations & Setup
# **Simplified installation –** Team Foundation Server 2008 installation is made easier and quicker compared to Visual Studio 2005 TFS. Improvements include the elimination of the separate data-tier installation as well as the elimination of the domain account requirement. Team Foundation Server 2008 supports built-in machine accounts (such as Network Service) wherever possible. 
# **Support for SharePoint 2007 –** Team Foundation Server 2008 adds support for SharePoint 2007 and Windows SharePoint Services 3.0. Team Foundation Server 2008 will support SharePoint on a separate server from the Team Foundation Application Tier Server. 
# **Support for Windows Server 2008** – Team Foundation Server 2008 will support the next version of Microsoft Windows Server™; for example  Microsoft Windows Server 2008 and Internet Information Services (IIS) 7.0. 
# **Support for X.509 Client Certificates** – Team Foundation Server 2008 will support the use of X.509 client certificates to improve authentication security.
# **Large group synchronization** – Team Foundation Server 2008 improves performance and robustness and will be able to support large numbers of users — approximately 30,000 or more users in a single instance of TFS.
# **Support for SQL named instances –** Team Foundation Server 2008 allows sharing of a SQL Server between multiple TFS instances, or with other applications. This allows different instances of TFS to use the same installation of SQL Server 2005.
# **Support for non-default ports –** Team Foundation Server 2008 has improved configurability to support alternate Web sites and ports.  

### Build 
# **Continuous Integration** **builds –** Team Foundation Server 2008 supports the creation of build triggers that allows you to configure exactly when Continuous Integration builds should be started. For example, you can set a trigger so that every check-in starts a build, or you can set up a rolling build so that builds will start no more often than every X minutes. 
# **Support for build queuing** – Team Foundation Server 2008 supports build queuing and queue management. This is especially useful for Continuous Integration as multiple check-ins may queue up multiple builds.
# **Scheduled builds –** Team Foundation Server 2008 supports scheduled builds, which can be configured to start at specified times based on your organization’s requirements. 
# **Drop management –** Team Foundation Server 2008**** supports drop management, which gives you the ability to set policies for when builds should be automatically deleted.
# **Specify build properties -** Team Foundation Server 2008 allows you to specify what source and versions of source should be built along with other build properties for a build type. There are many more exposed properties for customizing a build. Additionally, MSBuild command-line parameters can be passed when queuing builds.
# **Extensibility of build targets –** Team Foundation Server 2008 improves extensibility of the build targets. For example, you now have the ability to easily execute targets before and after each Visual Studio solution or project is built. 
# **Build management –** Team Foundation Server 2008 allows you to stop and delete builds from within Visual Studio. 
# **Build configuration –** Team Foundation Server 2008 has simplified the ability to specify what tests get run as part of a build. 
# **Build project file location flexibility –** Team Foundation Server 2008 provides the ability to store the MSBuild project file (and its associated rsp file) anywhere in the version control hierarchy instead of forcing the use of the **TeamBuildTypes** folder.
# **Support for GUI tests –** Team Foundation Server 2008 now allows running graphical user interface (GUI) tests as part of the build. 
# **Check-in Policy –** Team Foundation Server 2008 now supports a new check-in policy, which prevents users from checking-in code when a Continuous Integration build is broken.
# **Managing build server** – Team Foundation Server 2008 has an improved ability to manage multiple build machines.
# **Workspace mapping** – Build definition can be associated with a “real” workspace in Team Foundation Server 2008, meaning code from multiple team projects can be retrieved, client mappings can be specified, etc. Working folder mappings will be managed in the GUI instead of in workspacemapping.xml

### Version Control 
# **Annotate –** Team Foundation Server 2008 supports an annotation feature that allows your developers to inspect a source code file and see line-by-line-level detail about who last changed each section of code. 
# **Folder Diff** – Team Foundation Server 2008 supports comparing of folders where the contents of the folder are recursively compared in order to identify files that differ. Folder Diff can compare local folders to local folders, local folders to server folders, and server folders to server folders. 
# **Destroy –** Team Foundation Server 2008 supports the Destroy feature with the ability to remove files and folders from the version control system. The destroyed files and folders cannot be recovered after they have been destroyed.
# **Get Latest On Checkout –** Team Foundation Server 2008 now has an option for downloading the latest version of the file while checking it out. 
# **Workspace wild card mappings –** Team Foundation Server 2008 now allows mapping of a folder or file under a cloaked folder and wildcard mappings so that you can map all files in a folder without mapping sub folders.  
# **Performance improvements –** A variety of version control performance enhancements have been made in Team Foundation Server 2008, improving all aspects of version-control performance. Although the gains for smaller servers/projects (< 10,000 files) will be modest, the gains for larger projects (particularly where the file count approaches hundreds of thousands) will be substantial. 
# **Team Foundation Server 2008** **command line Help –** Team Foundation Server 2008 now supports the ability to get command line Help for the _+tf_+ tool. You get the Help by running "_tf help_" and obtain Help for individual commands by running "_tf_ _command_ _/help_". 
# **Offline improvements –** Team Foundation Server 2008 has significantly improved the experience of going offline and has integrated the _tfpt_ online capability into the Visual Studio Integrated Development Environment (IDE) for going back online.  
# **Check-in override information captured –** Team Foundation Server 2008 supports adding check-in policy overrides to the warehouse.

### Work Item Tracking 
# **Attachments improvements –** Team Foundation Server 2008 has drag-and-drop support for adding an attachment and allows multi-select for attaching files. 
# **Query Builder –** Team Foundation Server 2008 has improved the Query Builder usability in the following ways:
## Drop-down filtering is now based on the current project
## Improved MRU lists 
## Column drag-and-drop
## SHIFT + click mouse-based multi-column sorting

### Compatibility Issues with Visual Studio 2005 Team System 
The Team Foundation Server 2008 client is able to work with a Visual Studio 2005 Team Foundation Server and a Visual Studio 2005 client is able to work with a Team Foundation Server 2008 server, except for the following compatibility issues. 
# **Visual Studio add-ins –** Client-side Visual Studio add-ins will need to be recompiled (or have their policy changed) because the Team Foundation Server Object Model (TFSOM) assembly versions will change and add-ins will need to bind to the new assemblies.  
# **Team builds –** Most build operations ¬? such as listing build definitions, starting and stopping builds and examining build reports will work with the combination of Visual Studio 2005 TFS and Team Foundation Server 2008 clients and server. The following are the known issues:
# A Team Foundation Server 2008 server will only work with a Team Foundation Server 2008 build server. 
# For a Visual Studio 2005 client to start a build on an Team Foundation Server 2008 server, the build definition needs to be stored at $/<TeamProject>/TeamBuildTypes/<name>.  
# Changes made to properties in the tfsbuild.proj file that are in the database in Team Foundation Server 2008 will not be updated in the database and will no longer be in sync. 
# When working with the Continuous Integration feature in Team Foundation Server 2008, the Visual Studio 2005 client will be able to start a build, but it will not be able to queue a build, see the list of builds in the queue, see the list of build agents, etc. 
# A new build type cannot be created on a Visual Studio 2005 TFS server, using a Team Foundation Server 2008 client. 
# Parameters in the dialog for starting a build on Visual Studio 2005 Team Foundation Server cannot be changed when using a Team Foundation Server 2008 client.

### Impact on the Guidance
||**Guidance for Team Foundation Server 2005**	||**Guidance for Team Foundation Server 2008**||
||Dual server deployment will support up to 2000 users.	||You can use dual server deployment to support up to 30,000 users||
||Users need correct domain accounts as part of deployment.	||Domain accounts are no longer required, instead you can use the built in machine accounts, such as Network Service account.||
||Use a custom solution to create Continuous Integration builds.	||You can use Visual Studio build triggers to create and configure Continuous Integration builds or Rolling builds. ||
||Use automated tests as part of your build to measure the quality of the build. 	||It’s easier to build test lists and specify what tests get run as part of a build step. It’s possible to run GUI tests as part of your automated build tests. ||
||Build types must be placed in a specific folder in order for them to be recognized by Team Build.	||Build definition project files (tfsbuild.proj) can be stored anywhere in the version control hierarchy.||
||Use a custom solution to create Scheduled Builds. 	||You can create Visual Studio scheduled builds without the need for a custom solution.||
||There are a set of check-in policies available out-of-box.	||A new check-in policy is available for broken CI builds. This prevents check-in of code while the CI build is broken.||
||Use the tool converter.exe to migrate from VSS to Team Foundation Server.	||Use the Visual Studio toolkit for building conversion and mirroring solutions between Team Foundation Server and other source control systems – including VSS.||
||Use workspace mapping to define the set of files you want synchronized to your local machine.	||Team Foundation Server 2008 now allows mapping of a folder or file under a cloaked folder, and wildcard mappings so that you can map all files in a folder without mapping sub-folders. ||
||Use workspacemapping.xml file to modify workspace mapping.	||The Team Foundation Server 2008 GUI is used to manage workspace mapping, workspacemapping.xml is no longer used.||
||Use the TFS Power Tool to work offline. 	||Use the Visual Studio IDE for working offline.||
||Getting the latest version of a file and checking it out for edit are two separate source control operations.	||You can use an option, to automatically get the latest version of a file when you check it out for edit.||
||Customize pre-build steps to get dependencies when referencing project assemblies from a different team project	||The build definition workspace template is managed in the VS GUI and has the full flexibility of a standard workspace, including mapping paths from multiple team projects||
||Use the TFSBuild command line tool to delete builds.	||Use the Visual Studio IDE to stop and delete builds.||

### Additional Resources
* For more information on Team Foundation Server 2008 see, “An Overview of Microsoft Visual Studio Code Name "Orcas" White Paper” at [http://go.microsoft.com/?linkid=6625887](http://go.microsoft.com/?linkid=6625887)