### How To: Manage Projects in Visual Studio Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)

### Summary
This How To article walks you through the process of initiating new software development projects by creating and configuring new team projects based on a selected template and shows you how to use TFS tools to manage, control and monitor the ongoing software development processes throughout the software development lifecycle.

### Contents
* Objective
* Overview
* Summary of Steps
* Before You Begin
* Step 1 – Choose a Process Template
* Step 2 – Create a Team Project
* Step 3 – Create Security Groups (Optional)
* Step 4 – Add Team Members in Team Foundation Server 
* Step 5 – Determine Your Iteration Cycle
* Step 6 – Capture Your Project Scenarios in TFS
* Step 7 – Identify the Scenarios for the Iteration
* Step 8 – Define Your  Quality of Service Requirements
* Step 9 – Plan Your Iteration
* Step 10 – Monitor Progress
* Area and Iteration Consideration
* Additional Resources

### Objective
* Learn how to create team projects in TFS
* Learn how to manage projects in TFS

### Overview
Visual Studio Team System provides tools and reports to help project managers control and support the entire software development life cycle in a unified and centralized manner. By controlling the software process directly through VSTS and a centralized database shared by all team members, team communication is improved, and handoffs required between team members are automated. In addition using reports driven from the TFS data warehouse makes it much easier to monitor and track project progress.

This How To article walks you through the process of managing a team project from the first steps of creating and configuring a new project and then through the steps required to monitor the progress of an ongoing project.

### Summary of Steps
* Step 1 – Choose a Process Template
* Step 2 – Create a Team Project
* Step 3 – Create Security Groups (Optional)
* Step 4 – Add Team Members in Team Foundation Server 
* Step 5 – Determine Your Iteration Cycle
* Step 6 – Capture Your Project Scenarios in TFS
* Step 7 – Identify the Scenarios for the Iteration
* Step 8 – Define Your Quality of Service Requirements
* Step 9 – Plan Your Iteration
* Step 10 – Monitor Progress.

### Before You Begin
Before you start creating a new team project, you should gather the following information:

* **The process you want to use for the project**. The process you want to use to manage your project determines the template you should select when creating a new team project. It also helps you evaluate the degree to which you should customize the supplied templates. If you favor an agile style of project execution, start by selecting the Microsoft Solutions Framework (MSF) for Agile Software Development (MSF Agile) template and then consider any customizations you might need. 
* **The project name**. Give careful consideration to the naming convention that you use for the team projects you create. Make sure that your project names are sufficiently unique and use names that enable other people to easily find the project. Some organizations use project codes as part of their names, while others might use a combination of department and project title.
* **Source control structure**. Consider whether you need to start with an empty source control tree or whether your project should be based on existing source code. Evaluate an appropriate source control structure based on your code and branching needs. For more information, see “How To: Structure Your Source Control Folders in Visual Studio Team Foundation Server.”

### Step 1 – Choose a Process Template
Start by selecting your process template. Consider the process you would like to follow for your project and then examine the different features provided by each of the two templates supplied by TFS (see below). Features to evaluate include work item definitions (do they provide sufficient fields for your needs?), document templates, workflows, check in policies, and reports.

TFS provides following two process templates:

* **MSF for Agile Software Development (MSF Agile)** – This is a lightweight process for small and informal software projects. It is based on scenarios and context-driven actions and is both project-centric and team member (people)-centric.
* **MSF for CMMI® Process Improvement (MSF CMMI)** – This is designed for more mature software projects. It extends MSF Agile by providing support for auditing, verification, and formal processes. It relies on process and conformance to process and is organization-centric. 

If required you can customize the supplied process templates to align them more closely with your processes. For more information about customizing the process templates see “How To: Customize a Process Template in Visual Studio Team Foundation Server”. 

The remainder of this How To article, assumes that you have selected the MSF Agile process** template.

### Step 2 – Create a Team Project
After you have selected the template you want to use, you are ready to create a new team project. To create a new team project:

# Ensure that Visual Studio is connected to a TFS instance.
# In **Team Explorer,** right click the server node and then click **New Team Project…**
# On the first page of the New Project Creation Wizard, enter the name of your team project and then click **Next**.
# On the **Select a Process Template** page, from the drop-down list, select the process template you chose in Step 1. For this example, choose the **MSF for Agile Software Development –v4.0** process template and then click **Next**.
# On the **Specify the Settings for the Project Portal** page, enter the name and description for the team project portal and then click **Next**. The name you supply here is used to build the Microsoft Windows SharePoint® Services Web site for your project portal.
# On the **Specify Source Control Settings** page, select **Create an empty source control folder** and then click **Next**.
# On the **Confirm Team Project Settings** page, review the settings and then click **Finish**.  

This creates a team project on the TFS server based on the MSF Agile process template.

### Step 3 – Create Security Groups (Optional)
When you create a project in TFS, four default groups are created for that project regardless of your choice of process template. By default, each of these groups has a predefined set of permissions that govern what members of those groups are authorized to do. The four groups are:

* Project Administrator
* Contributor
* Reader
* Build Services. 

You can create security groups for your team project to better meet your organization’s security requirements. Creating a security group is an efficient way to grant a specific set of permissions to a group of users on your team project. Make sure that you allow only the minimum permissions necessary for the group, and add only those users or groups who must belong to this new team project group.

To perform this procedure, you must be a member of the **Project Administrators** group although you do not need to be a Microsoft Windows® administrator.

# In Team Explorer, select the team project for which you want to create a group.
# On the **Team** menu, point to **Team Project Settings**, and then click **Group Membership**.
# In the **Project Groups** dialog box, click **New**.
# In the **Create New Team Foundation Server Group** dialog box, in the **Group name** box, type the name for the team project group.
# In the **Description** box, type a description for the group.
# Click **OK** and then **Close**.


After you have created a team project group, give the group the appropriate permissions, and add members to the group. By default, a team project group is created without any permission granted.

### Step 4 – Add Team Members in Team Foundation Server
In this step, you identify the resources that will be working on the project and their roles, and then assign these team members to TFS. You can add users to existing team project groups or server-level groups. You must also add members to groups that you create. To perform this procedure, you must be a member of the **Team Foundation Administrators** group.

# In Team Explorer, select your team project.
# On the **Team** menu, point to **Team Project Settings**, and then click **Group Membership**  -Or- To add users to a server-level group, point to **Team Foundation Server Settings**, and then click **Group Membership**.
# In the **Project Groups** dialog box, select the group to which you want to add users, and then click **Properties**.
# In the **Team Foundation Server Group Properties** dialog box, on the **Members** tab, under **Add member**, select **Windows User or Group**.
# Click **Add**.
# In the **Select Users or Groups** dialog box, under **Enter the object names to select**, enter the domain name and alias of the users you want to add in the following format:

**domain\username** 

To add more than one user at a time, separate the entries with a semicolon (;).
# Click **OK** twice**** and then**** click **Close**. 

### Step 5 – Determine Your Iteration Cycle
_Iterations_ are fixed-length chunks of periods in which you plan, schedule, and perform work. All components of the software development lifecycle - from requirements definition through analysis, design, development, coding, and testing - are grouped into these iterations, which typically last anywhere from 2 to 6 weeks.

In this step you determine the iteration cycle for your project. The important points to keep in mind while determining the iteration cycle are:

* The iteration cycle should be long enough to get substantial work done, and should cover at least a few scenarios 
* The iteration cycle should be short enough to be flexible to accommodate changes and changing priorities.

The length of your iteration cycle will depend upon the size and complexity of your project. In practice, two-week iteration cycle works for most projects.

### Step 6 – Capture Your Project Scenarios in TFS
In this step, you capture your project scenarios in TFS so that you can plan better execution of your project and track its progress.

# Create a project back log (PBL) document from inputs provided by various stake holders, including customers, business analysts, end users and product managers. The PBL is generally a Microsoft Office Word document designed mainly to capture requirements.
# Use the PBL as input and scope out various scenarios for your project.
# You can create all the scenarios at the start of the first iteration or you can create scenarios as you move through iterations. To gain a complete picture of your project and to help track progress, you are recommended that you capture all your scenarios upfront.

**To create a scenario in a project that uses the MSF Agile process template**.
# In **Team Explorer,** expand the project node and then right-click on the **Work Items** folder.
# Point to **Add Work Item** and then click **Scenario.**
# On the **New Scenario** page, enter the details for the Scenario. 
# Save your new scenario. 
# Repeat the preceding steps for all scenarios that you have identified for the project.

### Step 7 – Identify the Scenarios for the Iteration
In this step, you identify the scenarios to be worked on during a specific iteration. You repeat this step for each iteration cycle.

# Identify the scenarios to be worked on during a specific iteration, based on inputs from the project stakeholders and your feature priorities.
# Assign these scenarios to the iteration 

**To retrieve work items and assign them to a specific iteration:**
# Expand the **Work Items** folder, expand the **Team Queries** folder, and then double-click the **All Scenarios** query to display all the scenarios in your project.
# Double-click the scenario you want to work on in the current iteration.
# Change the **Iteration** to the current iteration path and then click the save icon.
# Repeat the preceding steps for all identified scenarios.

### Step 8 – Define Your Quality of Service Requirements
In this step, you define your Quality of Service (QoS) requirements for each of the scenarios to be worked on during the iteration cycle. You repeat this step for each iteration cycle. This helps define the acceptance criteria for the scenario. The inputs for the QoS requirements come from project goals and requirements and specification documentation, if available.

# Right-click on the **Work Items** folder of your project, and point to **Add Work Item,** and then click **Quality of Service Requirements**.
# In the **New Quality of Service Requirements** page, add the following details 
## Set the **Type** to an appropriate value such as Performance, Scalability, Stress or Security. 
## Set the **Iteration** to the current iteration cycle.
## From the **Links** tab, link the QoS to a specific scenario, for easier traceability. 
# Save the new QoS requirement.
# Create one QoS requirements for each discipline or type of quality requirements, bearing in mind that each scenario can have multiple QoS requirements.
# Make sure you create QoS requirements for all of the scenarios in a specific iteration cycle.

**Important** – You can break down the QoS requirements into test tasks later. 

### Step 9 – Plan Your Iteration
In this step you plan for the iteration by breaking down the scenarios, QoS requirements, and other work items into tasks, estimating effort for each task and assigning the tasks to the relevant team members. You repeat this step for each iteration cycle.

#### Developer Tasks
# Break down the chosen scenarios into developer stories
# Subdivide the developer stories into developer tasks.
# Capture developer tasks in TFS as task work items.
## In Team Explorer, under your project node, right-click the **Work Items** folder, point to **Add Work Item** and then click **Task**.
## In the **New Task** page, add the following details
### Set **Discipline** to **Development**.
### Set* Iteration* to the current iteration cycle.
### On the **Links** tab link the task to the specific scenario for easier traceability.
### On the New Task Page, along with the description you can capture the acceptance criteria for the task, which can determine if the task is completed successfully.
### Set the **Assigned to** field to the developer who will be working on the task.
## Save the new task.
## Repeat the above steps for all the identified tasks.
# Repeat the above steps for all the identified scenarios for the iteration.

#### Test Tasks
# Break down the QoS requirements for the identified scenario into test cases.
# Divide the test cases into test tasks, these test tasks are captured in TFS as task work items.
## In Team Explorer, under your project node, right-click the **Work Items** folder, point to **Add Work Item** and then click **Task**.
## In the **New Task** page, add the following details
### Set* Discipline* to **Test**.
### Set* Iteration* to the current iteration cycle.
### On the **Links** tab link the task to the specific QoS requirements for easier traceability.
### On the New Task page, along with the description you can capture the acceptance criteria for the task, which can determine if the task is completed successfully.
### Set the **Assigned to** field to the tester who will be working on the task.
## Save the new task.
## Repeat the above steps for all the identified tasks.
# Repeat the above steps for all the QoS requirements for the iteration

#### Others
# Capture any relevant tasks for the iteration for other disciplines – such as Architecture, Release Management, Project Management and Requirements - which needs to be tracked. 
# Link each of these tasks to the appropriate scenario for easier traceability. 

For large projects that contain a huge number of work items, you can use the Microsoft Office Excel® integration feature to create work items in an Excel spread sheet and then upload it to TFS. For more information see “Working with Work Item Lists in Microsoft Excel” at [http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx) 

For large projects that contain a large number of resources, you can use the integration feature in Microsoft Office Project to track the work items and balance task assignment. For more information see “Working with Work Items in Microsoft Project” at [http://msdn2.microsoft.com/en-us/library/ms244368(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244368(VS.80).aspx) 

### Step 10 – Monitor Progress
Each process template includes a set of reports that you can use to track project status and health.  Below are the default reports that you can use to monitor progress:

#### Bugs
The bug related reports enable you to see the kind of bugs being generated and fixed and to spot trends. The following bug related reports are available:

* **Bugs by Priority**. Are the correct bugs being found? This report shows you the rate of high priority bugs found vs. low priority. This report is both of the supplied process templates.
* **Bug Rates**. How effectively are bugs being found, fixed and closed? This report shows trends over time for new bugs, bug backlogs, and bug resolution. This report is available in both of the supplied process templates.

#### Release Management
Release management reports enable you to judge how close your software is to being fit for release. The following release management reports are available:

* **Actual Quality versus Planned Velocity**. How many scenarios can be completed before quality is unacceptable? This report presents the relationship, for each iteration, of estimated size to overall quality. This report is available in both process templates.
* **Builds**. What is the quality of a build? This report provides a list of available builds including build quality and other detailed information. This report is available in MSF for CMMI Process Improvement.
* **Quality Indicators**. What is the quality of the software? This report collects test results, bugs code coverage and code churn into a single report to track project health. This report is available in MSF Agile and MSF CMMI.
* **Velocity**. How quickly is the team completing work? This report shows how quickly the team is completing planned work and show rates of change from day to day. This report is available in MSF Agile and MSF CMMI.
* **Scenario Details**. What scenarios are we building the application against? This report provides information on each scenario including completion status, risks and testing progress.

#### Testing
Testing reports enable you to monitor the effectiveness and progress of your testing. The following test reports are available:

* **Regressions**. What tests passed at one point but are now failing? This report shows a list of all the tests that passed previously and now are failing. This report is available in MSF CMMI.
* **Requirements Test History**. How well tested are my scenarios and requirements? This report shows the progress of testing against defined scenarios and requirements. This report is available in MSF CMMI.
* **Test Failure Without Active Bug**. Are there bugs to track every known defect? This report shows any tests that have failed and are not associated with an open bug. This report is available in MSF CMMI.
* **Test Passing With Open Bug**. Is the bug list up to date and consistent with application quality? This report shows stale bugs for which tests are now passing. This report is available in MSF CMMI.
* **Load Test Summary**. What are the results of load testing on application performance? This report shows test results for load testing on your application. This report is available in MSF Agile.

#### Work Items
Work item reports enable you to assess the current state of your project and current project progress. The following work item reports are available.

* **Open Issues and Blocked Work Items Trend**. How many open issues remain? This report shows the remaining open issues as well as the trend toward resolving them. This report is available in MSF CMMI.
* **Reactivations**. How many work items are being reactivated? This report shows work items that have been resolved or closed prematurely. This report is available in MSF Agile and MSF CMMI.
* **Related Work Items**. What work items are dependent on other work items? This report shows a list of work items that are linked to other work items so you trace dependencies. This report is available in MSF CMMI.
* **Remaining Work**. How much work is left to be done and when will it be completed? This report shows work remaining, resolved and closed over time.  Projecting remaining work trends forward can enable you to predict the point at which you will be code complete. This report is available in MSF Agile and MSF CMMI.
* **Triage**. What work items need to be triaged? This report shows every work item that is still in the proposed state. This report is available in MSF CMMI.
* **Unplanned Work**. How much unplanned work is there? This report charts total work versus remaining work and distinguishes planned from unplanned. This report is available in MSF Agile and MSF CMMI.
* **Work Items**. What are the active work items? This report lists every active work item. This report is available in MSF CMMI.
* **Work Items by Owner**. How much work is assigned to each member of the team? This report shows work items per team member. This report is available in MSF CMMI.
* **Work Items by State**. How many active, resolved and closed work items are there? This report lists work items organized by state. This report is available in MSF CMMI.
 
### Area and Iteration Consideration
Keep in mind the following key considerations related to areas and iterations

* Areas are used to organize work in your team project; for example, you could organize your project work into areas such as a UI area, an Application area, and a Database area. You can assign scenarios and work items to the specific areas. Areas are used to group work items for queries and reports. You can start with a single root-level area and later as your project matures you can create areas once you need them.

* Iterations are used to define how many times the team will repeat a particular set of major activities (such as planning, development and testing) during the course of application development. Iterations are used to group work items and therefore impact work item creation, work item queries, and reporting. 

### Additional Resources
* For more information on using Microsoft Office Excel spreadsheets with work items, see “Working with Work Item Lists in Microsoft Excel” at [http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181694(VS.80).aspx)
* For more information on using Microsoft Office Project to track work items and balance task assignment, see “Working with Work Items in Microsoft Project” at [http://msdn2.microsoft.com/en-us/library/ms244368(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244368(VS.80).aspx)