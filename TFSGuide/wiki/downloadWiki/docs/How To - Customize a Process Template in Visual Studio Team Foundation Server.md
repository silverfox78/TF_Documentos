### How To – Customize a Process Template in Visual Studio Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)

### Summary
This How To article walks you through the steps for modifying a process template in order to better suit your team’s needs, and explains the tools that you use to do so. Process templates define the initial process settings for team projects. By customizing a process template, you can define:
* Security for team project access control.
* What templates are available on the Microsoft Office SharePoint® project portal.
* Presence of source code control check-in notes.
* Work item types and queries.
* Reports for monitoring project progress and health.
* Iterations and areas used for project organization. 

Follow the steps in order to walk through the modification of a template, and then test the changes you made.

### Content
* Objective
* Overview
* Summary of Steps
* Step 1 – Install Process Editor
* Step 2 – Choose the Process Template
* Step 3 – Download the Process Template
* Step 4 – Open the Process Template in Process Editor
* Step 5 – Modify Work Item Types
* Step 6 – Modify the Default Work Items
* Step 7 – Modify and Manage Queries
* Step 8 – Modify Areas and Iterations
* Step 9 – Modify Groups and Permissions
* Step 10 – Modify Source Control Settings
* Step 11 – Modify the Project SharePoint Portal
* Step 12 – Modify Reports
* Step 13 – Upload the Modified Process Template
* Additional Resources

### Objectives
* Learn what parts of a process template can be modified.
* Customize a process template by using the Process Editor tool.

### Overview
Visual Studio Team System (VSTS) and Team Foundation Server (TFS) provide an integrated environment that supports most of the process activities involved in a software-development project. TFS implements life-cycle methodologies for team projects by using process templates. A _process template_ is a set of Extensible Markup Language (XML) files that provides specifications for different artifacts and processes of a methodology. By modifying a process template, you can change the default work item types, security settings, source control settings, and reports that are set up when a new team project is created.

You can manually customize the XML files, or you can use the Process Editor tool available with the Team Foundation Server Power Tool. Using the Process Editor tool is the recommended method because it is a user interface (UI)–based tool, which makes customizing a process much easier and less error-prone compared to manual customization of XML files.

To modify a process template, you must first download the template you want to modify and then use the Process Editor to make necessary changes.

### Summary of Steps
* Step 1 – Install Process Editor
* Step 2 – Choose the Process Template
* Step 3 – Download the Process Template
* Step 4 – Open the Process Template in Process Editor
* Step 5 – Modify Work Item Types
* Step 6 – Modify the Default Work Items
* Step 7 – Modify and Manage Queries
* Step 8 – Modify Areas and Iterations
* Step 9 – Modify Groups and Permissions
* Step 10 – Modify Source Control Settings
* Step 11 – Modify the Project SharePoint Portal
* Step 12 – Modify Reports
* Step 13 – Upload the Modified Process Template

### Step 1 – Install Process Editor
In this initial step, you will install the Process Editor tool, which provides a convenient UI–based method of viewing and customizing process templates. The Process Editor is part of the Team Foundation Server Power Tool,** a set of enhancements, tools, and command-line utilities that improve the TFS user experience.

# Install DSL Tools for Visual Studio 2005 before you run the Power Tool installer. This is a prerequisite for the Team System Process Editor. If you do not install DSL Tools, the Power Tool installer installs everything except the Process Editor. The DSL Tools download is available at [http://go.microsoft.com/fwlink/?LinkId=82410](http://go.microsoft.com/fwlink/?LinkId=82410)
# Download the Power Tool from: [http://www.microsoft.com/downloads/details.aspx?familyid=7324c3db-658d-441b-8522-689c557d0a79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324c3db-658d-441b-8522-689c557d0a79&displaylang=en) 
# Run through the default installation, and then verify that the Power Tool has been installed correctly with the Process Editor as follows:
## Click **Start** and then click **Programs**. 
## Click **Microsoft Team Foundation Server Power**.**** 
If the Microsoft Visual Studio Team System Process Editor appears,** this means the Process Editor has been installed correctly. If it does not appear, uninstall the Power Tool and then reinstall it according to the correct sequence as specified in the preceding steps.

### Step 2 – Choose the Process Template
In this step, you choose the out-of-box template that most closely suits your own process. This reduces the number of changes required in order to adapt the template to your own team’s process. TFS provides the following two templates out of the box:
* Microsoft Solution Framework (MSF) for Agile Software Development (MSF Agile)
* MSF for CMMI® Process Improvement (MSF CMMI)

Read the following details about these process templates to help make the correct choice.

#### MSF Agile 
The MSF Agile process template is a lightweight process template for small, agile, or informal software projects on a rapid delivery schedule. This process template is based on scenarios and context-driven actions and is both project-centric and team member (people)–centric. You can use the MSF Agile process template in the following project scenarios:
* Your project does not include a documented process and does not rely on formal processes.
* You do not need to certify your process or prove compliance with process standards.
* Your project is of a short duration. 
* Your project needs quick releases for the purpose of community/user feedback.

#### MSF CMMI 
The MSF CMMI process template is designed for more mature software projects. This process template extends the MSF Agile process template by providing support for auditing, verification, and formal processes. You can use this process template in the following project scenarios:
* Your project involves a documented process, or you want to develop more formal processes.
* Predictability of releases is more important than flexibility.
* Your project is of a long duration.
* You have to certify your process or prove compliance with process standards.

**Note:** You are not confined to the default process templates. If you have installed other process templates from third parties, such as the Scrum process template, you can choose these templates as well.

### Step 3 – Download the Process Template
In this step, you download the chosen process template to be adapted to your customized process.

# In Visual Studio, click **Team** and then select **Team Foundation Server Settings**.
# Click **Process Template Manager**.
# In the **Process Template Manager** dialog box, select the process template you want to modify, and then click **Download**.
# In the **Download Process Template** dialog box, select the folder location on your local drive where you want to save the template, and then click **Save**.

For instance, you can download the MSF CMMI process template to your desktop for use in the next step.

### Step 4 – Open the Process Template in Process Editor
In this step, you load the downloaded process template into the Process Editor in order to modify various settings.

# In Visual Studio, click the **Team** menu.
# Click **Process Editor**, and then click **Open Process Template**. 
# In the **Open Process Template fileset** dialog box, navigate to the downloaded process template, and then click **Open** to**** open the ProcessTemplate.xml file inside Visual Studio.
# Specify the **Name** of the methodology you are customizing.

For instance, you can specify ‘My Template’ as the new process template name.

### Step 5 – Modify Work Item Types
In this step, you add new work items types that are specific to your process, or modify the default work item types.

**To add new work item types**
# In the Process Template Explorer, click **Work Item Tracking**.
# In the right pane, click the **Type Definitions** tab. 
# To create a new work item, click **Add** in the toolbar in the right pane.
# In the **New Work Item Type** dialog box, enter a name for the work item type, or select an existing work item type from the **Copy From** drop-down list. 
The new work item type will be created and will be available in the **Item List** on the **Type Definitions** tab in the right pane.
# On the **File** menu, click **Save** to save your changes.

For example, you can create a new Bug type named ‘My Bug,’ copied from the Bug work item type.

You can now edit the work item type to modify its behavior.

**To edit a work item type**
* If you want to add/remove attributes fields to/from the new work item type or an existing work item type, on the **Type Definitions** tab, right-click the work item type you want to edit, and then click **Open**.
The selected work item type opens in a new Visual Studio window where you can add or remove the attributes you want.

**To add a new field to the work item**
# Click the **Fields** tab, and then click **Add** in the toolbar. 
# In the **Field Definition** dialog box, enter the details as specified below: 
## **Name** – Type the name of the new field.
## **Type –** In the** Data type** the drop-down list, select the data type for this field.
## **RefName –** Enter a unique **Identifier** for the field in TFS. The identifier must have at least one period in the name; for example, Test.Test1.
## **Help Text** – Type the text that you want the user to see when he or she moves the pointer over the name of the field. Generally, this text provides a definition of the field’s purpose.
## **Reportable –** Select the desired option in the **Reportable** drop-down list. This determines whether to make the data in this field available for TFS reports. The following options are available:
### **Dimension** – Use this for fields that have lists of valid values. Work Item Type and State are good examples of dimensions. The Dimension field can be used to filter reports.
### **Detail** – This option is a good choice for unrestricted text fields because it lets you use them in reports. However, any reports that you build using these fields must use the relational database instead of the cube.
### **Measure** – Measures are the numeric values in your reports. Each measure will appear in both the Current Work Item measure group and the Work Item History measure group.
## **Formula –** This drop-down list is shown only if you select **Measure** in the **Reportable** field. Examples of formula options include **sum**, **count**, and **avg**.
# For any new field added to the work item type, you can constrain the values that the user can enter into a field. You can also constrain a field when the work item is in a particular state; and when the work item is making a particular transition. Perform the following steps to add constraints:
## Click the **Rules** tab and then click **New**.
## In the **Select a rule type** dialog box, select a rule type. The most commonly used types are: 
### **AllowedValues –** Use this rule type when you want to set a list of values that can be entered.
### **DefaultValue** – Use this rule type when providing a starting value.
### **Required –** Use this rule type when forcing the user to always supply a value.
### **ValidUser –** Contains the name of a user on a project. - The dialog box that appears allows you to set the rule’s parameters. 
## Click **OK** twice to save the changes.
# After you have added a field to a work item, you need to decide where and how the field needs to displayed. Perform the following steps to add a field to your work item layout:
## On the Work Item Type page, click the **Layout** tab.
## On the **Layout** tab, select the location in the Layout tree where you want the new field to appear. 
## In the left pane, right-click the selected node and then select **New Control**.
## Add an appropriate label and then in the **FieldName** property of the control, use the Ref Name that was added for the field in the above steps.
## Click **Preview Form** to verify that the new control is properly positioned on work item form.

For example, you can add a new Security Impact field to the My Bug work item type you created previously, as follows:

# Click the **Fields** tab, and then click **Add** in the toolbar. 
# In the **Field Definition** dialog box, enter the following information:
## **Name** – Security Impact
## **Type** – String
## **RefName** – MyBug.CustomField.1
## **Help Text** – Enter the security impact of this bug, from 1 – 5 where 1 represents the lowest impact and 5 the highest.
## **Reportable** – Set the value as **Dimension** so that it is possible to create a report that will show which bugs have security impact. 
# Click the **Rules** tab, and then click the **Add** button.
# In the **Select a rule type** dialog box, select the **ALLOWEDVALUES** option and then click **OK**.
# In the **ALLOWEDVALUES** dialog box, click **Add** button five times, each time adding a value from 1 to 5.    
# Click **OK**.
# Click the **Layout** tab.
# Add the new field to the Status group as follows: 
## Under **Group – Status**, right-click the second **Column** node and then click **New Control**.
## Set **FieldName** to **MyBug.CustomField.1**.
## Set **Label** to **S&ecurity Impact**. - The ‘&’ assigns the ampersand character as a hotkey for the field.
## Click **Preview Form** to ensure that the new field is in the right location.

The new field has now been added to the custom work item type.

**To remove a field from a work item**
Many times fields are referenced in queries, reports, etc. Rather than track down and remove all of these references, you can leave the fields in the system but remove them from the work item dialog layout so the user cannot set their values.
* Click the **Fields** tab, and then click **Delete** in the toolbar. 

For example, you can remove one of the fields from the My Bug work item type you created previously, as shown below:

# Click the **Layout** tab to display the form layout for My Bug.
# On the **Layout** tab, in the tree, expand _TabPage_??Details_??Group_??Column_??Group_??Schedule_??Column_, right click** Remaining &work,** and then click **Delete** to remove it from the layout.

You can add the field back into the layout at a future point because the field itself has not been deleted.

**To edit work item type workflow**
After you have created a work item type and finalized the layout, the final step is to edit the work item type workflow. Workflow governs the states and transitions that are allowed throughout the life of a work item. Because you copied the work item from an existing type, the workflow was also copied. You now need to review the work item type workflow and decide how you want to modify it. Perform the following steps to modify the work item workflow:
# Create states and transitions.
## Click the **Workflow** tab to open the Workflow window.
## To create a new state, drag a state from the WITDesigner toolbox into the Workflow window.
## To create a transition between two states, WITDesigner toolbox, click the **Transition Link**, click the starting state, and then click the ending state.
## To indicate the initial state (that is, the state of a newly created work item), click the **Transition Link**, click a blank part of the diagram, and then click the initial state. - This creates a transition that has no source. There should only be one such transition on the diagram; if one already exists, you need to delete it.
## To see a summary of the attributes of each state or transition, click the expand/collapse icon at the top right of the shape. In the list of fields in the summary, “+” marks a field that has a required rule; “-” marks a field that has an empty rule; and “*” marks a field that has other rules.
## To edit the attributes of each state or transition, right-click the state heading, and then click **Open Details** or double-click the heading.

**Note**: If the WITDesigner toolbox is not visible, click **Toolbox** on the Visual Studio **View** menu.

# Edit the rules governing a state as follows:
## Right-click the state heading and then click **Open Details**, or double-click the heading. - This opens the **Workflow State Field Rules** dialog box. Each item in the list refers to a field of the work item type, and represents a set of rules governing that field while the work item is in this state.
## On the **Field Reference** tab, set the **RefName** to indicate the field you want to constrain while the work item is in this state. The drop-down list of available fields that you can set is located on the **Fields** tab of the work item type.
## On the **Rules** tab, click **New** to create a new rule, or click **Open** to edit an existing rule. - The details provided in the dialog box on opening a rule vary depending on the type of rule.
## Click **OK** to complete your changes.

# Edit a transition as follows:
## Right-click the transition heading and then click **Open Details** to open the **Workflow Transition** dialog box. 
### The **Transaction Detail** tab defines the **From** and **To** states of the transition. If this transition marks the initial state in which a new work item of this type is created, the **From** state is empty. These fields correspond to the links on the workflow diagram. The **For** and **Not** fields can contain the name of a user or group who can or cannot make the transition.
### The **Reasons** tab defines the content allowed in the **Reason** field when the transition occurs. There should be at least one reason for every transition. 
### The **Actions** tab defines the state transition actions necessary to automate transitions of work items at various points in their workflow. For example, a TFS version control system needs to support automatic transitions of work items at check-in time.
### The **Fields** tab defines rules constraining fields when the transition occurs.
## Click **OK** to complete your changes.

### Step 6 – Modify the Default Work Items
In this step, you add or remove the default work items that are created at the time of team project creation. These work items give a team working on a new project a head start by assigning default work items that should be completed to get the project up and running.

# In the Process Template Explorer, click **Work Item Tracking**.
# In the right pane, click the **Default Work Items** tab.
# To create a new default work item type, click **Add** in the toolbar in the right pane. 
# In the **Choose Type** dialog box, select a work item type.
# In the dialog box that opens, fill in the appropriate fields.
# Click **OK**.

For example, you can remove the task **Setup: Migration of Source Code** by doing the following:

# In the Process Template Explorer, click **Work Item Tracking**.
# In the right pane, click the **Default Work Items** tab.
# Select **Setup: Migration of Source Code**.
# Click **Remove**.

The default task “Setup: Migration of Source Code” will no longer be created when this process template is used to create a new project.

### Step 7 – Modify and Manage Queries
In this step, you modify, add, or remove the default queries created at the time of team project creation.
 
# In the Process Template Explorer, click **Work Item Tracking**.
# In the right pane, click the **Queries** tab.
# To create a new query, click **Add** in the toolbar in the right pane. 
# In the **Query Reference** dialog box, enter the name of the new query.
# Click **Edit Query Definition**.
# Use the **Fields**, **Sorting**, and **Criteria** tabs in the **Query Edit** dialog box to define your query.
# Click **OK**.

For example, you can create a new query to select all bugs that have the highest security impact by doing the following:

# In the Process Template Explorer, click **Work Item Tracking**.
# In the right pane, click the **Queries** tab. 
# Click **Add**.
# Specify the **Name** as **Bugs with Security Impact**.
# Click **Edit Query Definition**.
# In the **Query Edit** dialog box, click the **Fields** tab, select all the relevant fields you want to display (including **MyBug.CustomField.1**) from the available columns, click the > button, to move them to the Selected Columns pane. If you do not see the custom field you have added, make sure that you have saved the ProcessTemplate.xml file and then try again.
# Click the **Criteria** tab, leave the **And Or** column blank, and then in the **Field** column, select **MyBug.CustomField.1**. In the **Operator** column, select > and then in the **Value** column, type **“1”**. Be sure to add quotes around the value 1 because the field is a string data type. If you had selected integer or some other numeric type when creating the Security Impact field, the quotes would not be necessary.
# Click **OK** twice.

This query ensures that all work items that have “MyBug.CustomField.1” set to a value greater than 1 will be displayed in the output of the query.

**Note:** The Process Editor does not provide comprehensive features for editing queries. It is better to edit and test queries in a running team project in Visual Studio than in a process template. You can then save the queries to files that can be imported into other projects or copied into process templates.

### Step 8 – Modify Areas and Iterations
In this step, you set up the default iterations and areas that are available at the time of team project creation.

# In the Process Template Explorer, click **Areas & Iterations**.
# In the right pane, click the **Areas** or** Iterations** tab.
# Use the toolbar in the right pane to add, remove, or move areas or iterations

For example, you can add a few default areas to organize projects created by using this template as follows:

# In the Process Template Explorer, click **Areas & Iterations**.
# In the right pane, click the **Areas** tab.
# Click the new button.
# In the area name text field, type **UI**
# Select **Area**, because you want the next area to be a child of the root area node.
# Click the new button again.
# In the area name text field, type **Back End**

Any new projects that use your process template will now automatically have a UI and Back End area defined for them.

### Step 9 – Modify Groups and Permissions
In this step, you modify, remove, or add groups and their permissions that are available at the time of team project creation.

# In the Process Template Explorer, click **Groups & Permissions**. 
# To create a new group, click **Add** in the toolbar in the right pane.
# In the **Group** dialog box, enter the name of the new group and a brief description of what the members of the group can do, and then click **OK**.
# In the top section of the right pane, select a group and then assign permissions to that group in the section below. You can select **Allow** or **Deny** or leave the permissions setting as **Unset**. An **Unset** permission is an implicit deny.

### Step 10 – Modify Source Control Settings
In this step, you modify the source control settings for parallel edits and check-in edits.

# In the Process Template Explorer, click **Source Control**.
# In the right pane, click the **Checkout Settings** tab.
# If you want to allow more than one person to edit a file at the same time, select the **Enable Multiple Checkout** check box.
# In the right pane, click the **Checkin Notes** tab. 
# To create a new Checkin Note field, click **Add** in the toolbar in the right pane.
# To edit an existing Checkin Note field, select the field and then click **Open**. 
# In the **Checkin Note** dialog box, make necessary changes.
# Click **OK**.

**Note:** You cannot make any changes on the **Permissions** tab in this version of the Process Editor. 

For example, you can require that all check-ins must have a check-in note by performing the following steps:

# In the Process Template Explorer, click **Source Control**.
# In the right pane, click the **Checkin Notes** tab.
# Double-click each row, and then in the **Checkin Note** dialog box, select the **Required** check box.

All check-ins will now require a note.

### Step 11 – Modify the Project SharePoint Portal
In this step, you modify the project SharePoint portal to display specific documents and process guidance.

# In the Process Template Explorer, click **Portal**. 
# To create a new library, in the middle pane, right-click the **Portal** node and then click **New Document Library**.
# In the **Document Library** dialog box, enter the name and description of the library.
# Click **OK**.
# Right-click a document library and then click **New Folder** to create a new folder.
# In the **Folder Properties** dialog box, enter the name of the new folder.
# Select a folder and then on the toolbar in the right pane, click **Add** to upload a new document.
# In the **File Import** dialog box, browse to the file you want to upload. The **Destination Folder** and **Share Point Folder** fields will be automatically populated. Leave the **Query Id** field unchanged.
# Click **Import**.
# To edit the properties of an existing document in the document library, select the document in the right pane, and then click **Open** on the toolbar. 
# In the **File Edit** dialog box, change the name of the file in the **Name** field. Do not change the other fields.
# Click **OK**. 

### Step 12 – Modify Reports
In this step, you add or remove reports from the set of default reports created at the time of team project creation.

# In the Process Template Explorer, click **Reports**. 
# On the toolbar, click **Add**.
# In the **Report** dialog box, on the **Report Detail** tab, enter a name for the report. 
# Browse to the .rdl file you want to add in the **File Name** field. Do not make any changes to the data on the **Properties** and **Parameters** tabs.
# On the **DataSources** tab, enter the appropriate data sources. The default data sources for process templates shipped in TFS are /TfsOlapReportDS and /TfsReportDS.
# Click **OK**.

For example, you can remove a report from the process template as follows:

# In the Process Template Explorer, click **Reports**. 
# Select the **Load Test Detail** report and then click **Remove**.

The Load Test Detail report will no longer appear for projects created with this process template.

### Step 13 – Upload the Modified Process Template
In this step, you upload the modified process template to TFS so that it will be available when the new team project is created.

# In Visual Studio, click **Save** on the toolbar to save the ProjectTemplate.xml file.
# Click **Team** and then select **Team Foundation Server Settings**.
# Click **Process Template Manager**.
# In the **Process Template Manager** dialog box, click **Upload**.
# Browse to the local folder where the process template was downloaded and modified.
# In the **Upload Process Template** dialog box, click **Upload**. You should see the new process template listed in the **Process Templates:** list.
# Click **Close**. 

The customization process is now complete. The next time you create a new team project, the newly created process will be one of the options available when choosing the process templates.

To test the changes you made during the course of this How To article, first upload the My Test process template you created as follows:

# Make sure that you have saved any process template XML files that are still open.
# In Visual Studio, click **Team** and then select **Team Foundation Server Settings**.
# Click **Process Template Manager**.
# In the **Process Template Manager** dialog box, click **Upload**.
# Browse to your desktop location where you downloaded and modified the My Test process template.
# In the **Upload Process Template** dialog box, click **Upload**. You should see the new process template listed in the **Process Templates:** list.
# Click **Close**. 

Next, create a new project based on this process template as follows:

# Click **File** menu**,** click **New**, and**** then click **Team Project**.
# Specify a name (for example, Test Project) and then click **Next**.
# In the process template drop-down list, select **My Test**.
# Click **Finish**.

Finally, review each area to see the changes you made by performing the following steps:

# To view the new work item type:
## On the **Team** menu, click **Add Work Item**, and then click **My Bug** to create a new work item of the custom type you created.
## View the work item fields in the **Status** group box to see the **Security Impact** field that you added.
## Make sure that the field allows the adding of values only in the range of 1-5, add **5** as the value, and then save the work item.
# To verify that the default work item you removed is no longer in the project:
## In Team Explorer, open your team project.
## Expand the Work Items folder.
## Expand the Team Queries folder.
## Double-click **All Work Items**.
## Review the default tasks to verify that the Setup: Migration of Source Code task does not exist.
# To check the custom query you added:
## In Team Explorer, open your team project.
## Expand the Work Items folder.
## Expand the Team Queries folder.
## Double-click **Bugs with Security Impact**.
## Make sure that the bug you created above is displayed correctly.
# To review the areas you added:
## Select a task from the **All Work Items** query you ran in the previous step.
## Click the **Area** drop-down list to view the two areas (**UI** and **Back End**) that you added to the template.
# To ensure that the report you removed is no longer in the project:
## In Team Explorer, open your team project.
## Expand the Reports folder.
## Scan the list to verify that the **Load Test Detail** report has been removed.

### Additional Resources
* For more information about process template customization, see “Process Template Customization Overview” at [http://msdn2.microsoft.com/en-us/library/ms194945(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194945(VS.80).aspx) 
* To download the Team Foundation Power Tool, including the Process Template Editor, go to [http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx](http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx) 
* For more information about customizing a process template using the Process Editor tool, see “Process Editor User Guide,” available with the Process Editor Tool installation.