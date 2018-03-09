## Guidelines: Team Build
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Strategy
* _Use a scheduled build to produce regular builds._
* _Use a Continuous Integration (CI) build to get rapid feedback on check-ins._
* _Use a rolling build if CI builds are adversely impacting build server performance._
* _Use branching to reduce build breaks._
* _Use check-in policies to improve check-in quality._
* _Use build notification alerts to learn when the build has completed._ 

### Branching
* _Use new Team Build Types when creating a partial branch._ 
* _Modify the paths to solutions in the TFSBuild.proj files, when creating a complete branch._

### Check-in Policies
* _Use check-in policies to improve check-in quality._
* _Use check-in policies to associate work items with the build._

### Continuous Integration Builds
* _Use a CI build to get rapid feedback on check-ins._
* _Use a rolling build if CI builds are adversely impacting build server performance._
* _Ensure that the frequency of your rolling builds is less often than the build times._

### Customization
* _Use a custom post-build step to build an installer project._
* _Use MS Build Toolkit Extras to build Microsoft .NET 1.1 applications._
* _Use TFSBuild.proj to modify your build._
* _Use a custom pre-build step to build a project that has dependencies to another team project._

### Deployment
* _On larger teams, install the build services on a separate server._ 

### Performance
* _Use incremental builds to improve performance._
* _Avoid synchronizing redundant folders in your build._
* _Use workspaces to avoid checking out unwanted files and projects when doing a Team Build._
* _Consider using multiple build machines to improve performance._

### Projects
* _Avoid dependencies across team projects._
* _Use project references instead of file references._
* _Use Web Deployment Project for Web applications._
* _Use a single-solution strategy if you are working on a small team project._
* _Use a partitioned-solution strategy if you are working on a large team project with multiple independent sub-projects._
* _Use a multiple-solution strategy if you are working on a very large team project that requires many dozens of independent sub-projects._

### Scheduled Builds
* _Use a scheduled build to produce regular builds._

### Test-Driven Development
* _Run code analysis on each build._
* _Run automated tests on each build._
* _Consider setting builds to fail when automated tests fail._

### Work Items
* _Use work items to track build breaks._

## Strategy
* **Use a scheduled build to produce regular builds.**
* **Use CI build to get rapid feedback on check-ins.**
* **Use a rolling build if CI builds are adversely impacting build server performance.**
* **Use branching to reduce build breaks.**
* **Use check-in policies to improve check-in quality.**
* **Use build notification alerts to learn when the build has completed.** 

### Use a Scheduled Build to Produce Regular Builds
Use a scheduled build to produce builds at regular, predictable intervals.

Generally, builds provided to your test team and to others need to be reliable and should be made available at a fixed time frequency, so that feedback on the build can be collected in a timely fashion. 

The Team Build feature in Microsoft® Visual Studio® 2005 Team Foundation Server (TFS) does not support scheduled builds from the user interface. Instead, you can use the Microsoft Windows® Task Scheduler to run the TFSBuild command-line utility to start builds at a predetermined time.

**To create a scheduled build**
* Create a TFSBuild command line as follows:

{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

* Place the command line in a batch file.
* Create a Windows Scheduled Task that runs the batch file at your desired interval.

#### Additional Resources
* For more information about setting up scheduled builds with Team Build, see “Chapter 9: Setting Up a Scheduled Build with Team Build” in this guide.
* For more information about setting up scheduled build with TFS, see “How To – Set Up a Scheduled Build in Visual Studio Team Foundation Server” in this guide.

### Use a Continuous Integration Build to Get Rapid Feedback on Check-ins
You should use CI builds to provide your development team with rapid feedback on any breaking changes and on the quality of the build after each check-in. This helps the development team to fix the build issues quickly and can be used as a tool to improve the quality of your code.

Although Team Foundation Server 2005 does not provide a CI solution out of box, it does provide the framework for you to implement your own CI build solution.

For more information on setting up a CI build with TFS, see “How To – Set Up a Continuous Integration Build in Visual Studio Team Foundation Server.” This How To article uses the solution provided by the Microsoft Visual Studio Team System (VSTS) development team. The solution installs a Web service that runs under an account that has access to the TFS server. Team Foundation Server is able to send an e-mail message or call a Web service when specific events occur. This event mechanism is used by the CI solution to register a Web service with the **CheckinEvent** event,**** so that whenever a check-in occurs, the Web service initiates a Team Build. 

#### Additional Resources
* For more information, see “Chapter 8: Setting Up a Continuous Integration Build with Team Build” in this guide.
* For more information about setting up a CI build, see “How To – Set Up a Scheduled Build with Visual Studio Team Foundation Server” in this guide.
* For more information about how to use the VSTS CI solution, see “Continuous Integration Using Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx)
* To download the VSTS CI solution MSI, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)
* For more information about agile development and CI in TFS, see “Extend Team Foundation Server To Enable Continuous Integration” at [http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx](http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx)

### Use a Rolling Build if CI Builds Are Adversely Impacting Build Server Performance
Building immediately after every check-in is the simplest CI strategy and generally provides you with the most rapid feedback. However, if check-ins occurs rapidly enough to overwhelm your build server, you should use a rolling build approach where you build after a specified number of check-ins or after a specified time period. To decide if you need to use a rolling build, determine the following:
* Length of your Team Build in minutes
* Average frequency of check-ins in minutes
* Time window during which frequent check-ins occur

If the length of the build is longer than the average frequency of check-ins, your builds will run continuously because the first build will not complete before the next check-in occurs, which will start another build. If check-ins continue to occur before each build is complete, this impacts the performance of the build server and will block other builds (such as scheduled builds) from being started. Review the time window during which frequent check-ins occur and determine if CI builds will impact the delivery of scheduled builds or other important Team Builds.

#### Additional Resources
* For more information, see “Chapter 8 – Setting Up a Continuous Integration Build with Team Build” in this guide.

### Use Branching to Reduce Build Breaks
To help avoid build breaks, you should use a **Development** branch for active development and a **Main** branch for your integration build.

The following is an example of what your branch structure might look like after you have created a **Development** branch:
* **Development** – Development Branch
	* **Source**
* **Main** – Integration Branch
	* **Source**
	* **Other Assets folders**

Keep the following recommendations in mind when working with a release branch:
* **When to branch.** If you are creating daily builds and are having problems with build stabilization and integration, you should create both a main and a development branch to ensure greater predictability of your daily builds. You may also want to consider more stringent check-in policies to improve check-in quality. 
* **When not to branch.** If you are only creating CI builds, or your daily builds are already predictably stable, you might not need the extra overhead of an integration branch.
* **Permissions on branch:** 
	* The **Main** branch permissions should be read/write for developers responsible for merging and integration, but read-only for everyone else. 
	* The **Dev** branch permissions should be read/write for everyone.
* **Build frequency in branch:** 
	* Daily builds on the **Main** branch.
	* CI builds on the **Dev** branch.
* **Testing focus on branch:** 
	* Perform integration, performance, and security testing on the **Main** branch.  
	* Perform feature and quick feedback testing on the **Dev** branch.

Use the **Main** branch as a staging area for integrating changes that have been checked into the development branch. Perform all active development in the **Dev** branch, and integrate non-breaking changes into the **Main** branch.

#### Additional Resources
* For more information on defining a branching and merging strategy, see “Chapter 5 – Defining Your Branching and Merging Strategy” in this guide.
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)   
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx) 

### Use Check-in Policies to Improve Check-in Quality
You should use a combination of code analysis and testing policies to improve check-in quality. For example, use the supplied testing policy to ensure that specific tests are executed and passed prior to allowing source to be checked into TFS source control. You can also configure a code analysis policy to help ensure that your code meets certain quality standards by ensuring that security, performance, portability, maintainability, and reliability rules are passed.

By enforcing this type of check-in policy in addition to policies that enforce coding standards and guidelines, you can test your code against specific code quality issues.

To enforce a code analysis check-in policy for a team project, you right-click your team project in **Team Explorer**, point to **Team Project Settings**, and then click **Source Control**. Click the **Check-in Policy** tab, click **Add**, and then select and configure the appropriate policy.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To see sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at +[http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)+
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)

### Use Build Notification Alerts to Learn When the Build Has Completed 
To keep track of your build process, you can create alerts that send e-mail messages to you or to others when a build has completed. 

This is important because it provides quick turnaround among teams. For example, if the test team is notified by e-mail of a completed build, they can start their test pass without having to wait for manual instructions. 

#### Additional Resources
* For more information about build notifications, see “How to: Receive Build Notification E-Mail” at [http://msdn2.microsoft.com/en-us/library/ms181725(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181725(VS.80).aspx) 
* For further information about build notifications, see “How to: Add or Edit Alerts” at [http://msdn2.microsoft.com/en-us/library/ms181335(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181335(VS.80).aspx)

## Branching
* **Use new Team Build Types when creating a partial branch.** 
* **Modify the paths to solutions in the TFSBuild.proj files, when creating a complete branch.**

### Use New Team Build Types When Creating a Partial Branch
When you create a branch that contains a subset of the solutions in your team project, you might need to create new build types in order to build successfully. 

There are two types of partial branches:
# **A partial branch that does not include branching of any build types.** This would occur within a team project, and would simply branch solution and source files but would not branch any of the TeamBuildTypes folders into new folders.  
# **A partial branch that includes branching of build types.** This would occur within a team project, and would branch some of the TeamBuildTypes subfolders (that is, build types) in addition to other folders containing the relevant solution and source files.

If you create a partial branch that does not include Team Build Types all of the existing Team Builds will continue to work, but you will need to create a new Team Build Type if you want to build the branch. Create new build types by using the Team Build Wizard in order to build the code in the new branch. These new build types will point to the new branch location and may also point to the parent location for any solutions that must be included in the build but that were not branched.

If you create a partial branch that includes Team Build Types, the build types that are copied over with the branch will point to the original, parent branch locations and therefore will not allow you to build the new branch. Modify the branched build types so that they point to the new branched code locations.

#### Additional Resources
* For more information about how to update your build type, see “How to: Update Build Types on Branched Team Projects” at [http://msdn2.microsoft.com/en-us/library/ms252500(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252500(VS.80).aspx)

### Modify the Paths to Solutions in the TFSBuild.proj Files, When Creating a Complete Branch
When you create a new branch, including the Team Build Types, the paths in the build types still point to the previous location. In order for the build to work on the new branch, you must update the paths in the build type project files so that they reference the new path locations created after the branching operation.

When you create a full branch, you also branch the build types. The build types contain references to folders from the original source control tree. To have these build types refer to the branch folders, you must edit the folder references in these files. 

To perform the update, check out the build types from the branch you want to modify, apply the updates, and then commit the changes to the branch.

#### Additional Resources
* For more information about how to update your build types, see “How to: Update Build Types on Branched Team Projects” at [http://msdn2.microsoft.com/en-us/library/ms252500(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252500(VS.80).aspx)

## Check-in Policies
* **Use check-in policies to improve check-in quality.**
* **Use check-in policies to associate work items with the build.**

### Use Check-in Policies to Improve Check-in Quality
Use a combination of code analysis and testing policies to improve check-in quality. For example, use the supplied testing policy to ensure that specific tests are executed and passed prior to allowing source to be checked into TFS source control. You can also configure a code analysis policy to help ensure that your code meets certain quality standards by ensuring that security, performance, portability, maintainability, and reliability rules are passed.

By enforcing this type of check-in policy in addition to policies that enforce coding standards and guidelines, you can test your code against specific code quality issues.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To: Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To see sample code that will disallow selected patterns on check-in, see “Check-in Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Check-in Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at +[http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)+

### Use Check-in Policies to Associate Work Items with the Build
Set the Work Items check-in policy to force developers to associate their check-in with a work item. 

If a build breaks, it is important that you know what change sets are associated with this build and what work items those change sets are associated with. With this knowledge, you can identify the developer responsible for checking in the changed code and the area of the project on which he or she is working.

For a build to be associated with a set of completed work items, each check-in must be associated with a work item. These check-ins are represented as change sets associated with the build, and it is possible to trace from build to change set to work item.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To: Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 

## Continuous Integration Builds
* **Use a CI build to get rapid feedback on check-ins.**
* **Use a rolling build if CI builds are adversely impacting build server performance.**
* **Ensure that the frequency of your rolling builds is less often than the build times.**

### Use a CI Build to Get Rapid Feedback on Check-ins
You should use Continuous Integration builds to provide your development team with rapid feedback on any breaking changes and quality of the build after each check-in. This helps the development team to fix the build issues in a timely manner and can be used as a tool to improve the quality of your code.

Although Visual Studio 2005 Team Foundation Server does not provide a CI solution out of the box, it does provide the framework for you to implement your own CI build solution.

For more information on setting up a CI build with TFS, see “How To: Set Up a Continuous Integration Build in Visual Studio Team Foundation Server.” This How To article uses the solution provided by the VSTS development team. The solution installs a Web service that runs under an account that has access to the TFS server. Team Foundation Server is able to send an e-mail message or call a Web service when specific events occur. This event mechanism is used by the CI solution to register a Web service with the **CheckinEvent** event,**** so that whenever a check-in occurs, the Web service initiates a Team Build.

#### Additional Resources
* For more information about CI builds, see “Chapter 8 – Setting Up a Continuous Integration Build with Team Build” in this guide.
* For more information about setting up a CI build, see “How To – Set Up a Continuous Integration Build with Visual Studio Team Foundation Server” in this guide.
* For more information about how to use the VSTS CI solution, see “Continuous Integration Using Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx)
* To download the Visual Studio Team System CI solution MSI, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)
* For more information about agile development and CI in TFS, see “Extend Team Foundation Server to Enable Continuous Integration” at [http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx](http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx)

### Use a Rolling Build if CI Builds Are Adversely Impacting Build Server Performance
Building immediately after every check-in is the simplest CI strategy and will generally give you the most rapid feedback. However, if check-ins occurs rapidly enough to overwhelm your build server, you should use a rolling build approach where you build after a specified number of check-ins or after a specified time period. To decide if you need to use a rolling build, determine the following:
* Length of your Team Build in minutes
* Average frequency of check-ins in minutes
* Time window during which frequent check-ins occur

If the length of the build is longer than the average frequency of check-ins, your builds will run continuously because the first build will not complete before the next check-in occurs, which will start another build. If check-ins continue to occur before each build is complete, it will impact the performance of your build server and will delay other builds, such as scheduled builds. Review the time window during which frequent check-ins occur and determine if CI builds will impact the delivery of scheduled builds or other important Team Builds.

#### Additional Resources
* For more information about setting up CI builds, see “Chapter 8 – Setting Up an Continuous Integration Build with Team Build” in this guide.

### Ensure That the Frequency of Your Rolling Builds Is Less Often than the Build Times
It is important to determine the rolling build time interval to ensure an efficient build process. If the frequency of the rolling build is less than the time it takes to complete a build, it ensures that your build machine will be available for other build types between your rolling build intervals.

To determine the ideal rolling build interval, divide the average frequency of check-ins by the length of your build. For instance, if you have a build that takes 10 minutes and you average a check-in every 5 minutes, you could set a check-in interval of two check-ins and a timeout period of 10 minutes. This would help ensure that the build is complete before the next build kicks off. If you notice excessive load on your build server, you can increase these values.  

#### Additional Resources
* For more information about CI builds, see “Chapter 8 – Setting Up a Continuous Integration Build with Team Build” in this guide.

## Customization
* **Use a custom post-build step to build an installer project.**
* **Use MS Build Toolkit Extras to build Microsoft .NET 1.1 applications.**
* **Use TFSBuild.proj to modify your build.**
* **Use a custom pre-build step to build a project that has dependencies to another team project.**

### Use a Custom Post-Build Step to Build an Installer Project
Because Team Build does not support setup projects by default, you should use a custom post-build step to compile the setup project and copy the binaries to the build drop location.  

#### Additional Resources
* For more information, see “Walkthrough: Configuring Team Foundation Build to Build a Visual Studio Setup Project” at [http://msdn2.microsoft.com/en-us/library/ms404859(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404859(VS.80).aspx)

### Use MS Build Toolkit Extras to Build Microsoft .NET 1.1 Applications
Team Build does not support .NET 1.1 applications by default. The MSBuild Extras – Toolkit for .NET 1.1 (MSBee) allows .NET 1.1 builds but requires that your projects and solutions be upgraded to Visual Studio 2005. If you cannot upgrade to Visual Studio 2005 projects and solutions, you can use a custom post-build step to compile the .NET 1.1 applications. 

#### Additional Resources
* To download MSBee, go to [http://www.codeplex.com/MSBee](http://www.codeplex.com/MSBee) 
* For more information about creating a custom post-build step to compile a .NET 1.1 application, see Nagaraju’s blog entry at [http://blogs.msdn.com/nagarajp/archive/2005/10/26/485368.aspx](http://blogs.msdn.com/nagarajp/archive/2005/10/26/485368.aspx)

### Use TFSBuild.proj to Modify Your Build
To modify information about the build?such as the build server, drops location, or build directory?you edit the TFSBuild.proj file.

The TFSBuild.proj file contains much of the information needed to execute a Team Build. This information includes the build locations and whether the build should perform static code analysis and unit tests. To modify the build, you edit the TFSBuild.proj file. 

**To edit the TFSBuild.proj file**
# Check out the file from source control.
# Update the build information in the file. 
# Check the file back in, committing the changes. 

The next time the build is executed, it will use the amended build data.

#### Additional Resources
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 

### Use a Custom Pre-build Step to Build a Project That Has Dependencies to Another Team Project
Team Build does not support building solutions that cross team projects. To enable this, you must customize the TFSBuild.proj file to check out the code you need from the other projects on which your build depends.

#### Additional Resources
* For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx) 
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 

## Deployment
* **On larger teams, install the build services on a separate server.** 

### On Larger Teams, Install the Build Services on a Separate Server
Large Team Builds can take a long time and use up significant server resources. If you run your builds on your Team TFS server, this impacts the reliability, performance, and scalability of the server.

To improve the performance of your build and reduce load on your application tier, it is recommended that you run builds on a dedicated build server. 

#### Additional Resources
* To download the _Team Foundation Installation Guide_, or for more information about installing TFS and Team Build, go to [http://www.microsoft.com/downloads/details.aspx?FamilyId=E54BF6FF-026B-43A4-ADE4-A690388F310E&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=E54BF6FF-026B-43A4-ADE4-A690388F310E&displaylang=en) 

## Performance
* **Use incremental builds to improve performance.**
* **Avoid synchronizing redundant folders in your build.**
* **Use workspaces to avoid checking out unwanted files and projects when doing a Team Build**
* **Consider using multiple build machines to improve performance.**

### Use Incremental Builds to Improve Performance
By default, Team Build cleans out the directory it uses to perform the build before it checks out the complete source code tree needed for the build. Team Build also removes and re-initializes the workspace used to check out the sources for the build. To improve performance, you can set Team Build to only get sources that have changed since the last Team Build.

If the amount of source needed for a build is large and the build server is remote from the TFS server, the source code checkout could take a long time to execute. In such a case, you should consider using an incremental build. To perform the incremental build, you need to set several values in your TFSBuild.proj file should be true. You need to:
* Stop Team Build from cleaning the local build folder and sources folder.
* Stop Team Build from re-creating the workspace used for the build.
* Configure the Team Build to only get the changed sources from source control.

**To perform an incremental build**
# Create a new build type to represent the incremental build.
# Check out for edit the TFSBuild.proj file associated with the incremental build type you just created.
# Add the following <PropertyGroup> section just before the closing </project> element in TFSBuild.proj:
{{
<PropertyGroup>
    <SkipClean>true</SkipClean>
    <SkipInitializeWorkspace>true</SkipInitializeWorkspace>
    <ForceGet>false</ForceGet>
</ PropertyGroup>
}}
These settings accomplish the following:
* **SkipClean.** Setting **SkipClean** to **true** ensures that the build will not clean out the local build and sources folder.
* **SkipInitializeWorkspace.** Setting **SkipInitializeWorkspace** to **true** ensures that the build will leave the existing workspace in-place for the build machine.
* **ForceGet.** Setting **ForceGet** to **false** ensures that the build will only get updated source, rather than getting all source for the workspace.

#### Additional Resources
* For more information, see “Practices at a Glance – Team Build” in this guide.
* For more information about configuring an incremental build, see “How to: Configure Team Foundation Build for an Incremental Build” at [http://msdn2.microsoft.com/en-us/library/aa833876(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa833876(VS.80).aspx)

### Avoid Synchronizing Redundant Folders in Your Build
You should scale down your workspace mapping or cloak folders that are not needed as part of the build.

When you execute a Team Build, the server retrieves all of the files it needs from source control. The files that are retrieved are defined by the workspace that is used to create the Team Build Type. Some of the files that are mapped into the workspace may not be needed. You can change your workspace definition to reduce the folders included, or you can cloak unnecessary files so that they are not retrieved as part of the build.

For example, the default mapping for a new project is $/TeamProject. If all your source files are under $/TeamProject/foo/bar/foobar/sources, you should map only that directory.

To cloak files beneath your workspace mapping, you can edit the WorkspaceMapping.xml file that is created when the Team Build Type is created and is used to define the folders that are retrieved when performing the build. You can cloak files and folders that are not needed as part of the build. Folder cloaking is preferred because individual file cloaking can introduce maintenance overhead.

**To cloak folders**
# Check out WorkspaceMapping.xml from source control.
# Add the appropriate cloak entries to this file.
# Check in WorkspaceMapping.xml.

The following example ensures that the documentation folder will not be retrieved from source control during a Team Build:
{{
<Mappings>
  <InternalMapping ServerItem="$/MyTeamProject" LocalItem="c:\projects\teamproject” Type="Map" />
  <InternalMapping ServerItem="$/MyTeamProject/documentation" Type="Cloak" />
</Mappings>
}}

#### Additional Resources
* For more information about cloaking folders in a workspace, see “How to: Cloak and Decloak Folders in a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181378(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181378(VS.80).aspx)
* For more information about making Team Build ignore folders, see “How to make ‘Team Build’ skip getting certain folders?” at [http://blogs.msdn.com/manishagarwal/archive/2005/10/13/480584.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/10/13/480584.aspx)
* For more information about the WorkspaceMapping schema, see “Schema for the WorkspaceMapping.xml file” at [http://blogs.msdn.com/buckh/archive/2007/02/28/schema-for-the-workspacemapping-xml-file.aspx](http://blogs.msdn.com/buckh/archive/2007/02/28/schema-for-the-workspacemapping-xml-file.aspx)

### Use Workspaces to Avoid Checking Out Unwanted Files and Projects When Doing a Team Build
Team Build checks out your sources in order to execute the build. If you have a large source tree for a project, checking out the sources can be very time-consuming. If you are only building part of the team project, you should ensure that only the necessary sources are checked out.

If you have a large team project, it will contain multiple Visual Studio solutions, each of which is used to build a separate part of the team project. When you create a Team Build Type, you specify the solution that Team Build will use. If you specify a solution file without specifying a workspace, Team Build will check out all of the sources in the team project before performing a build. 

To check out only the sources you need, you must first define a workspace. Before creating the Team Build Type, you first define a workspace and only map the solution you want to build to that workspace. When you define the Team Build Type, select the workspace you have defined and then select the solution. In this way, only the sources defined in that workspace will be checked out.

#### Additional Resources
* For more information about creating a Team Build Type, see “Walkthrough: Creating a Build Type in Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms181286(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181286(VS.80).aspx)
* For more information about why Team Build checks out all the source code in a workspace, see “Why does Team Build sync all sources in spite of my selecting only a subset of solutions?” at [http://blogs.msdn.com/anutthara/archive/2005/12/07/500923.aspx](http://blogs.msdn.com/anutthara/archive/2005/12/07/500923.aspx)

### Consider Using Multiple Build Machines to Improve Performance
If you have multiple build types all executing on a single build server, the server could become overwhelmed. In such a situation, you should consider executing different build types on different build servers.

A build can take a long time to execute, especially if the build is for a large project. If you are using CI or frequent scheduled builds, the build server might not be able to keep up with the volume of builds being generated.

You can install multiple build servers to distribute the load among different servers. Assign different build types to each server to even out the build load.

#### Additional Resources
* For more information, see “Chapter 7 – Team Build Explained” in this guide.

## Projects
* **Avoid dependencies across team projects.**
* **Use project references instead of file references.**
* **Use Web Deployment Project for Web applications.**
* **Use a single-solution strategy if you are working on a small team project.**
* **Use a partitioned-solution strategy if you are working on a large team project with multiple independent sub-projects.**
* **Use a multiple-solution strategy if you are working on a very large team project that requires many dozens of independent sub-projects.**

### Avoid Dependencies Across Team Projects
In general, you should avoid dependencies that cross team projects and instead try to keep all related/dependent solutions/projects under same team project. This reduces the need for build script customization. If you have a dependency, use project references to define it, or branch the dependency from a shared project into your project. You should avoid file references because they are more difficult to manage. 

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at +[http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)+
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 

### Use Project References Instead of File References
If you need to reference another assembly in the same Visual Studio solution, you should use a Visual Studio project reference. By using project references, you enable Visual Studio to do a few things automatically for you, such as keeping build configuration synchronized (debug/release) and tracking versioning and rebuilding of components as necessary when assembly versions change.

#### Additional Resources
* For more information about project references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx) 

### Use Web Deployment Project for Web Applications
Web deployment projects are associated with a Visual Studio Web Site project or Web Application project. They allow you to manage build settings as well as a variety of other settings common to ASP.NET Web applications. For instance, the deployment project gives you easy access to Web.config, connection strings, and virtual directories, and allows you to more easily deploy the compiled Web application to the hosting server. 

#### Additional Resources
* For more information, see “Visual Studio 2005 Web Deployment Projects” at [http://msdn2.microsoft.com/en-us/asp.net/aa336619.aspx](http://msdn2.microsoft.com/en-us/asp.net/aa336619.aspx) 

### Use a Single-Solution Strategy if You Are Working on a Small Team Project
If you work on a small team, consider using a single Visual Studio solution to contain all of your projects. This structure simplifies development because all of the code is available when you open the solution. This strategy also makes it easy to set up references, because all references are between projects in your solution. You may still need to use file references to reference third-party assemblies, such as purchased components, that are outside your solution.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

### Use a Partitioned-Solution Strategy if You Are Working on a Large Team Project with Multiple Independent Sub-Projects
If you work on a large team, consider using multiple solutions, each representing a subsystem in your application. Developers can use these solutions to work on smaller parts of the system without having to load all code across all projects. You should design your solution structure so that any projects that have dependencies are grouped together. This enables you to use project references rather than file references. Consider creating a master solution file that contains all of the projects, if you want to use this to build the entire application.

**Note:** If you are building with Team Build (which relies upon MSBuild), it is possible to create solution structures that do not include all referenced projects. As long as the entire solution has been built first, generating the binary output from each solution, MSBuild will be able to follow project references outside the bounds of your solution and build successfully. Solutions created in this way will not build from the Visual Studio build command, but will only work with Team Build and MSBuild.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

### Use a Multiple-Solution Strategy if You Are Working on a Very Large Team Project That Requires Many Dozens of Independent Sub-Projects
If you work on a very large solution requiring many dozens of projects, you may run up against solution scalability limits. In this scenario, break your application into multiple solutions but do not create a master solution for the entire application because all references inside each solution are project references. References to projects outside of each solution (for example, to third-party libraries or projects in another sub-solution) are file references. This means that there can be no “master” solution. Instead, a script must be used that understands the order in which the solutions must be built. One of the maintenance tasks associated with a multiple-solution structure is ensuring that developers do not inadvertently create circular references between solutions. This structure requires complex build scripts and explicit mapping of dependency relationships. In this structure, it is not possible to build the application in its entirety within Visual Studio. Instead, you can use TFS Team Build or MSBuild directly.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

## Scheduled Builds
* **Use a scheduled build to produce regular builds.**

### Use a Scheduled Build to Produce Regular Builds
You should use a scheduled build to produce builds at regular, predictable intervals.

In general, builds provided to test teams and others need to be reliable and should be made available at a fixed time frequency, so that feedback on the build can be collected in a timely fashion. 

Although the Team Build feature in TFS does not support scheduled builds from the user interface, you can use the Microsoft Windows Task Scheduler to run the TFSBuild command utility to start builds at a predetermined time.

**To create a scheduled build**
* Create a TFSBuild command line as follows:

{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

* Place the command line in a batch file.
* Create a Windows Scheduled Task that runs the batch file at your desired interval.

#### Additional Resources
* For more information, see “Chapter 9 – Setting Up Scheduled Build with Team Build” in this guide.
* For more information about setting up scheduled build, see “How To – Set Up a Scheduled Build with Visual Studio Team Foundation Server” in this guide.

## Test-Driven Development
* **Run code analysis on each build.**
* **Run automated tests on each build.**
* **Consider setting builds to fail when automated tests fail.**

### Run Code Analysis on Each Build
Use code analysis as part of the build to improve build quality. You can configure a code analysis step in the build to help ensure that your code meets certain quality standards, ensuring that security, performance, portability, maintainability, and reliability rules are passed.

To turn on code analysis for a build type, you can either select the **code analysis** check box in the Team Build Type wizard when you create the new Team Build Type, or you can modify the TFSBuild.proj file after the build type has been created. 

**To enable code analysis in the TFSBuild.proj file**
* If you want all projects to run code analysis, regardless of project settings, change the **<RunCodeAnalysis>** tag to **Always**.
* If you want to run code analysis on each project based on project settings, change the **<RunCodeAnalysis>** tag to **Default.**

#### Additional Resources
* For more information about automatic code analysis as part of a build, see “How To – Automatically Run Code Analysis with Team Build in Visual Studio Team Foundation Server” in this guide.
* For more information about code analysis tools, see “Guidelines for Using Code Analysis Tools” at [http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx) 

### Run Automated Tests on Each Build
Run automated tests to automatically gain feedback on build quality after every build. In order to create a test list to associate with the build you must have either Visual Studio Test Edition or Visual Studio Team Suite installed. In order to run automated tests on the build server you must have either Visual Studio Developer Edition, Visual Studio Test Edition, or Visual Studio Team Suite installed on the build server. 

**To run automated tests as part of the Team Build process**
# Create one or more automated tests that you want to run with the build.
# Use the Test Manager to create a Test List.
# Use the Test Manager to group tests into the new Test List by dragging and dropping the tests from the Test View to the Test List in the Test Manager.
# Create a new Team Build Type.
# Select the check box to run automated tests.
# Select the test project within which your tests and test list were created.
# Select the test list you want to run.

#### Additional Resources
* For more information about automatically running build verification tests, see “How to: Configure and Run Build Verification Tests (BVTs)” at [http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx) 
* For more information about how to run automated build tests without Visual Studio Test Edition or a VSMDI file, see “How to run tests in a build without test metadata files and test lists (.vsmdi files)” at [http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx](http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx) 

### Consider Setting Builds to Fail When Automated Tests Fail
When a build fails because of compilation errors, a work item is created to track the failure and the build is marked as failed. When an automated test fails, however, the build does not fail. The test failure is converted into a warning and the build continues.

You may want to fail the build if an associated automated test fails. You may also want to generate a work item automatically to track the test failure.

**To fail the build upon test failure**
# Open the Microsoft.TeamFoundation.Build.targets file from Program Files\MSBuild\Microsoft\VisualStudio\v8.0\TeamBuild.
# Check out for edit and open the TFSBuild.proj file for the Team Build Type you want to have failed upon test failure.
# Copy the **RunTestWithConfiguration** target from Microsoft.TeamFoundation.Build.targets to the end of the TFSBuild.proj file, just before the closing **</Project>** tag.
# Modify the **ContinueOnError** attribute from **true** to **false**. - **Note:** There will be two test tool tasks. Modify the end-to-end task in order to only modify the behavior of builds on the build server. The desktop build task is used when building on a developer’s desktop.
# If you want to create a work item when the build fails, modify the **RunTestWithConfiguration** by adding an **OnError** element just before the closing **</Target>** tag The **OnError** element should look like the following:
{{ <OnError ExecuteTargets="CreateWorkItem;"/> }}

Alternatively, if you want all Team Build Types to fail upon test failure, you can modify Microsoft.TeamFoundation.Build.targets directly. This change will modify behavior for all Team Build Types.

The solution recommended above is straightforward to implement but is not guaranteed to continue working for future versions of Visual Studio. If you would like to implement a solution that is guaranteed to continue working after upgrade, see Aaron Hallberg’s blog entry, “Determining Whether Tests Passed in Team Build,” at [http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx](http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx) 

#### Additional Resources
* For more information about setting up a build to create a work item upon test failure, see “Create Workitems for Test Failures in TeamBuild” at [http://blogs.msdn.com/nagarajp/archive/2005/10/14/481290.aspx](http://blogs.msdn.com/nagarajp/archive/2005/10/14/481290.aspx)  
* For more information about a solution that is guaranteed to continue working after a Visual Studio upgrade, see “Determining Whether Tests Passed in Team Build” at [http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx](http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx) 

### Work Items
* **Use work items to track build breaks.**

### Use Work Items to Track Build Breaks
If Team Build fails, it automatically creates a work item to track that failure. By default, the work item will be assigned to ‘Active’ and the title will inform you that there has been a build failure. You should assign this work item to the responsible developer or build manager in order to fix the build and resolve the problem.

The build task in TFSBuild.proj that defines this work item looks like the following:
{{
<!-- Create WorkItem for build failure -->
    <CreateNewWorkItem
          BuildId="$(BuildNumber)"
          Description="$(WorkItemDescription)"
          TeamProject="$(TeamProject)"
          TeamFoundationServerUrl="$(TeamFoundationServerUrl)"
          Title="$(WorkItemTitle)"
          WorkItemFieldValues="$(WorkItemFieldValues)"
          WorkItemType="$(WorkItemType)"
          ContinueOnError="true" /> 
}}
If you would like to customize the work item that is created (for instance, to assign it to a specific developer or to set severity and priority), you can modify the WorkItemFieldValues field.

#### Additional Resources
* For more information about customizing the build failure work item, see “Team Foundation Build Tasks” at [http://msdn2.microsoft.com/en-us/library/ms243778(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms243778(vs.80).aspx) 

## Build Resources
* For more information about Team Builds in general, see “Overview of Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms181710(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181710(VS.80).aspx)