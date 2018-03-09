## Guidelines:  Project Management
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Areas and Iterations
* _Use areas for better traceability._
* _Use iterations to represent milestones in your project._
* _Create a separate iteration for unassigned scenarios and tasks._
* _Determine appropriate iteration cycle duration._

### Check-in Policies
* _Use check-in policies to enforce code quality._
* _Use check-in policies to ensure that developers associate work items with check-ins._
* _Create check-in policies to enforce coding standards._ 
* _Set up notifications to inform you when developers bypass check-in policies._

### Process Templates
* _Use the MSF Agile process template when working on projects that only require a lightweight or informal process._
* _Use the MSF CMMI process template when working on projects requiring a more formal process or conformance with CMMI standards._
* _Consider using a minimal process template._
* _Modify an existing process template to match your team’s process._

### Security Groups and Permissions
* _Create security groups to grant a specific set of permissions._
* _Assign team members to the appropriate security group._

### Team Projects
* _Create one team project per application if you want to migrate work items and other assets between application versions._
* _Create one team project per version if you want to start with new work items and other assets with each application version._
* _Grant only required permissions on project assets._ 
* _Structure your source tree to support branching._

### Work Items
* _Capture your scenarios at the start of your project._
* _Define your Quality of Service requirements appropriately._
* _Break scenarios into manageable, modular development tasks._
* _Set acceptance criteria for each task._
* _Link requirements and tasks to scenarios._
* _Use Microsoft Excel for bulk editing of work items._

## Areas and Iterations
* **Use areas for better traceability.**
* **Use iterations to represent milestones in your project.**
* **Create a separate iteration for unassigned scenarios and tasks.**
* **Determine appropriate iteration cycle duration.**

### Use Areas for Better Traceability
Use areas in your team project to keep project tasks, bugs, requirements, and other work items organized. You can also set permissions on areas to restrict access to various parts of your team project. 

Use areas to represent logical or physical components, and then create sub-areas to represent specific features. This structure helps you keep your work items organized and can be used to improve traceability by component or feature.

**To create areas for your project**
# In Team Explorer, click your team project. 
# On the **Team** menu, point to **Team Project Settings**, and then click **Areas and Iterations**.
# In the **Areas and Iterations** dialog box, click the **Area** tab.
# Click the **Add a child node** toolbar button.
# Right-click the new node, click **Rename**, and then type the area name you want.
# Click the **Area** node.
# Repeat steps 2, 3, and 4 to create additional areas and to create a hierarchy for your project structure.

Beware of creating too complex area structure, while areas allow you to partition work items permissions, there is overhead associated with managing those permissions for complex trees. It may also be problematic to copy over the structure/ permissions to other Team projects.

#### Additional Resources
* For more information about using areas, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

### Use Iterations to Represent Milestones in Your Project
Use iterations to define how many times your team will repeat a particular set of major activities (such as planning, implementation, or testing) during the course of application development. This set of major activities should represent a milestone for the project with a quantifiable outcome such as feature complete or component complete. 

**To create an iteration**
# In Team Explorer, click your team project. 
# On the **Team** menu, point to **Team Project Settings**, and then click **Areas and Iterations**.
# In the **Areas and Iterations** dialog box, click the **Iteration** tab.
# Click the **Add a child node** toolbar button.
# Right-click the new node, click **Rename**, and then type the iteration name.
# Click the **Iteration** node.
# Repeat steps 2, 3, and 4 to create additional iterations identified for your project.
# Click **Close**.

**Note**: The Microsoft® Solutions Framework (MSF) for Agile Software Development (MSF Agile) process template includes three predefined iterations. Depending on your specific requirements, you can delete these iterations, rename them instead of creating new ones, or leave them unchanged.

#### Additional Resources
* For more information about using iterations, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

### Create a Separate Iteration for Unassigned Scenarios and Tasks
Create a separate iteration to which you can assign all the scenarios and tasks that have not yet been assigned to any iteration. This helps you to easily identify the scenarios and tasks that are pending when planning your iterations. 

**To create a separate iteration**
# In Team Explorer, click your team project. 
# On the **Team** menu, point to **Team Project Settings**, and then click **Areas and Iterations**.
# In the **Areas and Iterations** dialog box, click the **Iteration** tab.
# Click the **Add a child node** toolbar button.
# Right-click the new node, click **Rename**, and then type the iteration name **Iteration 999**
# Click **Close**.

#### Additional Resources
* For more information about creating iterations, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

### Determine Appropriate Iteration Cycle Duration
When setting up your team project, determine the appropriate iteration cycle duration based on the size and complexity of your project.

Keep the following key points in mind when determining iteration cycle duration:
* The iteration cycle should be long enough to allow team members to get substantial work done, and should cover at least a few different scenarios. 
* The iteration cycle should be short enough to flexibly accommodate changes and priorities.

In practice, a two-week iteration cycle works for most projects.

#### Additional Resources
* For more information about iteration cycle duration, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.
* For further information about iteration cycle duration, see “Chapter 11 – Project Management Explained” in this guide.

## Check-in Policies
* **Use check-in policies to enforce code quality.**
* **Use check-in policies to ensure that developers associate work items with check-ins.**
* **Create check-in policies to enforce coding standards.** 
* **Set up notifications to inform you when developers bypass check-in policies.**

### Use Check-in Policies to Enforce Code Quality
Use a combination of code analysis and testing policies to improve check-in quality for your project. For example, use the supplied testing policy to ensure that specific tests are executed and passed prior to allowing source to be checked into Microsoft Visual Studio® 2005 Team Foundation Server (TFS) source control. You can also configure a code analysis policy to help ensure that your code meets certain quality standards by ensuring that security, performance, portability, maintainability, and reliability rules are passed.

By enforcing this type of check-in policy in addition to policies that enforce coding standards and guidelines, you ensure that your code meets a specific quality standard.

**To enforce a code analysis check-in policy for a team project**
# In Team Explorer, right-click your team project, point to **Team Project Settings**, and then click **Source Control**. 
# Click the **Check-in Policy** tab, click **Add**, and then select and configure the appropriate policy.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.

### Use Check-in Policies to Ensure That Developers Associate Work Items with Check-ins
Set the Work Items check-in policy to force developers to associate their check-in with a work item. 

If a build breaks, it is important that you know what changesets are associated with the build, and what work items those changesets are associated with, so that you can identify the developer responsible for checking in this code and the area of the project on which the developer is working.

**To set the Work Items check-in policy to force developers to associate their check-in with a work item**
# In Team Explorer, right-click your team project**,** select** Team Project Settings**, and then click **Source Control**.
# Click the **Check-in Policy** tab.
# Click **Add** and then select and configure the **Work Item** check-in policy.

#### Additional Resources
* For more information about check-ins, see “How to: Check In Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx) 
* For more information about work items and changesets, see “How to: Associate Work Items with Changesets” at [http://msdn2.microsoft.com/en-us/library/ms181410(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181410(VS.80).aspx) 

### Create Check-in Policies to Enforce Coding Standards
The project you are working on may require coding standards that are not covered by static code analysis or by existing check-in policies. For example, your project may require that your code never uses the tab character, or that all check-ins require comments. You can create new check-in policies to cover these scenarios.

**To enforce a code analysis check-in policy for a team project**
# In Team Explorer, right-click your team project, point to **Team Project Settings**, and then click **Source Control**.
# Click the **Check-in Policy** tab and then click **Add**.
# In the **Add Check-in Policy** dialog box, select **Code Analysis** and then click **OK**.
# In the **Code Analysis Policy Editor**, select either **Enforce C/C++ Code Analysis (/analyze)** or **Enforce Code Analysis** **For Managed Code**. Select both if your project contains a combination of managed and unmanaged code.
# If you select managed code analysis, configure your required rule settings for managed code analysis based on your required coding standards. 
This determines precisely which rules are enforced.

You can also create a custom check-in policy to perform checks that are not available by default. For example, you can disallow code patterns such as banned application programming interface (API) calls, or you can write a policy to enforce your team’s specific coding style guidelines, such as where braces should be positioned within your source code.

#### Additional Resources
* For more information about creating check-in policies, see “How To – Create Custom Check-in Policies in Visual Studio Team Foundation Server” in this guide.

### Set Up Notifications to Inform You When Developers Bypass Check-in Policies
Team Foundation Server Version Control does not prevent you from overriding a check-in policy. However, you can use the following steps to detect if a check-in policy has been overridden:
# Use the Team Foundation Server Eventing Service (from the Team Foundation Core Services API) for hooking check-in events.
# Write a **Notify** method that parses the details of the changeset and then reacts to it if an override has occurred.

Alternatively, you can manually scan changeset history to discover policy overrides.

#### Additional Resources
* To learn more about overriding a check-in policy, see “How to: Override a Check-in Policy” at  [http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx) 

## Process Templates 
* **Use the MSF Agile process template when working on projects that only require a lightweight or informal process.**
* **Use the MSF CMMI process template when working on projects requiring a more formal process or conformance with CMMI standards.**
* **Consider using a minimal process template.**
* **Modify an existing process template to match your team’s process.**

### Use the MSF Agile Process Template When Working on Projects That Only Require a Lightweight or Informal Process
When using Test-Driven Development (TDD) or other agile methodologies, you should use the MSF for Agile Software Development (MSF Agile) process template. This is a lightweight process for agile software projects. You should use this project template as your first choice, unless you specifically need the additional process improvement features provided by the MSF for CMMI Software Development (MSF CMMI) process template.

You can easily edit the MSF Agile process template and modify it to suit your process requirements.

#### Additional Resources
* For more information, see “Chapter 11 – Project Management Explained” in this guide.
* For more information about the MSF Agile process template, see “Chapter 13 – MSF for Agile Software Development Projects” in this guide.
* For more information about customizing the process template, see “How To – Customize a Process Template in Visual Studio Team Foundation Server” in this guide.

### Use the MSF CMMI Process Template When Working on Projects Requiring a More Formal Process or Conformance with CMMI Standards
When using a formal software development process aimed at improving the existing process, you should use the MSF for CMMI Software Development (MS CMMI) process template. 

You can easily edit and modify this process template to suit your process requirements.

#### Additional Resources
* For more information, see “Chapter 11 – Project Management Explained” in this guide.
* For more information about customizing the template, see “How To – Customize a Process Template in Visual Studio Team Foundation Server” in this guide.

### Consider Using a Minimal Process Template
Many teams do not require support for all parts of a standard team project. For example, many teams want to use the source control portion of a team project but not the Microsoft Office SharePoint® portal. Team project templates can be modified, and it is possible to remove some parts of the template that you do not need. When you modify the template, you will need to keep the Group Permissions and Classifications sections; however, you can keep or remove the other sections as you see fit.

In order to create a minimal process template, you use the Process Template Manager to download the template to your local computer, edit the template to remove the sections you are not going to use, and then upload the template back to the server.

#### Additional Resources
* For more information about process templates, see “Chapter 13 – Process Templates Explained” in this guide.
* For more information about customizing process templates, see “How To – Customize a Process Template in Visual Studio Team Foundation Server” in this guide.
* For further information about customizing process templates, see “Customizing Process Templates” at [http://msdn2.microsoft.com/en-us/library/ms243782(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms243782(VS.80).aspx)
* For more information on using a minimal process template see, “How to use TFS for source control only” at http://blogs.msdn.com/richardb/archive/2007/05/10/how-to-use-tfs-for-source-control-only.aspx

### Modify an Existing Process Template to Match Your Team’s Process
The project you are working on might not fit the out-of-box process templates provided with Microsoft Visual Studio Team System (VSTS). You might need a different work item type, or you might be using an entirely different process methodology. In this case, you should modify the existing process template. Choose the process template that most closely meets your process requirements and then modify the template as necessary.

The following areas of the process templates commonly need to be customized:
* Groups and Permissions
* Work Item Types
* Source Control Check-in Notes and Policies
* Areas and Iterations
* Reports
* Team Portal
* Process Guidance

#### Additional Resources
* For more information about process templates, see “Chapter 13 – Process Template Explained” in this guide.
* For more information about customizing the template, see “How To – Customize a Process Template in Visual Studio Team Foundation Server” in this guide.

## Security Groups and Permissions
* **Create security groups to grant a specific set of permissions.**
* **Assign team members to the appropriate security group.**

### Create Security Groups to Grant a Specific Set of Permissions
When you create a project in Team Foundation Server, four default groups are created for that project regardless of your choice of process template. By default, each of these groups has a set of permissions defined for it that governs what members of those groups are authorized to do. The four groups are:
* Project Administrator
* Contributor
* Reader
* Build Services. 

You can create security groups for your team project to better meet your organization’s security requirements. Creating a security group is an efficient way to grant a specific set of permissions to a group of users on your team project. Make sure that you allow only the minimum permissions necessary for the group, and add only those users or groups who must belong to this new team project group.

Additionally use the following guidelines:
* Do not change the permissions on default groups (or if you do, do it in every project the same way)
* Use Active Directory (AD) groups for membership on server level only
* Use TFS groups for permissions settings (rather than AD groups)
* Never deny anything (usually deny means that the partitioning you use is less than ideal); make sure you reason is sound when you do

#### Additional Resources
* For more information on creating security groups, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.
* For more information on TFS permissions, see “Team Foundation Server Permissions” at [http://msdn2.microsoft.com/en-us/library/ms252587(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252587(VS.80).aspx)  

### Assign Team Members to the Appropriate Security Group
Identify the team members who will be working on the project and their roles, and assign these team members to TFS by using existing team project groups, server-level groups, or custom security groups that you create.

When assigning members to a security group, assign only those members who need the permissions available to that security group. If necessary, you can create custom security groups with appropriate security permissions and then assign users to those security groups.

#### Additional Resources
* For more information about security groups, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

## Team Projects
* **Create one team project per application if you want to migrate work items and other assets between application versions.**
* **Create one team project per version if you want to start with new work items and other assets with each application version.**
* **Create one team project per team when working with large projects that span multiple projects.**
* **Grant only required permissions on project assets.** 
* **Structure your source tree to support branching.**

### Create One Team Project per Application if You Want to Migrate Work Items and Other Assets Between Application Versions
If you want to carry forward not only source code but also work items and other TFS assets between releases, consider using one team project per application. When you use a single team project for multiple versions of the application, all of the TFS assets are carried forward automatically for the next release. When you are ready to release a new version of your application, you can create a branch within the project to represent the release and isolate that code.

Keep the following key points in mind when using one project per application:
* Parallel releases are forced to share work items schema, check in policies, and process guidance.  
* Reporting is more difficult; because reports default to the entire project, you must add filtering by release.
* If you have hundreds of applications, each in its own project, you will run up against TFS performance and scale limits.
* You will accumulate ‘baggage’ over multiple releases. The easiest way to address this issue is to create a new project and branch the code you want to carry forward into that project.

#### Additional Resources
* For more information about using team projects, see “When to use Team Projects” at http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx 

### Create One Team Project per Version if You Want to Start with New Work Items and Other Assets with Each Application Version
If you want each release to start fresh without carrying forward work items and other TFS assets, consider using one project per release. When you use a new project for each release, you can modify work item schema, workflow, check-in policies, and other assets without impacting the old release. This can be especially useful if the old release will be maintained by a separate team such as a sustained engineering team who may have a different process and workflow than your main development team.

Keep the following key points in mind when using one project per release:
* Although it is very easy to move the source code from one project to another, it is difficult to move work items and other TFS assets from one project to another. Because work items can only be copied one at a time to another project, if you want to copy sets of work items, you will need to write your own utility.
* If you have hundreds of applications and releases, each in its own project, you will run up against TFS performance and scale limits.
* Choose a structure you can live with in the long term because restructuring existing team projects is difficult.
* Source can be easily shared among team projects as follows:
* Branch source from one project to another.
* Map source from another project into your workspace.
* Team Foundation Server can scale to ~500 projects by using the MSF Agile process template or 250 projects using the MSF CMMI process template. If you create your own process template or customize an existing process template, keep in mind that the work item schema has the largest impact on server scalability. A complex schema will result in a server capable of supporting fewer projects. 
* You will have to carry over all the areas from the original project; and perhaps also change the permissions in source control.

#### Additional Resources
* For more information about using team projects, see “When to use Team Projects” at http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx

### Grant Only Required Permissions on Project Assets 
When creating team projects, review the default security groups created by the process and, if necessary, create security groups with appropriate permissions. You then assign the project members to appropriate groups to ensure that each member gets only the permissions he or she requires on project assets.   

#### Additional Resources
* For more information about granting permissions, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

### Structure Your Source Tree to Support Branching
When creating your source tree structure, make sure that it supports branching. Keep separate folders for source and for other project assets, so that if isolation development is required in the future, you can simply branch the source folder. Also make sure that you maintain separate folders for each component within the source folder, so that partial branching can be performed if required.

Segregate other entities such as shared code, unit tests, library dependencies, and so on by using folders so that they can be excluded or included during branching as required.

The following is an example of a source tree structure that supports branching:
* **Main** – Container for all assets you need to ship the product
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
	* **Docs** – Container for documentation that will ship with the product 
	* **Installer** – Container for installer source code and binaries 
	* **Builds** – Container for Team Build scripts
	* **Tests** – Container for test team test cases 

#### Additional Resources
* For more information about source tree structure, see “Chapter 5 – Defining Your Branching and Merging Strategy” in this guide.

## Work Items
* **Capture your scenarios at the start of your project.**
* **Define your Quality of Service requirements appropriately.**
* **Break scenarios into manageable, modular development tasks.**
* **Set acceptance criteria for each task.**
* **Link requirements and tasks to scenarios.**
* **Use Microsoft Excel for bulk editing of work items.**

### Capture Your Scenarios at the Start of Your Project
Create and capture a set of project scenarios at the start of your project. This helps you to gain a complete picture of your project and can later be used track progress. During the course of development, you can modify existing scenarios or add new scenarios to represent what you learn over time.

**To capture scenarios at the start of the project**
# Use the project back log (PBL) document, which is a requirement document based on input from various stakeholders (including customers, business analysts, end users, and product managers), and scope out the scenarios for your project. 
# In Team Explorer, expand the project node, right-click the Work Items folder, point to **Add Work Item**, and then click **Scenario**.
# On the New Scenario page, enter the details for the scenario. Make sure to set the Iteration to **Iteration 999**. 
# Save your new scenario. 
# Repeat the above steps for all scenarios that you have identified for the project.

#### Additional Resources
* For more information about capturing scenarios, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.

### Define Your Quality of Service Requirements Appropriately
Define your Quality of Service (QoS) requirements for each of the scenarios to be worked on during the iteration cycle. This helps to define the acceptance criteria for the scenario. The inputs for the QoS requirements come from project goals and requirements and specification documentation, if available.

**To define your QoS requirements**
# Right-click your project’s Work Items folder, point to **Add Work Item**, and then click **Quality of Service Requirements**.
# On the New Quality of Service Requirements page, add the following details: 
## Set the **Type** to an appropriate value such as performance, scalability, stress, or security. 
## Set the **Iteration** to the current iteration cycle.
## From the **Links** tab, link the QoS to a specific scenario for easier traceability. 
# Save the new QoS requirement.
# Create one QoS requirement for each discipline or type of quality requirement, bearing in mind that each scenario can have multiple QoS requirements.
# Make sure that you create QoS requirements for all of the scenarios being worked on during a specific iteration cycle.

**Important:** You can break down the QoS requirements into test tasks later. 

#### Additional Resources
* For more information about defining QoS requirements, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.
* For more information about work items, see “Managing Team Foundation Work Items” at [http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx)  

### Break Scenarios into Manageable, Modular Development Tasks
During iteration planning, break your scenarios into user stories and then further break the user stories into development tasks. Make sure that the development tasks you create are manageable and modular. The tasks should not last for more than one or two days. If they are larger than this, you need to break the tasks down into smaller tasks or sub-tasks. Doing this contributes to schedule flexibility and improved manageability of the project.

**To break scenarios into manageable, modular development tasks**
# Break down the chosen scenarios into developer stories.
# Subdivide the developer stories into developer tasks.
# Capture developer tasks in TFS as task work items as follows:
## In Team Explorer, under your project node, right-click the Work Items folder, point to **Add Work Item**, and then click **Task**.
## On the New Task page, add the following details:
### Set the **Discipline** to **Development**.
### Set** the* Iteration* to the current iteration cycle.
### On the **Links** tab, link the task to the specific scenario for easier traceability. On this tab, along with the description, you can capture the acceptance criteria for the task, which can determine if the task has been successfully completed.
### Set the **Assigned to** field to the developer who will work on the task.
## Save the new task.
## Repeat the above steps for all the identified tasks.
# Repeat the above steps for all the identified scenarios for the iteration.

#### Additional Resources
* For more information about scenarios, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.
* For more information about work items, see “Managing Team Foundation Work Items” at [http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx)  

### Set Acceptance Criteria for Each Task 
Development tasks, when defined, should include acceptance criteria that allow a developer to decide when the task is complete. Depending on the process template you are using, this could be done in two different ways:
* **MSF Agile** – If you are using MSF Agile without a formal work item type requirement, it is best to include acceptance criteria as text in the work item itself. Start with a bulleted list and add more detail as necessary.
* **MSF CMMI** – If you are using MSF CMMI, you can use formal requirements to define acceptance criteria for a task. The first step is to define your requirements. You then create the development task that will be used to implement these requirements and link the task to the requirements so that the developer can check against them, and so that there is traceability from requirements to task. 

The acceptance criteria are most often defined as a user experience requirement in the form of a mini-scenario or a QoS requirement. After the acceptance criteria have been met, the developer can mark the task as complete and move to the next task.

#### Additional Resources
* For more information about work items, see “Managing Team Foundation Work Items” at [http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx)  

### Link Requirements and Tasks to Scenarios
When creating new work items such as tasks, bugs, issues, or QoS requirements, make sure that you link these work items to the scenarios that drove their creation. This helps ensure that each work item is driven by a real user scenario and can be used to better track scenario completion progress during the course of your development iterations.

**To links new tasks, bugs, issues, or QoS work items to scenarios**
# In the **New work item** page, click the **Links** tab, on the Links tab click the **Add** button.
# In the **Add Link** dialog box, under **Link Type**, select **Scenario**.
# Click **Browse** to find the scenarios in your team project.
# In the list, select the scenario to which you want to link and then click **OK**.
# In the **Comment** box, type a comment that explains how the work item is related. The **Description** box is filled in automatically.
# Click **OK**.

#### Additional Resources
* For more information, see “How To – Manage Projects in Visual Studio Team Foundation Server” in this guide.
* For more information about work items, see “Managing Team Foundation Work Items” at [http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181314(VS.80).aspx)   

### Use Microsoft Excel for Bulk Editing of Work Items
Team Foundation Server does not support bulk editing of work items. Instead, you must edit each work item individually. If you need to modify a large number of work items in a short period of time—for example, during a triage meeting—consider using Microsoft Office Excel® to ease the task. Work items can be exported from TFS to Excel, modified, and then imported back into TFS to retain any edits that you made.

**To create a work item list in Excel and edit it**
# In Microsoft Office Excel, on the **Team** menu, click **New List**.
# Under **Connect to a Team Foundation Server**, select the server to connect to, or click **Servers** to enter the server information.
# Under **Team Projects**, select the team project on the Team Foundation Server with which you want to work. The document will be bound to this team project.
# Click **OK**.
# Select the type of list you want. To create a query list, select the **Query List** option and then select a team query from the **Select a Query** drop-down list.
# Select the columns you want to appear in the new work item list.
# Import the desired work items. For more information, see How to: Import Work Items in Microsoft Excel or Microsoft Project at http://msdn2.microsoft.com/en-us/library/ms181676(VS.80).aspx   
# You can now edit the work items and then publish the updated work items to the work item database by clicking **Publish Changes** on the **Team** menu.

#### Additional Resources
* For more information about using Microsoft Office Excel for project-management tasks, see “Working with Work Item Lists in Microsoft Excel” at [http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx)

## Team Foundation Project Management Resources
* For more information about MSF process templates, see “Process Templates” at [http://msdn2.microsoft.com/en-us/teamsystem/aa718801.aspx](http://msdn2.microsoft.com/en-us/teamsystem/aa718801.aspx)