### How To: Set Up a Continuous Integration Build in Visual Studio Team Foundation Server 
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)

### Summary
Although Visual Studio 2005 Team Foundation Server does not provide a Continuous Integration (CI) solution out of box, it does provide a framework on which you can build your own CI build solution. This How To article walks you through the process of setting up a CI build with TFS by using the solution provided by the VSTS team. This solution installs a Web service running under the account that has access to the TFS server. When you register the Web service for the **CheckinEvent** event, the Web service will initiate a team build whenever a check-in occurs. 

### Contents
* Objectives
* Overview
* Summary of Steps
* Before You Begin
* Step 1 – Create and Test Your Build
* Step 2 – Install the Continuous Integration Solution
* Step 3 – Configure the Continuous Integration Solution
* Step 4 – Register for the CheckinEvent Event
* Step 5 – Test the Continuous Integration Build
* Step 6 – Set Up E-mail Alerts
* Additional Resources

### Objectives
* Learn what a Continuous Integration build is
* Create a CI build by using **TFSBuild** and the VSTS team’s CI solution. 

### Overview
An important mechanism for improving code quality is to give developers continuous feedback regarding the quality of the check-ins they make. This is especially important for check-in that causes a build break resulting in compilation errors. The earlier the developer receives feedback, the sooner they can fix any errors in the code, thus unblocking other developers/testers and improving all team members’ productivity. 

This is where the Continuous Integration build type—the process of creating builds whenever a developer checks code into source control—becomes valuable. The Continuous Integration build provides quick feedback to developers, who can also configure their CI builds with quality gates to ensure further improvement in your build quality. 

### Summary of Steps
* Step 1 – Create and Test your Build
* Step 2 – Install the Continuous Integration Solution
* Step 3 – Configure the Continuous Integration Solution
* Step 4 – Register for the CheckinEvent Event
* Step 5 – Test the Continuous Integration Build
* Step 6 – Set Up E-mail Alerts

### Before You Begin
Make sure the account that runs your build service has, Start a build = Allow, permission in Team Foundation Server.

### Step 1 – Create and Test your Build
In this initial step, you create a test build and make sure it works from within the Visual Studio Integrated Development Environment (IDE).  If the team build does not work, you should fix it before moving on to the next step.

# Create a Microsoft Windows® Form project that you can use for testing the build.
# Build the project and make sure that it is working correctly. 
# Check your project into source control
# Create a team build as follows
## In Team Explorer, right-click **Team Builds**, and then click **New Team Build Type**
## Complete the self-explanatory **Team Build Type Creation Wizard**
# Verify that the team build is working by performing the following steps:
## In Team Explorer, double-click the Team Build Project you just created.
## On the **Build** menu of the Visual Studio instance, click **Build Team Project _<<Your Team Build Name>>._**
## Confirm that the correct build type is selected and then click **Build.** 
# Review the build output and make sure that no errors occurred in the build process.

**Important**: Make sure your build services account (TFSService) has Full Control permission to the shared folder for the drops, as specified in **Team Build Type Wizard**.

### Step 2 – Install the Continuous Integration Solution
In this step, you install the solution provided by VSTS team for setting up the CI build. Detailed information about the solution is available at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx) 

# Install the solution on your TFS server from following location  [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi) 
# On the second page of the installer wizard, ensure that the “**Team Foundation Server**” site is selected.

Setup creates a virtual directory beneath the root of the application-tier server for TFS. This should be an Internet Information Services (IIS) Web site named Team Foundation Server on port 8080.

### Step 3 – Configure the Continuous Integration Solution
In this step, you will configure the CI settings to specify the project to be built and the build machine and team build type to be used.

# Perform the followings steps to ensure that the virtual root runs in the "TfsAppPool" application pool:
## Open IIS Manager by clicking **Start**, click** Administrative Tools**, and then select **IIS Manager**
## Under the **Web Sites,** expand the **Team Foundation Server** Web site.
## Right-click on the **CI Web Application** and make sure that **Application Pool** is set to **TfsAppPool**.
# Configure Continuous Integration settings as follows
# Open the **CI Web Application** Web.config file located at C:\Program Files\Microsoft Visual Studio 2005 Team Foundation Server\Web Services\CI\
# Set the following properties by adding a new key under the **<appsettings>** node:
	* **TeamFoundationServer** – the URL for the application tier, in the format http://machine:8080.
	* **TeamProject** – the  team project for which you want to enable CI
	* **BuildType** – the build type to be used while creating CI builds. Typically, this is configured for builds only. You can also add a basic level of testing and static analysis.
	* **Build Machine** – an optional parameter, use this to override the default build machine specified in the build type.

The following is an example of the configuration settings:
{{ …. 
<add key="1" value="TeamServer=http://TFSRTM:8080;TeamProjectName=AdventureWorks;BuildType=Test Build"/>
…. }}

### Step 4 – Register for the CheckinEvent Event
In this step, you register for the **CheckinEvent** event by using the **bisubscribe** tool available with TFS.
# Open a command prompt and navigate to the following location C:\Program Files\Microsoft Visual Studio 2005 Team Foundation Server\TF Setup\
# Run the following command 
 
{{ Bissubscribe /eventType CheckinEvent /address http://TFSRTM:8080/ci/notify.asmx /deliveryType Soap /domain http://TFSRTM:8080 }}

# If you get any errors, or if you want to confirm that you have registered correctly, do the following:
## Open Microsoft SQL Server™ Management Studio.
## Open the **tfsIntegration** database.
# Open the **tbl_subscription** table.
The table has entries for all events that have already been subscribed; you should be able to find the entry for CI solution subscribed to the CheckinEvent event. If required, you can unsubscribe any registered event, by simply deleting the entry from the table. 

### Step 5 – Test the Continuous Integration Build
In this step, you verify that the CI build is working correctly.

# Open the Windows Forms Application that was created in Step 1.
# Make some nominal changes to the code. Be careful to ensure that the changes will not break the build.
# Check-in the code changes you made.
# If you have access to the build machine, open Task Manager and look at the machine’s CPU usage; it should increase soon after the check-in to indicate that a build is occurring. If you look at the process list, you should see msbuild, csc, and/or aspnet_compiler using up CPU cycles, indicating that the build is in progress.
# Give the build time to run and then in the **Team Explorer,** double-click on **All Build Types** and look for the build after it completes.

#### Trouble shooting
In case the build does not show up in the build list, you can troubleshoot the problem as follows:
# Make sure that the event is subscribed correctly. For more information, see sub-step 3 of Step 4 above.
# Make sure that the CI Web Application’s Web.config is configured correctly, for more information, see Step 3 above.
# Make sure that the CI Web application is running in the right context and that it has access to the TFS server.
# If you have followed the preceding troubleshooting steps but the build still fails you can debug the CI Web application as follows:
# Create a new Web site project.
# Select to add an existing Web site to this new project.
# Click the local IIS button and then select the CI Web Application from the list.
# Open **notify.cs** and set a breakpoint on the **Notify** method.
# Press F5 to start debugging.
# Make changes to the Windows Forms test application and then check the code into source control.
	* If the breakpoint is not hit, the event is not being captured; try subscribing again
	* If the breakpoint is hit, debug further.
	* Ensure that script debugging is enabled in Microsoft Internet Explorer. On tools menu select **Internet Options** and then click the **Advanced** tab, here make sure the **Disable Script Debugging (Internet Explorer)** option is unchecked.

### Step 6 – Set Up E-mail Alerts
In this step you will set up an e-mail alert to be sent upon build completion, so that all concerned parties are informed. 

# In the Team Explorer, right-click the relevant team project. 
# Select **Project Alerts.**
# Select the **A build completes** option and enter the e-mail address(es) for notification. 

### Additional Resources
* For more information on how to use the Visual Studio Team System CI solution, see “Continuous Integration Using Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx)
* To download the Visual Studio Team System CI solution installer, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)
* For more information on Agile Development and Continuous Integration in Team Foundation Server, see “Extend Team Foundation Server To Enable Continuous Integration” at [http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx](http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx)