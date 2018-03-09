## Practices at a Glance: Team Build
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Administration
* _How to secure your build server_
* _How to delete a build_
* _How to delete a build type_
* _How to associate a work item with a build_

### Check-in Policies
* _How to use check-in policies to improve check-in quality_
* _How to use check-in policies to associate work items with the build_

### Continuous Integration Builds
* _How to automatically run Continuous Integration (CI) builds_
* _How to determine if you need a rolling build_
* _How to determine your rolling build time interval_

### Customization
* _How to modify the build number_ 
* _How to set up workspace mapping to get and build a subset of the tree_
* _How to build a project with dependencies on another team project_
* _How to change the build configuration (release/debug)_

### Deployment
* _How to set up a build server_ 
* _How to determine if you need multiple build servers_

### General
* _How to build and deploy an ASP.NET application with Team Build_
* _How to build a Microsoft® .NET 1.1 application with Team Build_
* _How to build setup and deployment projects with Team Build_
* _How to create a team build_
* _How to create multiple build types_
* _How to create a team build for a project that references assemblies from another project_
* _How to subscribe to build e-mail events_
* _How to receive notification when a build has failed_
* _How to start a build_
* _How to verify that the build succeeded_
* _How to view the build output_
* _How to change the build server location_
* _How to change the build output location_
* _How to determine what changesets are part of the build_
* _How to change the reported build quality_ 

### Projects
* _How to use a single-solution strategy_ 
* _How to use a partitioned-solution strategy_
* _How to use a multiple-solution strategy_ 

### Reporting
* _How to view build quality_
* _How to view all the check-ins for a build_
* _How to view work items or bugs closed for a build_
* _How to view open work items or bugs for a build_
* _How to track velocity from build to build_
* _How to track test case pass/fail results for a build_
* _How to review build status (BVT results)_

### Scheduled Builds
* _How to automatically run nightly builds_
* _How to decide on a build frequency and type for your project_

### Test-Driven Development
* _How to create a “hello world” acceptance test_
* _How to run automated tests as part of the build_
* _How to run code analysis as part of the build_
* _How to get failed tests to fail a build_

## Administration
* **How to secure your build server**
* **How to delete a build**
* **How to delete a build type**
* **How to associate a work item with a build**

### How to Secure Your Build Server
**To secure your build server**
# Deploy build services on a separate server, rather than sharing a server with the Microsoft Visual Studio® 2005 Team Foundation Server (TFS) application-tier or data-tier.
# Grant the build process read/write access to the builds directory. Ensure that the account running the build is able to access this directory.
# Grant the build process read/write access to the build drop network share. Ensure that the account running the build is able to access this share.
# Ensure that the account used to run the team build is a member of the Team Project’s **Build Services** group.

To improve Team Foundation Server security, you should install the build server on its own computer rather than on the application tier or data tier. Certain deployment or build steps may require elevated privileges; for example, creating a virtual directory to deploy a Web application requires administrative rights on the build server. This means that the Microsoft Windows® account running the build requires these rights. If the build computer is on the application tier, then this could present a security risk. Similarly, if the build computer is on the data tier, the build account could access and change the databases on that tier. 

**Note:** For security reasons, do not add the account running the team build to the SERVER\ Service Accounts group. Members of this group have full administration rights in TFS. 

#### Additional Resources
* For more information about TFS groups and permissions, see “Team Foundation Server Default Groups, Permissions, and Roles” at [http://msdn2.microsoft.com/en-us/library/ms253077(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms253077(VS.80).aspx)

### How to Delete a Build
To delete a build, you use the TFSBuild command-line tool. Specify the address of the TFS server, the name of the team project, and the build name; for example:
{{ TfsBuild delete [http://mytfsserver:8080/](http://mytfsserver:8080/) myproject build20070606.4 }}

#### Additional Resources
* For more information about deleting a completed build, see “How to: Delete a Completed Build” at [http://msdn2.microsoft.com/en-us/library/aa337656(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa337656(VS.80).aspx)
* For more information about the delete command, see “Delete Command (Team Foundation Build)” at [http://msdn2.microsoft.com/en-us/library/ms244360(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244360(VS.80).aspx)

### How to Delete a Build Type
You cannot delete Team Build types by using Team Explorer. Instead, you should remove the build type from source control.

**To delete an existing build type**
# Open Source Control Explorer.
# In Source Control Explorer, expand your team project folder.
# Expand the TeamBuildTypes folder.
# Right-click the Team Build folder that represents the Team Build type you want to delete and then click **Delete**.
# Right-click the Team Build folder again and then click **Check In Pending Changes…**
# Open Team Explorer.
# Right-click the Team Builds** folder and then click **Refresh**.
# Expand the Team Builds** folder and confirm that the Team Build has been deleted.

#### Additional Resources
* For more information about Team Build, see “Overview of Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms181710(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181710(vs.80).aspx)

### How to Associate a Work Item with a Build
Use the **Check In** dialog box to associate work items with a check-in. This automatically associates these work items with the next build.

**To associate a work item with a build**
# Make code changes that you want to have included in the build and that will be associated with a work item.
# Check in the pending changes.
# In the **Check In** dialog box, click **Work Items**.
# Select the work item(s) you want to associate with this check-in.

All changesets that have occurred since the last successful build will be associated with the next build. After the next build, Team Build will list this changeset in the associated changesets for the build and will include the selected work item as being associated with the changeset.

#### Additional Resources
* For more information about checking in pending changes, see “How to: Check In Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx) 

## Check-in Policies
* **How to use check-in policies to improve check-in quality**
* **How to use check-in policies to associate work items with the build**

### How to Use Check-in Policies to Improve Check-in Quality
Use a combination of code analysis and testing policies to improve check-in quality. For example, use the default testing check-in policy to ensure that specific tests are executed and passed prior to allowing source to be checked into TFS source control. You can also configure a code analysis policy to help ensure that your code meets certain quality standards by ensuring that security, performance, portability, maintainability, and reliability rules are passed.

**To enforce a code analysis check-in policy for a team project**
# In Team Explorer, right-click your team project, select **Team Project Settings**, and then click **Source Control**
# Click the **Check-in Policy** tab.
# Click **Add** and then select and configure the code analysis and testing policies.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To see sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn't Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)

### How to Use Check-in Policies to Associate Work Items with the Build
Use a check-in policy to enforce that each check-in has associated work items. Developers use the **Check In** dialog box to associate work items with a check-in. This automatically associates these work items with the next build. 

**To set the work item check-in policy to force developers to associate their check-in with a work item**
# In Team Explorer, right-click your team project, select **Team Project Settings**, and then click **Source Control**.
# Click the **Check-in Policy** tab.
# Click **Add** and then select and configure the **Work Item** check-in policy.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 

## Continuous Integration Builds
* **How to automatically run Continuous Integration (CI) builds**
* **How to determine if you need a rolling build**
* **How to determine your rolling build time interval**

### How to Automatically Run Continuous Integration Builds
Although Visual Studio 2005 Team Foundation Server does not provide a Continuous Integration (CI) solution out of the box, it does provide the framework for you to implement your own CI solution.

**To set up a CI build solution**
* **Create and test your build.** Make sure that you have a Team Build type in place and that you can run it without errors.
* **Install the Continuous Integration add-on.** Install the CI add-on from [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx).
* **Configure the Continuous Integration add-on.** Ensure that the CI Web application virtual root runs in the **TFSAppPool** application pool. Update the CI Web application Web.config file so that it works with your team server and team build by adding the following key:
{{
<add key="1" value="TeamServer=http://TFSRTM:8080;TeamProjectName=AdventureWorks;BuildType=Test Build"/>
}}
* **Register for the CheckinEvent event.** Use the **BisSubscribe.exe** tool to register for the check-in event, by using the following command line:
{{
Bissubscribe /eventType CheckinEvent /address http://TFSRTM:8080/ci/notify.asmx /deliveryType Soap /domain [http://tfsrtm:8080/](http://tfsrtm:8080/) 
}}
* **Test the CI build.** Test the build by completing a check-in. Wait a few minutes for the build to complete, and then view the builds page to see if the build completed successfully.
* **Set up e-mail alerts.** Set up alerts so that concerned parties can be notified when the build completes. Open the **Project Alerts** dialog box from the team project context menu, and then select the **A build completes** alert check box.

For more information and expanded steps, see “How To – Set Up a Continuous Integration Build with Visual Studio Team Foundation Server” in this guide.

#### Additional Resources
* For more information, see “Chapter 8 – Setting up a Continuous Integration Build with Team Build” in this guide.
* For more information about setting up a CI build, see “How To – Set Up a Scheduled Build with Visual Studio Team Foundation Server” in this guide.
* For more information about how to use the Visual Studio Team System CI solution, see “Continuous Integration Using Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx)
* To download the Visual Studio Team System CI solution MSI, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)
* For more information about agile development and CI in TFS, see “Extend Team Foundation Server To Enable Continuous Integration” at [http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx](http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx)

### How to Determine if You Need a Rolling Build
Building immediately after every check-in is the simplest CI strategy and generally gives you the most rapid feedback. However, if check-ins occur rapidly enough to overwhelm the build server, you should use a rolling build approach where you build after a specified number of check-ins or after a specified time period. To find out if you need to use a rolling build, determine the following:
* Length of your team build in minutes
* Average frequency of check-ins in minutes
* Time window during which frequent check-ins occur

If the length of the build is longer than the average frequency of check-ins, your builds run continuously because the first build will not complete before the next check-in occurs, which starts another build. If check-ins continue to occur before each build is complete, this impacts the performance of the build server and will block other builds from being started, such as scheduled builds. Review the time window during which frequent check-ins occur and determine if CI builds are likely to impact the delivery of scheduled builds or other important team builds.

#### Additional Resources
* For more information, see “Chapter 8 – Setting Up a Continuous Integration Build with Team Build” in this guide.

### How to Determine Your Rolling Build Time Interval
It is important to determine the rolling build time interval to ensure an efficient build process. You will want a timely build while at the same time not overloading the build process.

To determine the ideal rolling build interval, divide the average frequency of check-ins by the length of your build. For example, if you have a build that takes 10 minutes and you average a check-in every 5 minutes, you could set a check-in interval of two check-ins and a timeout period of 10 minutes. This helps to ensure that the build is complete before the next build is started. If you notice excessive load on your build server, you can increase these values.  

#### Additional Resources
* For more information, see “Chapter 8 – Setting Up a Continuous Integration Build with Team Build” in this guide.

## Customization
* **How to modify the build number** 
* **How to set up workspace mapping to get and build a subset of the tree**
* **How to build a project with dependencies on another team project**
* **How to change the build configuration (release/debug)**

### How to Modify the Build Number 
In order to customize the build number in your compiled assemblies, you need to generate the replacement build number and then write it to the assemblyinfo source file.

In order to customize the build number property displayed in the Team Build interface, you need to override the $(**BuildNumber**) property in the **BuildNumberOverride** target.

**To customize the build number in both the assembly and in the Team Build interface**
# Override the **$(BuildNumber)** in the **BuildNumberOverride** target.
# Override the **BeforeCompile** target to write the AssemblyInfo.cs or .vb file.

**Example**
{{
  <Target Name="BuildNumberOverrideTarget">
    <Message Importance="High" Text="$(BuildNumber)" />
 
    <ConvertTFSBuildNumberToSolutionBuildNumber
      MajorAndMinorVersion="1.0"
      TFSBuildNumber="$(BuildNumber)"
      TFSLastBuildNumber="$(LastBuildNumber)">
      <Output TaskParameter="SolutionBuildNumber" PropertyName="SolutionBuildNumber" />
      <Output TaskParameter="TFSBuildNumber" PropertyName="BuildNumber" />
    </ConvertTFSBuildNumberToSolutionBuildNumber>
    <Message Importance="High" Text="$(SolutionBuildNumber)" />
    <Message Importance="High" Text="$(BuildNumber)" />
  </Target>
 
  <Target Name="BeforeCompile">
    <Message Importance="High" Text="$(SolutionBuildNumber)" />
    <CreateItem Include="$(SolutionRoot)\**\AssemblyInfo.cs">
      <Output TaskParameter="Include" ItemName="AssemblyInfoFiles"/>
    </CreateItem>
    <CreateItem Include="$(SolutionRoot)\**\AssemblyInfo.vb">
      <Output TaskParameter="Include" ItemName="AssemblyInfoFiles"/>
    </CreateItem>
    <RewriteFileVersions 
      AssemblyInfoFiles="@(AssemblyInfoFiles)"
      AssemblyVersionNumber="$(SolutionBuildNumber)" 
      AssemblyFileVersionNumber="$(SolutionBuildNumber)" 
      AssemblyInformationalVersionNumber="$(SolutionBuildNumber)" />
  </Target>
}}
#### Additional Resources
* For another method to modify assembly versioning, see Aaron Halberg’s blog post “Team Build and the AssemblyInfo Task” at [http://blogs.msdn.com/aaronhallberg/archive/2007/06/08/team-build-and-the-assemblyinfo-task.aspx](http://blogs.msdn.com/aaronhallberg/archive/2007/06/08/team-build-and-the-assemblyinfo-task.aspx) 
* The AssemblyInfo task, referenced in the blog post above, has a new home on GotDotNet. You can find it here [http://www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=5C455590-332C-433B-A648-E368B9515580](http://www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=5C455590-332C-433B-A648-E368B9515580) 
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 

### How to Set Up Workspace Mapping to Get and Build a Subset of the Tree
The workspace mapping file defines the source control folders that are retrieved by the build server. It is not always necessary to check out all of the files in order to perform the build. You can change your workspace definition to reduce the number of folders included, or you can cloak unnecessary files so that they are not retrieved as part of the build.

For example, the default mapping for a new project is $/TeamProject. If all your source files are under $/TeamProject/foo/bar/foobar/sources, you should map only that directory

**To cloak files and folders**
# Check out WorkspaceMapping.xml from source control.
# Add the appropriate cloak entries to this file.
# Check in WorkspaceMapping.xml.

The WorkspaceMapping.xml file looks like the following:
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

### How to Build a Project with Dependencies on Another Team Project
Team Build does not support building solutions that cross team projects. To enable this, you must customize the TFSBuild.proj file to check out the code you need from the other projects on which your build depends.

To build a project with dependencies on another team project, you need to get the source or assemblies from that project into the workspace on your build server. To do this, you need to edit your TFSBuild.proj file to add the assembly or the solution reference and override the **BeforeGet** event to get assemblies or sources from each of the team projects on which you have a dependency.
   
**To build a project that has dependencies on another team project**
* Check out the TFSBuild.proj** script from Source Control Explorer. 
* Add the following configuration setting under the **PropertyGroup** section: 
{{
<!-- to be added under PropertyGroup -->
<TfCommand>$(TeamBuildRefPath)\..\tf.exe</TfCommand>
<SkipInitializeWorkspace>true</SkipInitializeWorkspace>
}}
SkipInitializeWorkSpace allows you to skip invoking the default tasks to delete and re-create the workspace on the build machine. The new property is used in the custom target **BeforeGet** (see below).
* Add the following configuration setting to the **ItemGroup** entries that map both the Team Projects and the solutions. Make sure that you provide the correct local paths for the build machine. Multiple mappings cannot share the same local folder and will result in a **MappingConflictException** exception in the CreateWorkspace task.
{{
<ItemGroup>
  <!-- add one entry for every solution you reference -->
  <SolutionToBuild Include="$(SolutionRoot)\DependentApp\DependentApp.sln" />
  <SolutionToBuild Include="$(SolutionRoot)\YourApp\YourApp.sln" />
</ItemGroup>

<ItemGroup>
  <!-- add one entry for every Team Project you reference -->
  <Map Include="$/YourApp/YourApp">
    <LocalPath>$(SolutionRoot)\YourApp</LocalPath>
  </Map>
  <Map Include="$/DependentApp/DependentApp">
    <LocalPath>$(SolutionRoot)\DependentApp</LocalPath>
  </Map>
</ItemGroup>
}}
* Override the **BeforeGet** event to retrieve the workspaces for each Team Project: 
{{
<Target Name="BeforeGet">
  <DeleteWorkspaceTask 
      TeamFoundationServerUrl="$(TeamFoundationServerUrl)" 
      Name="$(WorkspaceName)" />
  <Exec 
    WorkingDirectory="$(SolutionRoot)" 
    Command="&quot;$(TfCommand)&quot; workspace /new $(WorkSpaceName) /server:$(TeamFoundationServerUrl)"/>
  <Exec 
   WorkingDirectory="$(SolutionRoot)"
   Command="&quot;$(TfCommand)&quot; workfold /unmap /workspace:$(WorkSpaceName) &quot;$(SolutionRoot)&quot;"/>
  <Exec 
    WorkingDirectory="$(SolutionRoot)" 
    Command="&quot;$(TfCommand)&quot; workfold /map /workspace:$(WorkSpaceName) 
          /server:$(TeamFoundationServerUrl) &quot;%(Map.Identity)&quot; &quot;%(Map.LocalPath)&quot;"/>
</Target> 
}}
* Check in the build script and run the build.

#### Additional Resources
* For more information, see Manish Agarwal’s blog entry, “Working with multiple team projects in Team Build,” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)  

### How to Change the Build Configuration (Release/Debug)
In order to change build configuration in an existing build, you need to modify the <**ConfigurationToBuild>** tag in TFSBuild.proj.

**To change the build configuration**
# Open Source Control Explorer.
# In Source Control Explorer, expand your team project folder.
# Expand the TeamBuildTypes folder.
# Select the team build folder for which you want to turn on code analysis.
# Check out the TFSBuild.proj file from source control. You might need to perform a **Get Latest Version** operation on the folder first.
# In Source Control Explorer, double-click TFSBuild.Proj to open it. 
# Modify the **<ConfigurationToBuild>** tag to the new build configuration.
# Save TFSBuild.proj and check it back into source control.

#### Additional Resources
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 

## Deployment
* **How to set up a build server** 
* **How to determine if you need multiple build servers**

### How to Set Up a Build Server 
You install the build server separately from your installation of TFS. Because the build server needs to be able to compile your code, run tests, and perform code analysis, all tools that are needed by the build process must be installed.

**To set up a build server**
# Install Visual Studio.
* If you want to ensure you have all the tools necessary for any build scenario, install the entire Team Suite.
* If you want to run Team Build but do not need to run test cases, install Visual Studio Team Developer Edition.
* If you want to run automated tests cases as part of your build process, install Visual Studio Team Test Edition.
# On the Team Foundation Server DVD, open the \build folder.
# Run the Setup wizard.

The account used to run the build server: 
* Must have **Log On Locally** permission on the TFS computers.
* Should not be a local administrator account on TFS computers.
* Should be marked **Account is sensitive and cannot be delegated** for Microsoft Active Directory® on the domain.

#### Additional Resources
* You can download the _Team Foundation Server Installation Guide_ from [http://www.microsoft.com/downloads/details.aspx?familyid=e54bf6ff-026b-43a4-ade4-a690388f310e&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=e54bf6ff-026b-43a4-ade4-a690388f310e&displaylang=en) 

### How to Determine if You Need Multiple Build Servers
If you have multiple build types all executing on a single build server, you can overload the build server. If this becomes an issue, consider executing different build types on different build servers.

A build can take a long time to execute, especially if the build is for a large project. If you are using Continuous Integration or frequent scheduled builds, it is possible that the build server will not be able to keep up with the volume of builds being generated. You can install multiple build servers to distribute the load. Assign different build types to each server to even out the build load.

## General
* **How to build and deploy an ASP.NET application with Team Build**
* **How to build a .NET 1.1 application with Team Build**
* **How to build setup and deployment projects with Team Build**
* **How to create a team build**
* **How to create multiple build types**
* **How to create a team build for a project that references assemblies from another project**
* **How to subscribe to build e-mail events**
* **How to receive notification when a build has failed**
* **How to start a build**
* **How to verify that the build succeeded**
* **How to view the build output**
* **How to change the build server location**
* **How to change the build output location**
* **How to determine what changesets are part of the build**
* **How to change the reported build quality** 

### How to Build and Deploy an ASP.NET Application with Team Build
If you want to build a solution that contains only ASP.NET Web applications, you must ensure that you choose the appropriate configuration. When creating the build type, when you select the configuration and the platform, make sure that the platform is set to **.NET** and that the **Configuration** is set to **Debug**:

**To build a solution that contains only ASP.NET Web applications projects**
# Run the **New Team Build Type** **Creation** **Wizard**.
# Give the build a name.
# Select the solution that contains only the ASP.NET Web application.
# Select the appropriate configuration.
# Click the **Platform** drop-down list and select **.NET** as the platform.
# Specify the location information for the build type.
# Choose the tests and code analysis rules to run.
# Save the build type by selecting **Finish**.

If you are building a solution that contains both ASP.NET Web applications and other .NET projects, you must set the platform type to **Mixed Platforms**.

**To build a solution that contains ASP.NET Web applications and other .NET projects**
# Run the **New Team Build Type** **Creation Wizard**.
# Give the build a name.
# Select the solution that contains only ASP.NET Web applications and other projects.
# Select the appropriate configuration.
# Click the **Platform** drop-down list and select **Mixed** as the platform.
# Specify the location information for the build type.
# Choose the tests and code analysis rules to run.
# Save the build type by selecting **Finish**.

You will find the compiled binaries in the drop location under {BuildType}\{Configuration Name}\{Platform}\_PublishedWebsites

Deploying a Web application to Internet Information Services (IIS) is not supported natively by Team Build. If you want to deploy the application to IIS as part of the team build, you have two choices: you can: add a custom step to the build type, or you can use a Web Deployment Project.

If you are at the start of a Team Project, examine the Web Deployment Project option to see if you can use this option in your development. If you already have existing Web sites, using Web Deployment Projects may disrupt application development. Consider using an MSBuild post-build step instead. In both cases, you must ensure that the service account used to run the build is a member of the local administrators group to allow it to create a virtual directory in IIS.

**To use a post build step to deploy your Web application**
* Download the SDC Tasks Library from Codeplex at [http://www.codeplex.com/sdctasks](http://www.codeplex.com/sdctasks)
* Check out the Team Build type that you are going to use to deploy the Web application.
* Extract the file Microsoft.Sdc.Tasks.dll from the downloaded zip file into the folder where you checked out the build type.
* Add the DLL to source control and check it in.
* Amend the TFSBuild.proj file so that the build copies the files to the correct directory, and then create that directory as a virtual directory as follows:
	* Add a **<PropertyGroup>** element specifying the location of the compiled Web application:

{{ <PropertyGroup>
     <WebBinariesLocation>$(SolutionRoot)\..\Binaries\.NET\Release\_PublishedWebSites\MyWebSite</WebBinariesLocation>
  </PropertyGroup> }}

	* Add two **UsingTask** elements that add a references to the CreateVirtualDirectory and DeleteVirtualDirectory tasks:
{{
<UsingTask TaskName="Microsoft.Sdc.Tasks.Web.WebSite.CreateVirtualDirectory" AssemblyFile="Microsoft.Sdc.Tasks.dll" />
<UsingTask TaskName="Microsoft.Sdc.Tasks.Web.WebSite.CreateVirtualDirectory" AssemblyFile="Microsoft.Sdc.Tasks.dll" />
}}
	* Add an **AfterCompile** target to create the virtual directory and copy the files into that directory:
{{
<Target Name="AfterCompile">
  <MakeDir Directories="C:\Deploy\MyWebsite" />
  <CreateVirtualDirectory VirtualDirectoryName="MyWebSite" Path="C:\Deploy\Website" />
  <DeleteVirtualDirectory VirtualDirectoryName="MyWebSite" />
  <Exec Command="xcopy /y /e $(WebBinariesLocation) C:\Deploy\MyWebsite"/>
</Target>
}}
* Save the file and commit it to the source control repository.

If you run the team build, it will now build the Web application, create a virtual directory, and copy the Web application to that directory.

**To use a Web deployment project**
# Download and install the Visual Studio 2005 Web Deployment Projects onto your client computer.
# Download and install the Visual Studio 2005 Web Deployment Projects onto your build server.
# Open the solution containing the Web application. 
# Click the **Build** menu and then select **Add Web Deployment Project…**
# Specify the name and location of the deployment project.
# In Solution Explorer, right-click the Web Deployment Project and then select **Property Pages**.
# In the dialog box, choose the **Configuration** that Team Build should build (Debug or Release).
# In the **Deployment** section, select the **Create an IIS virtual directory for the output folder** check box and then specify the virtual directory name.
# Click **OK**.
# Check the solution changes into source control.

If you run the team build containing this solution, it will build the Web application and create a virtual directory in the directory where the Web application is built. This will be Build Directory}\{Team Project Name}\{Build Type}\Binaries\{Configuration Name}\{Platform}\_PublishedWebSite\{Web Deployment Project Name.

#### Additional Resources
* To download the SDC Tasks, go to [http://www.codeplex.com/sdctasks](http://www.codeplex.com/sdctasks)
* For more information about building ASP.NET applications with Team Build, see “TN_1600: Building ASP.NET projects with Team Build” at [http://msdn2.microsoft.com/en-us/teamsystem/aa718894.aspx](http://msdn2.microsoft.com/en-us/teamsystem/aa718894.aspx)
* For more information about using Web Deployment Projects, see “TN_1601: Team Build and Web Deployment Projects” at [http://msdn2.microsoft.com/en-us/teamsystem/aa718895.aspx](http://msdn2.microsoft.com/en-us/teamsystem/aa718895.aspx)
* For more information about building Web Deployment Projects, see “Visual Studio 2005 Web Deployment Projects” at [http://msdn2.microsoft.com/en-us/asp.net/aa336619.aspx](http://msdn2.microsoft.com/en-us/asp.net/aa336619.aspx)

### How to Build a .NET 1.1 Application with Team Build
Because .NET 1.1 is not directly supported by MSBuild, it is not supported by Team Build. Microsoft has released a project on CodePlex named MSBuild Extras (MSBee) that supports building .NET 1.1 applications. 

In order to build your .NET 1.1 applications, you need to upgrade your project file to a .NET 2.0 project file. You will also need to edit the Team Build project file so that it builds using the .NET 1.1 tools rather than the .NET 2.0 tools.

**To build a .NET 1.1 applications with Team Build**
* Upgrade your .NET 1.1 solutions to .NET 2.0. You can do this by opening the solution in Visual Studio 2005 and running the Conversion Wizard, or by running devenv [projectname](projectname) /upgrade 
* Ensure that the .NET 1.1 Software Development Kit (SDK) is installed on your build server.
* Download and install MSBuild Extras from [http://www.codeplex.com/MSBee](http://www.codeplex.com/MSBee)
* Download BuildingFx11inTB.targets from [http://blogs.msdn.com/gautamg/attachment/578915.ashx](http://blogs.msdn.com/gautamg/attachment/578915.ashx)
* Check out the build type from source control that will build your .NET 1.1 project.
* Copy BuildingFx11inTB.targets to the directory containing the build type and check the file into source control.
* Edit TFSBuild.proj file:
	* Import the BuildingFx11inTB.targets file:
{{
<Import Project="$(MSBuildProjectDirectory)\BuildingFx11inTB.targets" />  
}}
	* Add a property defining the CSharp targets:
{{
<PropertyGroup>
     <AdditionalPropertiesForBuildTarget>
        CustomAfterMicrosoftCommonTargets=$(ProgramFiles)\MSBuild\MSBee\MSBuildExtras.Fx1_1.CSharp.targets
    </AdditionalPropertiesForBuildTarget>
 </PropertyGroup> 
}}
* Check TFSBuild.proj into source control.

#### Additional Resources
* For more information about MSBuild Extras, see “MSBuild Extras - Toolkit for .NET 1.1 "MSBee” at [http://www.codeplex.com/MSBee](http://www.codeplex.com/MSBee)
* For more information about using MSBuild Extras to build .NET 1.1 applications, see “Building .NET 1.1 application using Team Build” at [http://blogs.msdn.com/gautamg/archive/2006/04/19/578915.aspx](http://blogs.msdn.com/gautamg/archive/2006/04/19/578915.aspx)

### How to Build Setup and Deployment Projects with Team Build
Team Build does not support setup projects by default. Use a custom post-build step to compile the setup project and copy the binaries to the build drop location as follows.

**1. Test the build.**
Make sure that the Team Build that you want to use for the setup project works. If it does not, fix it before moving on.

**Tip:** Most builds include the main project build as well as the setup build. If you are creating a new team build for the setup project only, do this before moving to step 2.

**2. Ensure that the setup project is built by default.**
# In Solution Explorer, right-click the installer project for which you need to create a team build.
# Click **Properties**.
# Click **Configuration Manager...**
# Select the build configuration(s) you want to build; for example, Debug, Release.
# Select the **Build** check box for the installer project.

**3. Ensure that all build paths in the project file are relative.**
* Open the solution folder for the installer project.
* Open the .vdproj file in an editor other than Visual Studio.
* Check out the .vdproj file for editing.
* Search for each of the following entries: **SccLocalPath**, **SccAuxPath**, **OutputFileName**, and **SourcePath**.
* Ensure that the path for each entry is relative and not absolute. (This is the default when a setup project is created.) Absolute paths start with a drive letter. Relative paths start with a double forward slash (‘\\’) or nothing.
* If you find an absolute path, replace it with a relative path. Do not modify any constant expressions. These are expanded by the installer later; for example:

{{ "OutputFileName" = "8:c:\\temp\\SetupProject.msi" would be replaced with "OutputFileName" = "8:debug\\SetupProject.msi" }}

**Tip:** Relative paths will be directly off of the project folder.

**Tip:** Always use double forward slash ( '\\' ) when creating paths because it will be passed through code that decodes to a single forward slash ( '\' ).
* If you had to make any changes, check the .vdproj file back in.

**4. Add a post-compile task to your team build.**
* Open the team build you want to use for the setup project.
* Check out the build type from source control:
	* You can find the build type beneath your team project in source control, in a subfolder of the TeamBuildTypes folder named TFSBuild.proj.
	* You might need to perform a **Get Latest Version** operation on the folder first.
* In Source Control Explorer, double-click TFSBuild.Proj to open it. 
**Note:** Viewing the build type from the Team Explorer will not work; because this opens a read-only copy of the build file.
* Add the following code to the end of the file between the last **</ItemGroup>** tag and the last **</Project>** tag:
{{
<Target Name="AfterCompile">
   <Exec Command="&quot;C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\devenv&quot; &quot;C:\Documents and Settings\darren\My Documents\
            Visual Studio 2005\Projects\HelloWorldTest\HelloWorldTestInstaller\HelloWorldTestInstaller.vdproj&quot; /Build &quot;Debug&quot;"/>
   <Copy SourceFiles="C:\Documents and Settings\darren\My Documents\Visual Studio 2005\Projects\HelloWorldTest\HelloWorldTestInstaller\Debug\
             HelloWorldTestInstaller.msi" DestinationFolder="$(OutDir)" />
   <Copy SourceFiles="C:\Documents and Settings\darren\My Documents\Visual Studio 2005\Projects\HelloWorldTest\HelloWorldTestInstaller
             \Debug\setup.exe" DestinationFolder="$(OutDir)" />
 </Target>
}}
* Check the paths in the pasted code to make sure that they are accurate for your build server.
**Tip:** Use the command line to test the path in the exec command tag. Replace each &quot; with a quote when testing on the command line, for example:

{{ "C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\devenv" "C:\Documents and Settings\darren\My Documents\Visual Studio 2005\Projects\HelloWorldTest\HelloWorldTestInstaller\HelloWorldTestInstaller.vdproj" /Build "Debug" }}

**Tip:** Use the command line to test the SourceFiles paths as well.

**5. Test the build changes.**
# In Team Explorer, right-click the build type and then click **Build Team Project**.
# Review the build summary to determine if the build passed or failed.
# If the build failed, click the link to the build log. Common reasons for failure include:
## **Exec command path is incorrect.**
## **Permissions are not set to allow the output files to be copied to the build directory.** Make sure that the tfsservice user account has permissions to copy from the binaries folder and to the build folder. The binaries folder is the location where the msi file will be placed after the solution builds. The build folder is specified in tfs.proj in the <BuildDirectoryPath> tag.
## **Permissions are not set to allow the installer to build.** Make sure that the tfsserver user account has permissions to read the .vdproj file and source files for your installer project as well as the application with which the installer is associated. Also make sure that the tfsserver user account has permissions to write binary files to the output directory; for example, Debug or Release.
## **Build configuration is incorrect.** Make sure that the build configuration you specify in the **exec** command exists for your project. For instance, your project might have "Debug|Any CPU" but not "Debug". You can check this by looking at the solution properties in Solution Explorer.
# If the build log does not give you enough information, create an output file for the exec command and review this log for more information. For example:
{{
<Exec Command="&quot;C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\devenv&quot; &quot;C:\Documents and Settings\darren\My Documents\
    Visual Studio 2005\Projects\HelloWorldTest\HelloWorldTestInstaller\HelloWorldTestInstaller.vdproj&quot; /Build &quot;Debug&quot; 
    > c:\temp\output.txt"/>
}}

#### Additional Resources
* For more information, see “Walkthrough: Configuring Team Foundation Build to Build a Visual Studio Setup Project” at [http://msdn2.microsoft.com/en-us/library/ms404859(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404859(VS.80).aspx) 

### How to Create a Team Build
You can create a new team build from the Team Builds folder in Team Explorer.

**To create a team build**
# Open Team Explorer.
# Expand the team project for which you want to create a build.
# Right-click the Team Builds folder in the tree.
# Select **New Team Build Type…**
# Specify the name of the new team build type and click **Next**.
# Select the projects you wish to build, this should include the project that contains your unit tests.
# Select a build configuration (e.g. release or debug) and click **Next**.
# Specify the name of your build server, e.g. **TFSRTM**
# Specify a local build directory on your build server, e.g. **c:\builds**
# Specify a drop location for your build output, e.g. \\**TFSRTM\NightlyBuilds** and then click **Next**.
# Click the **Run tests** checkbox, select the test list you want to associate with the build, and then click **Next**.
# Click **Finish** to create the team build type.

### How to Create Multiple Build Types  
To create multiple build types—for example, Release for Customers or Debug for Test Team—use separate team builds for each build type that interests you.

**To create a team build**
# Open Team Explorer.
# Expand the team project for which you want to create a build.
# Right-click the Team Builds folder in the tree.
# Select **New Team Build Type…**
# Specify the name of the new team build type and click **Next**.
# Select the projects you wish to build, this should include the project that contains your unit tests.
# Select a build configuration (e.g. release or debug) and click **Next**.
# Specify the name of your build server, e.g. **TFSRTM**
# Specify a local build directory on your build server, e.g. **c:\builds**
# Specify a drop location for your build output, e.g. \\**TFSRTM\NightlyBuilds** and then click **Next**.
# Click the **Run tests** checkbox, select the test list you want to associate with the build, and then click **Next**.
# Click **Finish** to create the team build type.

### How to Create a Team Build for a Project That References Assemblies from Another Project
To build a project that has dependencies on another team project, you need to get the source or assemblies from that project into the workspace on your build server. To do this, you need to edit your TFSBuild.proj file in order to add the assembly or the solution reference and override the **BeforeGet** event to get assemblies or sources from each of the required team projects.  

**To build a project that references assemblies in another team project**
* Check out the TFSBuild.proj** script from Source Control Explorer. 
* Add the following configuration setting under the **PropertyGroup** section: 
{{
<!-- to be added under PropertyGroup -->
<TfCommand>$(TeamBuildRefPath)\..\tf.exe</TfCommand>
<SkipInitializeWorkspace>true</SkipInitializeWorkspace>
}}
SkipInitializeWorkSpace allows you to skip invoking the default tasks to delete and re-create the workspace on the build machine. The new property is used in the custom target **BeforeGet** (see below).
* Add the following configuration setting to the **ItemGroup** entries that map both the Team Projects and the solutions. Make sure that you provide the correct local paths for the build machine. Multiple mappings cannot share the same local folder and will result in a **MappingConflictException** exception in the CreateWorkspace task.
{{
<ItemGroup>
  <!-- add one entry for every solution you reference -->
  <SolutionToBuild Include="$(SolutionRoot)\DependentApp\DependentApp.sln" />
  <SolutionToBuild Include="$(SolutionRoot)\YourApp\YourApp.sln" />
</ItemGroup>

<ItemGroup>
  <!-- add one entry for every Team Project you reference -->
  <Map Include="$/YourApp/YourApp">
    <LocalPath>$(SolutionRoot)\YourApp</LocalPath>
  </Map>
  <Map Include="$/DependentApp/DependentApp">
    <LocalPath>$(SolutionRoot)\DependentApp</LocalPath>
  </Map>
</ItemGroup>
}}
* Override the **BeforeGet** event to retrieve the workspaces for each Team Project: 
{{
<Target Name="BeforeGet">
  <DeleteWorkspaceTask 
      TeamFoundationServerUrl="$(TeamFoundationServerUrl)" 
      Name="$(WorkspaceName)" />
  <Exec 
    WorkingDirectory="$(SolutionRoot)" 
    Command="&quot;$(TfCommand)&quot; workspace /new $(WorkSpaceName) /server:$(TeamFoundationServerUrl)"/>
  <Exec 
   WorkingDirectory="$(SolutionRoot)"
   Command="&quot;$(TfCommand)&quot; workfold /unmap /workspace:$(WorkSpaceName) &quot;$(SolutionRoot)&quot;"/>
  <Exec 
    WorkingDirectory="$(SolutionRoot)" 
    Command="&quot;$(TfCommand)&quot; workfold /map /workspace:$(WorkSpaceName) 
          /server:$(TeamFoundationServerUrl) &quot;%(Map.Identity)&quot; &quot;%(Map.LocalPath)&quot;"/>
</Target> 
}}
* Check in the build script and run the build.

#### Additional Resources
* For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)

### How to Subscribe to Build E-mail Events
You can create a new project alert in order to subscribe to build e-mail events.

**To set up build e-mail alerts**
# Right-click the relevant team project in Team Explorer.
# Select **Project Alerts**.
# Select each alert option you would like to receive and enter an e-mail address for notification.

#### Additional Resources
* For more information about project alerts, see “Setting Alerts” at [http://msdn2.microsoft.com/en-us/library/ms181334(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181334(VS.80).aspx) 

### How to Receive Notification When a Build Has Failed
You can create a new project alert with a filter to receive e-mails only when the build fails.

**To create a project alert to notify you when a build fails**
* **Create and Test your Build.** Make sure that you have a Team Build type in place and that it runs without errors.
* **Register for BuildCompletionEvent event.** Use the **BisSubscribe.exe** tool to register for the **BuildCompletionEvent** event with a filter specifying that you only want the e-mail notification when the build fails, by using the following command-line syntax:

{{ bissubscribe /eventType BuildCompletionEvent /address myemail@domain.com /deliveryType EmailPlaintext /server tfsserver1 /filter "TeamProject = 'MyTeamProject' AND CompletionStatus=‘Failed’“ }}

* **Test the build.** Test the build by checking in code that fails to compile, execute the build, and ensure that an e-mail notification is received.

#### Additional Resources
* For more information about filtering the build completion event, see “How to Filter the Build Completion Event” at [http://blogs.msdn.com/jpricket/archive/2006/09/05/how-to-filter-the-build-completion-event.aspx](http://blogs.msdn.com/jpricket/archive/2006/09/05/how-to-filter-the-build-completion-event.aspx) 
* For more information about BuildCompletionEvent filters, see “Useful BuildCompletionEvent Filters” at [http://blogs.msdn.com/jpricket/archive/2006/09/05/useful-buildcompletionevent-filters.aspx](http://blogs.msdn.com/jpricket/archive/2006/09/05/useful-buildcompletionevent-filters.aspx)   

### How to Start a Build
You can start a build type from the Team Builds folder in Team Explorer.

**To manually start a build**
# Open Team Explorer.
# Expand the team project for which you want to start a build.
# Expand the Team Builds folder in the tree.
# Right-click the Team Build type you want to start.
# Select **Build Team Project**.

### How to Verify That the Build Succeeded
You can check build status from the Builds window, accessible from Team Explorer.

**To verify that a build succeeded**
# Open Team Explorer.
# Expand the team project for which you want to see results.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to see results. 

### How to View the Build Output
You can view build output from the Builds window, accessible from Team Explorer.

**To view build output**
# Open Team Explorer.
# Expand the team project for which you want to see build output.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to see build output.
# Double-click the Team Build result entry for the build number for which you want to see output.
# If you want to see the build output folder, click the **Build name** link.
# If you want to see the build log, click the **Log** link.

### How to Change the Build Server Location
In order to change the build server location for an existing Team Build, you modify the <**BuildMachine>** tag in TFSBuild.proj.

**To change the build server location for an existing Team Build type**
# Open Source Control Explorer.
# In Source Control Explorer, expand your team project folder.
# Expand the TeamBuildTypes folder.
# Select the Team Build folder for which you want to turn on code analysis.
# Check out the TFSBuild.proj file from source control. You might need to perform a **Get Latest Version** operation on the folder first.
# In Source Control Explorer, double-click TFSBuild.Proj to open it. 
# Modify the **<BuildMachine>** tag to point to the new server.
# Save TFSBuild.proj and check it back into source control.

#### Additional Resources
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 

### How to Change the Build Output Location
In order to change the build output location for an existing Team Build, modify the <**DropLocation>** tag in TFSBuild.proj.

**To change the build server location for an existing Team Build type**
# Open Source Control Explorer.
# In Source Control Explorer, expand your team project folder.
# Expand the TeamBuildTypes folder.
# Select the team build folder for which you want to turn on code analysis.
# Check out the TFSBuild.proj file from source control. You might need to perform a **Get Latest Version** operation on the folder first.
# In Source Control Explorer, double-click TFSBuild.Proj to open it. 
# Modify the **<DropLocation>** tag to point to the new location.
# Save TFSBuild.proj and check it back into source control.

#### Additional Resources
* For more information about customizing Team Foundation Build, see “Customizing Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400688(VS.80).aspx) 
### How to Determine What Changesets Are Part of the Build
You can view changesets associated with each build from the Builds window, accessible from Team Explorer.

**To view changesets associated with a build**
# Open Team Explorer.
# Expand the team project for which you want to view changesets.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to view changesets.
# Double-click the Team Build result entry for the build number for which you want to view changesets.
# Expand the **Associated changesets** item.
# If you want to see more information about a particular changeset, click the **ID** link.

### How to Change the Reported Build Quality 
You can change build quality from the Builds window, accessible from Team Explorer.

**To change the build quality**
# Open Team Explorer.
# Expand the team project for which you want to change the build quality.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to change the build quality.
# In the **Build Quality** drop-down list, select the build for which you want to set build quality, and then set a build quality value.

## Projects
* **How to use a single-solution strategy** 
* **How to use a partitioned-solution strategy**
* **How to use a multiple-solution strategy** 

### How to Use a Single-Solution Strategy 
If you work on a small system, consider using a single Visual Studio solution to contain all of your projects. This strategy simplifies development because all of the code is available when you open the solution. This strategy also makes it easy to set up references, because all references are between projects in your solution. You might still need to use file references to reference third-party assemblies (such as purchased components) that are outside your solution.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

### How to Use a Partitioned-Solution Strategy
If you work on a large system, consider using multiple Visual Studio solutions, each representing a subsystem of your application. These solutions can be used by developers to work on smaller parts of your system without having to load all code across all projects. Design your solution structure so that any projects that have dependencies are grouped together. This enables you to use project references rather than file references. Consider creating a master solution file that contains all of the projects, if you want to use this to build the entire application.

When working with multiple solutions, use a flat file structure for all of your projects. A typical example is an application that has a Microsoft Windows Forms project, an ASP.NET project, a Windows service, and a set of class library projects shared by some or all of those projects.
 
You can use the following flat structure for all projects:
# /Source
# /WinFormsProject
# /WebProject
# /WindowsServiceProject
# /ClassLibrary1
# /ClassLibrary2
# /ClassLibrary3
# Web.sln
# Service.sln
# All.sln

By keeping the structure flat, you gain a lot of flexibility and the ability to use solutions for presenting different views of the projects. Designing the physical folder structure around solution files is very hard to change, especially if you realize that you need to reuse a class library from another solution.

**Note:** If you are building with Team Build (which relies on MSBuild), it is possible to create solution structures that do not include all referenced projects. As long as the entire solution has been built first, generating the binary output from each solution, MSBuild is able to follow project references outside the boundaries of your solution and build successfully. You cannot build solutions created in this way from the Visual Studio build command, and this approach only works with Team Build and MSBuild.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

### How to Use a Multiple-Solution Strategy 
If you work on a very large solution requiring many dozens of projects, you might run up against solution scalability limits. In this scenario, you should break your application into multiple solutions, but do not create a master solution for the entire application because all references inside each solution are project references. References to projects outside of each solution (for example, to third-party libraries or projects in another sub-solution) are file references. This means that there can be no “master” solution. Instead, a script must be used that understands the order in which the solutions must be built. One of the maintenance tasks associated with a multiple-solution structure is ensuring that developers do not inadvertently create circular references between solutions. This structure requires complex build scripts and explicit mapping of dependency relationships. In this structure, it is not possible to build the application in its entirety within Visual Studio. Instead, you use TFS Team Build.

#### Additional Resources
* For more information, see “Chapter 3 – Structuring Projects and Solutions in Source Control” in this guide.

## Reporting
* **How to view build quality**
* **How to view all the check-ins for a build**
* **How to view work items or bugs closed for a build**
* **How to view open work items or bugs for a build**
* **How to track velocity from build to build**
* **How to track test case pass/fail results for a build**
* **How to review build status (BVT results)**

### How to View Build Quality
You can view build quality from the Builds window, accessible from Team Explorer.

**To view build quality**
# Open Team Explorer.
# Expand the team project for which you want to view build quality.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type to view build quality.

If you are using the Microsoft Solutions Framework (MSF) for CMMI® Process Improvement (MSF CMMI) process template, you can view the Builds report in order to see build quality as well as additional information on test results, code coverage and code churn.

**To view build quality in MSF CMMI**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Builds** report.

### How to View All the Check-ins for a Build
You can view check-ins associated with each build from the Builds window, accessible from Team Explorer.

**To view check-ins associated with a build**
# Open Team Explorer.
# Expand the team project for which you want to view check-ins for a build.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to view check-ins for a build.
# Double-click the Team Build result entry for which you want to view check-ins for a build.
# Expand the **Associated changesets** item to see all check-ins associated with the build
# If you want to see more information on a particular changeset (which represents a check-in), click the **ID** link.

### How to View Work Items or Bugs Closed for a Build
You can view work items and bugs that have been closed for each build from the Builds window, accessible from Team Explorer.

**To view work items associated with a build**
# Open Team Explorer.
# Expand the team project for which you want to view work items.
# Expand the Team Builds folder in the tree.
# Double-click the Team Build type for which you want to view work items.
# Double-click the Team Build result entry for the build number for which you want to view work items.
# Expand the **Associated work items** item.

### How to View Open Work Items or Bugs for a Build
If you are using the MSF CMMI process template, you can view the Open Issues and Blocked Work Items Trend report to view open, resolved, and closed work items over a given time period. However, because the report presents the information by date instead of by build, you need to translate the results into builds according to the date on which the build was produced.

To view open work items or bugs for a build
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Open Issues and Blocked Work Items Trend** report.

### How to Track Velocity from Build to Build
You can use the Velocity report to track the progress and the rate at which work items are getting completed from build to build. This report is available in both MSF CMMI and MSF for Agile Software Development (MSF Agile).

**To track velocity from build to build**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Velocity** report.

### How to Track Test Case Pass/Fail results for a Build
You can use the Quality Indicators report to track the number of test cases that pass and fail over a given time period. The report presents the information by date instead of by build. As a result, you need to translate the results into builds according to the date at which the build was produced. This report is available in both MSF CMMI and MSF Agile.

**To track test case pass/fail for a build**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Quality Indicators** report.

### How to Review Build Status (BVT Results)
If you are using the MSF CMMI process template, you can view the Builds report in order to see BVT results.

**To review build status**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Builds** report.

## Scheduled Builds
* **How to automatically run nightly builds**
* **How to decide on a build frequency and type for your project**

### How to Automatically Run Nightly Builds
The Team Build feature in TFS does not support scheduled builds from the user interface. Instead, you can use the Microsoft Windows Task Scheduler to run the TFSBuild command utility to start builds at predetermined time.

**To create a scheduled build**
* Create a TFSBuild command line as follows:

{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

* Place the command line in a batch file.
* Create a Windows Scheduled Task that runs the batch file at your desired interval.

For more information and expanded steps, see “How To – Set Up a Scheduled Build with Visual Studio Team Foundation Server” in this guide.

#### Additional Resources
* For more information, see “Chapter 9 – Setting Up a Scheduled Build with Team Build” in this guide.

### How to Decide on a Build Frequency and Type for Your Project
The frequency of your builds is one of the most important decisions to make when creating a scheduled build.

If you are working on a project that has enough check-ins to cause significant changes within an hour, and you do not use Continuous Integration (CI) builds, you can choose an hourly build frequency. Hourly builds provide rapid feedback to developers and can also be made available to testers and other team members to solicit their feedback.

If you are working on a project that has enough check-ins to cause significant changes within a day, you can use daily scheduled build frequency because it gives your test and development teams a new build every morning that incorporates the changes from the previous day, ready to be tested.  

If you are working on a large, complex project where the build time can last for days, you should opt for weekly builds. This ensures that your test team will have a build at the start of each week incorporating the changes from the previous week, ready to be tested.   

#### Additional Resources
* For more information about setting up scheduled builds, see “How To – Set Up a Scheduled Build with Visual Studio Team Foundation Server” in this guide.
* For more information, see “Chapter 9 – Setting Up Scheduled Build with Team Build” in this guide.

## Test-Driven Development
* **How to create a “hello world” acceptance test**
* **How to run automated tests as part of the build**
* **How to run code analysis as part of the build**
* **How to get failed tests to fail a build**

### How to Create a “Hello World” Acceptance Test
A “hello world” acceptance test is a simple test that you can use to prove that you can create unit tests and hook them up to your build process. 

In order to create a test list to associate with the build you must have either Visual Studio Test Edition or Visual Studio Team Suite installed. In order to run automated tests on the build server you must have either Visual Studio Developer Edition, Visual Studio Test Edition, or Visual Studio Team Suite installed on the build server. 

**To create a hello world test**
# On the **Test** menu, click **New Test**…
# Click **Unit Test** and then click **OK**.
# Enter a name for your test project and then click **Create**.
# Compile your new project.
# Check the project into source control.
# With your unit test solution still open in Visual Studio, on the **Test** menu, click **Create New Test List**...
# Specify a test list name in the **Create New Test List** dialog and then click **OK**.
# In the Test Manager, click on the **All Loaded Tests** node.
# Drag and drop tests from the available tests into your test list node in the tree.
# Check the modified unit test project VSMDI file into source control.

The test list you have created is available when you create a new Team Build and can be run automatically as part of the build process.

#### Additional Resources
* For more information about automatically running Build Verification Tests, see “How to: Configure and Run Build Verification Tests (BVTs)” at [http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx) 
* For more information about how to run automated build tests without Visual Studio Test Edition or a VSMDI file, see “How to run tests in a build without test metadata files and test lists (.vsmdi files)” at [http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx](http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx) 

### How to Run Automated Tests as Part of the Build
You can run automated tests to automatically gain feedback on build quality after every build. In order to run automated tests, you must have Visual Studio Developer Edition as well as Visual Studio Test Edition on the build server, or you can install the entire Team Suite. Developer Edition is necessary in order to run the build, while Test Edition is necessary in order to set up tests and test lists that can be run.

**To run automated tests as part of the Team Build process**
# Create one or more automated tests that you want to run with the build.
# On the **Test** menu, click **Create New Test List**...
# Use the Test Manager to group tests into the new Test List by dragging and dropping the tests from the Test View to the Test List in the Test Manager.
# Create a new Team Build type.
# Select the check box to run automated tests.
# Select the test project within which your tests and test list were created
# Select the test list you want to run.

#### Additional Resources
* For more information about automatically running Build Verification Tests, see “How to: Configure and Run Build Verification Tests (BVTs)” at [http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182465(VS.80).aspx) 
* For more information about how to run automated build tests without Visual Studio Test Edition or a VSMDI file, see “How to run tests in a build without test metadata files and test lists (.vsmdi files)” at [http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx](http://blogs.msdn.com/buckh/archive/2006/11/04/how-to-run-tests-without-test-metadata-files-and-test-lists-vsmdi-files.aspx) 

### How to Run Code Analysis as Part of the Build
To turn on code analysis for a build type, you can either select the code analysis check box in the New Team Build Type Creation Wizard when you create the new Team Build type, or you can modify the TFSBuild.proj file after the build type has been created. 

**To enable code analysis in the TFSBuild.proj file**
* If you want all projects to run code analysis, regardless of project settings, change the **<RunCodeAnalysis>** tag to **Always**.
* If you want to run code analysis on each project based on project settings, change the **<RunCodeAnalysis>** tag to **Default**.

#### Additional Resources
* For more information about automatic code analysis as part of the build, see “How To – Automatically Run Code Analysis with Team Build in Visual Studio Team Foundation Server” in this guide.
* For more information about code analysis tools, see “Guidelines for Using Code Analysis Tools” at [http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx) 

### How to Get Failed Tests to Fail a Build
When a build fails because of compilation errors, a work item is created to track the failure and the build is marked as failed. When an automated test fails, however, the build does not fail. The test failure is converted into a warning and the build continues.

You might want to fail the build if an associated automated test fails. You might also want to generate a work item automatically to track the failure.

**To fail the build upon test failure**
# Open the Microsoft.TeamFoundation.Build.targets file from Program Files\MSBuild\Microsoft\VisualStudio\v8.0\TeamBuild.
# Check out for edit and open the TFSBuild.proj file for the Team Build type you want to have failed upon test failure.
# Copy the **RunTestWithConfiguration** target from Microsoft.TeamFoundation.Build.targets to the end of the TFSBuild.proj file, just before the closing </Project> tag.
# Modify the **ContinueOnError** attribute from **true** to **false**. 
**Note:** There will be two test tool tasks. Modify the end-to-end task in order to only modify the behavior of builds on the build server. Use the desktop build task when building on a developer’s desktop.

Alternatively, if you want all Team Build types to fail upon test failure, you can modify Microsoft.TeamFoundation.Build.targets directly. This change will modify behavior for all Team Build types.

The solution recommended above is straightforward to implement but is not guaranteed to continue working for future versions of Visual Studio. If you want to implement a solution that is guaranteed to continue working after upgrade, see Aaron Hallberg’s blog entry “Determining Whether Tests Passed in Team Build” at [http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx](http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx)

#### Additional Resources
* For more information about setting up the build to create a work item upon test failure, see “Create Workitems for Test Failures in TeamBuild” at [http://blogs.msdn.com/nagarajp/archive/2005/10/14/481290.aspx](http://blogs.msdn.com/nagarajp/archive/2005/10/14/481290.aspx)  
* For more information about a solution that is guaranteed to continue working after a Visual Studio upgrade, see “Determining Whether Tests Passed in Team Build” at [http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx](http://blogs.msdn.com/aaronhallberg/archive/2006/09/21/determining-whether-tests-passed-in-team-build.aspx) 

## Team Build Resources
* For an overview of Team Foundation Build, see “Overview of Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms181710(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181710(vs.80).aspx)