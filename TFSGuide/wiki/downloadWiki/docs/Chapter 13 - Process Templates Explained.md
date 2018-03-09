### Chapter 13 – Process Templates Explained
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Understand the purpose, content and structure of process templates.
* Learn the key differences between the Microsoft® Solution Framework (MSF) for Agile Software Development (MSF Agile) and MSF for CMMI® Process Improvements (MSF CMMI) process templates.
* Customize process templates to meet your team’s specific needs.

### Overview
This chapter explains the role of process templates in Microsoft Visual Studio® 2005 Team Foundation Server (TFS). It identifies the main features and main differences between the two supplied process templates: MSF Agile and MSF CMMI.

Software-development processes are complex, involving many levels of interdependent activities. These processes are generally available to development team in the form of documentation but are usually not enforced by tools. This lack of tool support makes it difficult for development teams to learn and follow the processes consistently. Project managers might use a variety of different tools for project management, requirement management, bug tracking, or review management and they are often not well integrated. This lack of integration makes it more difficult to enforce a consistent methodology across multiple projects and to generate consistent reports to drive common team understanding of project progress and health. This lack of consistency can server to make process analysis unreliable, which makes it more difficult to identify and implement process improvements over time. 

Visual Studio Team System (VSTS) and TFS provide an integrated environment that supports most of the process activities involved in a software-development project. TFS implements its life-cycle methodologies through the use of process templates. A process template is a set of Extensible Markup Language (XML) files that provides specifications for processes and artifacts that make up a development methodology. This chapter explains the architecture of a process template and its components to give you a better understanding of how to utilize and customize the supplied process templates.

If existing process templates are not a good match for your team’s development process you can create a new process template, modify the existing templates, or choose from process templates offered by Microsoft Partners. To review process templates offered by Microsoft Partners, see: [http://msdn2.microsoft.com/en-us/teamsystem/aa718801](http://msdn2.microsoft.com/en-us/teamsystem/aa718801) 

### How to Use This Chapter
Use this chapter to understand process template architecture, structure, and customization. To gain the greatest benefits from this chapter, you should:
* **Read the “MSF Agile and MSF CMMI Process Templates” section**. To learn about the default process templates and how to choose the template that best fits your team’s needs.
* **Read the “Customizing Process Guidance” section**. To learn how to customize the existing process templates to better suit your team’s needs.

### MSF Agile and MSF CMMI Process Templates
Team Foundation Server comes with two process templates: MSF Agile and MSF CMMI. These two process templates are aimed at two different styles of software development. You should use MSF Agile if you are employing an agile methodology to build your software. MSF Agile encourages test-driven development and other agile practices. You should use MSF CMMI if you are following the Software Engineering Institute (SEI) Capability Maturity Model® Integration methodology. This is a formal process aimed at improving existing development processes.

The templates differ in what they provide. For example, they create different types of default reports and work item types. These templates can easily be edited to suit your project’s needs.

### Customizing Process Guidance
The project you are creating may not fit the process templates provided with VSTS. You might need a different work item type or you are using an entirely different process methodology. For example, if you are using SCRUM there is no mention of sprints in the current process template. In this case you need to amend or replace the existing process template to fit the methodology your team uses.

#### Process Template Architecture 
There are three key pieces to the process template architecture:
* **Process template plug-ins**
* **XML process definition files**
* **New Team Project Wizard**

##### Process Template Plug-ins
Process template plug-ins are components that run when a new team project is created. A plug-in sets up required files and configures data for a specific area of the template. The following plug-ins are available out-of-box with TFS. 

* **Classification** – Defines a team project’s initial iteration and areas.
* **Groups and Permissions** – Defines a team project’s initial security groups and their permissions.
* **Windows SharePoint Services** – Defines the project portal for the team based on a Microsoft Windows SharePoint® site template. It also defines template files and process guidance.
* **Work Item Tracking** – Defines a team project's initial work item types, queries, and work item instances.
* **Reports** – Defines a team project's initial reports and sets up the report site.
* **Version Control** –Defines a team project's initial version control security permissions, and check-in notes. 
 
You can modify each plug-in definition file to customize a process template. Except for the classification plug-in, you can also delete plug-in definition files to customize a process template.

##### XML Process Definition Files
The _XML process definition_ files are a set of XML files that define a set of tasks that must run in order to correctly configure a new team project for the process. When you use the **New Team Project** Wizard to create a team project, it runs the required plug-ins. Each plug-in reads its corresponding XML process definition file to obtain the list of tasks it must run. By using the XML process definition files, you specify what configurations and settings the plug-ins must implement. The following are the details about the XML files:
* **Work Item Tracking XML** – This process definition file is named Workitems.xml and is located in the Work Item Tracking folder in the process template folder hierarchy. There are three key types of tasks to specify: work item types, work item queries, and work item instances.
	* **Work Item Types** – Defines the rules, fields, states, and transitions for an item of work that will be tracked on a team project such as tasks, bugs, and requirements.
	* **Work Item Queries** – Used to find specific groupings of work items, such as tasks or active bugs. Work item queries are specified in work item query (WIQ) files in the Queries folder under the Work Item Tracking**** folder in the process template folder hierarchy.
	* **Work Item Instances** – The initial set of work item instances that are created by default when you create the team project.
* **Classification XML** – This process definition file is named Classification.xml and is located in the Classification folder in the process template folder hierarchy. It consists of two parts: Iterations and Areas.
	* **Iterations** – Used to define how many times the team will repeat a particular set of major activities (such as plan, develop, test). Iterations affect work item queries and reports because iterations are used to group work items.
	* **Areas** – Used to organize work in the team project. For example, a team could organize the work based on product or feature, such as UI area, Application area, and Database area. Areas are used to group work items for queries and reports.
* **Windows SharePoint Services XML** – This process definition file is named WssTasks.xml and is located in the Windows SharePoint Services folder in the process template folder hierarchy. There are three key tasks to specify: Site Template (which site template to use), Document Libraries (which document libraries to create), and Folders and Files (which folders and files to copy into the document libraries).
	* **Site Template** – You must specify a site template on which the project portal is based on. This site template also must be available on the TFS SharePoint Portal. Site templates are not included in the process template. 
	* **Document Libraries** – After the project portal is created, you can specify that additional document libraries be created.
	* **Folders and Files** – After the project portal is created, you can specify additional folders to create. You can also specify files to copy such as template files. 
* **Version Control XML** – This process definition file is named VersionControl.xml and is located in the Version Control folder in the process template folder hierarchy. It defines a team project’s initial version control security permissions, check-in notes, and whether exclusive check-out is required.
	* **Check-in Notes** – Specify whether to include check-in notes or not. Check-in notes are provided by the developer when code is checked in to describe how, or if, the code changes are related to team processes. For example, a check-in note can indicate if the change was part of a security review, and can include details about the changes relative to the security review.
	* **Exclusive Check-out** – Used to control whether multiple users can check out a file at the same time.
	* **Permissions –** Defines what actions security groups and individuals can perform on items under version control.
* **Reports XML** – This process definition file is named ReportsTasks.xml and is located in the Reports folder in the process template folder hierarchy. It defines the team project's initial reports.
	* **Reports Site** – The reporting site has a link to it, labeled Reports, on the project portal home page.
	* **Folders** – You can create folders on the reporting site. The folder(s) you create will appear on the project site and under the Reports folder in Team Explorer.
	* **Reports** – Used to add reports by using the .rdl files
* **Groups and Permissions XML** – This process definition file is named GroupsandPermissions.xml and is located in the Groups and Permissions folder in the process template folder hierarchy. It is used to define the team project’s initial security groups.
	* **Groups** – Used to specify a new TFS security group.
	* **Permissions** – Used to define permissions for each group you specify. 

##### New Team Project Wizard
You use the **New Team Project** Wizard to create new team projects. The wizard uses the plug-ins and the XML process definition files to create the project. 

#### Customization Approach
To customize a process template, perform the following steps:
# Review the process templates provided by TFS and choose the one that most closely matches your organizational process.
# Download the chosen process template.
# Customize various components of the process template.
# Upload the customized template to TFS.
# Verify that the changes suit your process requirements. 

This core approach is used as part of the following solutions for customizing the process templates:
* **Manually customize the XML files**.  Manual customization is error-prone but nevertheless gives fine grained control over the customization of process templates. For more information, see “Customizing Process Templates” at [http://msdn2.microsoft.com/en-us/library/ms243782(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms243782(VS.80).aspx) 
* **Process Template Editor Tool available with Power tools**. The latest version the Visual Studio 2005 Team Foundation Server Power Tool ? a set of enhancements, tools, and command-line utilities that improve the TFS experience ? provides a graphical tool for viewing and customizing process templates. When connected to TFS, you can use this tool to customize work item type definitions and global lists on an active project. For more information, see “How To: Customize a Process Template in Visual Studio Team Foundation Server”

#### Common Customizations
The following are descriptions of the set of the components that you generally will customize to create your own custom process:
* **Groups and Permissions**. The out-of-box process templates have a set of groups with various permissions assigned to them. If the default groups and permissions associated with these templates are not adequate or appropriate for your process requirements, you can update those groups or create new groups. You can also add individual users to a group, remove users from a group, or grant and revoke permissions for a group.
* **Source Control Check-In Notes and Policies**. The out-of-box process templates have a set of Source Control Check-In notes and Policies. If the default check-in notes are not adequate or appropriate for your process requirements, you can add or remove check-in note fields, or make some fields required and others not. If the default check-in policies are not adequate or appropriate, you can add, update, or delete individual check-in policies. 
* **Areas and Iterations**.  The out-of-box process templates do not provide a classification structure for either areas or iterations. You can customize the areas and iterations according to your specific process requirements. The recommended approach is to carve out the areas based on the component or features of the project. Iterations can be time-based cycles for which you will repeat particular set of major activities (such as plan, develop, and test).
* **Team Portal**. The out-of-box process templates provide a default team portal, which can be the central hub for communication among team members and others in the organization. You can modify the team portal to change its appearance, behavior, and content to suit your process requirements. 
* **Process Guidance**. The out-of-box process templates provide relevant process guidance that explains the roles, forms, reports, and workflow used in the team project. When customizing the process template to meet your requirement, you must edit the process guidance to reflect the changes for various components. 
* **Reports**. The out-of-box process templates provide a set of default reports. If the default reports are not appropriate or adequate, you can create your own custom reports based on your requirements.
* **Work Item Types and Queries**. The out-of-box process templates have a set of Work item types, default work item instances and queries. If the default Work item types, work item instances and queries are not adequate or appropriate for your process requirements, you can customize work item types to fit your workflow or different types of work items that you want to track. For example, you can:

	* Add new work item types.
	* Remove existing work item types.
	* Add default work item type instances.
	* Remove default work item type instances.
	* Create your own public or private queries.

You can also modify an existing work item type; for example:
	* Add fields.
	* Rename fields.
	* Restrict the list of allowed values for fields.
	* Change the states and supported state transitions.
	* Make fields required or read-only.
	* Make one field dependent on another.
	* Automatically populate field values.
	* Rearrange the appearance of information on the form.
	* Change the Microsoft Office Project column to which a certain field is mapped.

### How Does the Customization Process Work?
Customizing a process template involves the following steps:
# The user launches the **New Team Project** Wizard.
# The wizard asks for:
	* The name of the team project.
	* The process template to be used when creating the team project.

The screens displayed in the wizard are determined by the plug-ins used. For example, if a process template does not include the Windows SharePoint Services plug-in, there is no screen presented to ask information about the project portal.
# After the user provides the information the wizard requests and clicks **Finish**, the wizard makes calls to the plug-ins to perform the work of creating the team project. The order in which the plug-ins are called is determined by the XML process definition files.
# The wizard reads the instructions contained in the process template and then creates and configures the specified items.
The user does not need to specify any details about the various types of work items to be created because the instructions are already provided by the process template.

**Note:** If the wizard encounters a problem while creating the new team project, you will see an error message describing the problem and suggesting corrective action.

### Summary
Use MSF Agile process template if you are employing an agile methodology to build your software. Use the MSF CMMI if you are following the Software Engineering Institute (SEI) Capability Maturity Model Integration methodology. 

The key components of the process template architecture are process template plug-ins, XML process definition files, and the **New Team Project** wizard.

If the default process templates do not satisfy your process requirements, you can customize the template by manually customizing the XML process definition files, or you can use the Process Editor Tool to customize the process templates.

The most common areas of customization are groups and permissions, source control check-in notes and policy, areas and iteration, reports, and work item type definitions.

### Additional Resources
* For information about choosing a process template, see “Choosing a Process Template” at [http://msdn2.microsoft.com/en-us/library/ms400752(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400752(vs.80).aspx) 
* To download the MSF CMMI process template, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=12A8D806-BB98-4EB4-BF6B-FB5B266171EB&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=12A8D806-BB98-4EB4-BF6B-FB5B266171EB&displaylang=en) 
* To download the MSF Agile process template, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=EA75784E-3A3F-48FB-824E-828BF593C34D&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=EA75784E-3A3F-48FB-824E-828BF593C34D&displaylang=en) 
* For more information about process template customization, see “Process Template Customization Overview” at [http://msdn2.microsoft.com/en-us/library/ms194945(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194945(VS.80).aspx) 
* To download the Team Foundation Server Power Tools including the Process Template Editor, go to [http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx](http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx) 
* To review process templates offered by Microsoft Partners, see [http://msdn2.microsoft.com/en-us/teamsystem/aa718801](http://msdn2.microsoft.com/en-us/teamsystem/aa718801)