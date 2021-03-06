### How To: Set Up a Scheduled Build in Visual Studio Team Foundation Server 
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)

### Summary
Although Visual Studio 2005 Team Foundation Server does not provide scheduled builds out of the box, you can use the **TFSBuild** command to implement your own scheduled builds. This How To article walks you through the process of setting up a scheduled build by using the **TFSBuild** command and the Microsoft Windows® Task Scheduler.  

### Contents
* Objectives
* Overview
* Summary of Steps
* Before You Begin
* Step 1 – Create and Test Your Build
* Step 2 – Create the TFSBuild Command Line
* Step 3 – Test the TFSBuild Command Line
* Step 4 – Create a Batch File
* Step 5 – Test the Batch File
* Step 6 – Add a Scheduled Task
* Step 7 – Test the Scheduled Task
* Additional Resources

### Objectives
* Learn what a scheduled build is.
* Create a scheduled build by using the **TFSBuild** command utility and the Windows Task Scheduler.

### Overview
It is highly important that a project development team to generate regular builds in order to get timely feedback from a test team as well as other stake holders. This can be achieved through the use of scheduled builds. You can choose to schedule your build on a nightly, weekly, biweekly, or on any other regular schedule depending upon your project scope and requirements.
 
Although the Team Build feature in TFS does not have support scheduled builds out of box, it does provide a **TFSBuild** command line utility that enables you to initiate team builds from the command line. You can use any scheduler, such as the Windows Task Scheduler, to run the **TFSBuild** command utility in order to start builds at regular intervals.

### Summary of Steps
* Step 1 – Create and Test Your Build
* Step 2 – Create the TFSBuild Command Line
* Step 3 – Test the TFSBuild Command Line
* Step 4 – Create a Batch File
* Step 5 – Test the Batch File
* Step 6 – Add a Scheduled Task
* Step 7 – Test the Scheduled Task

### Before You Begin
Make sure the account that runs your build service is assigned Start a build = Allow permission in TFS.

### Step 1 – Create and Test Your build
In this step, you create a test build and make sure the team-build works from within Visual Studio Integrated Development Environment (IDE).  If the build does not work, you should fix it before moving on to the next step.

# Create a Microsoft Windows® Form project that you can use for testing the build.
# Build the project and make sure that it is working correctly. 
# Check your project into source control
# Create a team build as follows:
## In Team Explorer, right-click **Team Builds**, and then click **New Team Build Type.**
## Complete the self-explanatory **Team Build Type Creation Wizard.**
# Perform the following steps to verify that the team build is working:
## In Team Explorer, double-click the Team Build Project you just created
## On the **Build** menu of the Visual Studio instance, click **Build Team Project _<<Your Team Build Name>>._**
## Confirm that the correct build type is selected and the click **Build** 
# Review the build output and make sure that there are no errors in the build process

**Important:** Make sure that your build services account (TFSService) has Full Control permission to the shared folder for the drops, as specified in the **Team Build Type Wizard**.

### Step 2 – Create the TFSBuild Command Line
In this step, you create a command for the **TFSBuild** utility for the purpose of starting a build. 

# As the TFSBuild command utility needs a number of parameters in order to start a build, you first need to determine the parameters to be used, as follows.
## **Team Foundation Server** – The TFS URL where the solutions being built are checked in.
## **Team Project** – The name of the team project which you want to build.
## **Build Type** – The build type that you created using the Build Type Wizard in Step 1.
## **Build Machine** – The name of the build server that you want to use for building your project. This is an optional parameter; by default, it uses the build server specified in the team build type. 
## **Build Directory** – The path to the directory where the build occurs. This is an optional parameter; by default, it uses the path specified in the team build type.
# Create the build command as follows:

{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

If you plan to override the build machine name and build directory path specified while creating the build type, the command would then be as follows:

{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> /m:<<MachineName>> /d:<<BuildDirectory>> }}

### Step 3 – Test the TFSBuild Command Line
In this step, you test that the TFSBuild command is working correctly.

# Open the Visual Studio command prompt
# Type the **TfsBuild** command that you created in Step 2.
# Review the output to make sure that no errors occurred and that the build was created successfully.

### Step 4 – Create a Batch File
In this step, you create a batch file that will be used for scheduling the builds.

* Open Microsoft Notepad and type following command; please note that the full path to the TFSBuild.exe file is specified so that it can run from Windows command prompt. The following is an example of the command: 

{{ "C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\TFSBuild" start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

If you override the build machine and build directory path, the command in the batch file would be as follows:

{{ "C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\TFSBuild" start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> /m:<<BuildMachineName>> /d:<<BuildDirectoryPath>> }}

* Save the file as a batch file; for example, batchbuild.bat
* Place the file in a build scripts folder in TFS server source control, for example **Main\Scripts.**

### Step 5 – Test the batch file
 In this step, you verify that the batch file you created works correctly.

# Open a Windows command prompt. - **Note:** Do not open a Visual Studio command prompt; by default the Windows scheduler will run the batch file in a Windows command prompt.
# Start the batch file on the command line.
# Ensure that the build works correctly without any errors.

### Step 6 – Add a Scheduled Task
In this step, you add a schedule task for running the build command at regular intervals as required by your project.

# Click **Start** and then click **Control Panel.**
# Select the **Scheduled Tasks** option and then click **Add Scheduled Tasks.**
# In the **Scheduled Task Wizard** click **Next.**
# Click **Browse** and select the batch file you created in Step 4, then click **Next**.
# On this page, type the name of the task and select the frequency at which you want to run the tasks – for example, **Daily** and then click **Next**
# Configure the **Start time** and **Start date** and then click **Next.**
# Enter user name and password of an account with Start a build permissions and click **Next**
# Then click **Finish.**

### Step 7 – Test the Scheduled Task
In this step, you verify that the scheduled task is running at the right time and that the build work properly.
# Wait for the time at which the scheduled task should execute. -or- Click **Start** and then click **Control Panel,** then select **Scheduled Tasks** option, from the list right click on your scheduled task and select **Run**.  
# A command prompt should appear and your build should start.
# If you do not have access to the build machine at the time the task should execute, you can check back later and see if a build has completed:
# In **Team Explorer** double-click **All Build Types**.
# View the list of builds to see if a build is completed at the time you scheduled.

### Additional Resources
* For more information on configuring a scheduled build, see “How to: Configure a Scheduled Build (Command Line)” at [http://msdn2.microsoft.com/en-us/library/ms181727(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181727(VS.80).aspx)