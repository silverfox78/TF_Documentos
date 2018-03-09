## Practices at a Glance:  Reporting
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Administration
* _How to set up a report dashboard_
* _How to set permissions on reports_

### Creation / Customization
* _How to customize an existing report_
* _How to create a new report in Visual Studio_
* _How to create a new report in Excel_
* _How to create a scheduled report snapshot_
* _How to create a report subscription_
* _How to add a new report to an existing process template_

### Viewing 
* _How to analyze the status of a project_
* _How to analyze application quality_
* _How to review remaining work_
* _How to review build status_
* _How to review bugs and test results_
* _How to review scheduled work versus actual work on an iteration_
* _How to determine the owner of the last edit on a file_
* _How to discover all the code changes made by a developer_
* _How to discover all the code changes made to a file_
* _How to discover all the code changes associated with a specific work item_ 
* _How to generate code churn metrics_
* _How to generate workspace metrics such as number of files, lines of code, and number of projects_ 

## Administration
* **How to set up a report dashboard**
* **How to set permissions on reports**

### How to Set Up a Report Dashboard
Modify the team project Microsoft® Office SharePoint® portal site in order to create a report dashboard that enables you to display a variety of project information in one location.

For example, a useful reporting dashboard could contain the following reports:
* Remaining Work
* Quality Indicators
* Bug Rates
* Project Velocity

You can add new reports to your SharePoint portal page by adding a Report Viewer Web Part for each report you want displayed on the page.

**To modify the team project portal and create a reporting dashboard**
# Install the Report Viewer Web Part on your report server by using the stsadm.exe tool and RSWebParts.cab, both of which are included with SharePoint and the Report Services installation package. 
## STSADM.EXE can be found in the following path: C:\Program Files\Common Files\Microsoft Shared\web server extensions\60\BIN
## RSWebParts.Cab can be found in the following path: C:\ Program Files\Microsoft SQL Server\90\Tools\Reporting Services\SharePoint 
## Example: STSADM.EXE -o addwppack -filename "C:\ Program Files\Microsoft SQL Server\90\Tools\Reporting Services\SharePoint\RSWebParts.cab" -globalinstall
# In Team Explorer, right-click your project.
# Click **Show Project Portal**.
# Click **Modify Shared Page**.
# Point to **Browse** and click **Add Web Parts**.
# Click **Virtual Server Gallery**.
# In the **Web Part List**, select **Report Viewer**.
# Click **Add**.
# Enter the Report Manager name, such as http://<_report server_>/reports.
# Enter the path for the report you want to display, such as <_my project_>/Quality Indicators.

#### Additional Resources
* For more information about adding a Report Viewer Web Part, see “Viewing Reports with SharePoint 2.0 Web Parts” at [http://msdn2.microsoft.com/en-us/library/ms159772(SQL.90).aspx](http://msdn2.microsoft.com/en-us/library/ms159772(SQL.90).aspx) 
* For more information about the team project portal, see “Using the Team Project Portal” at [http://msdn2.microsoft.com/en-us/library/ms242883(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242883(VS.80).aspx)

### How to Set Permissions on Reports
You can modify report permissions to define who can edit or view reports. You must be a member of the Microsoft SQL Server™ Reporting Services Content Manager role in order to be able to set report permissions.

**To set permissions for all reports in your team project**
# In Team Explorer, expand you team project node.
# Right-click **Reports** and then click **Show Report Site**.
# Click the **Properties** tab.
# Click **Security**.
# Click **Edit Item Security**.
# If you want to edit security on a role that is already defined for the report, click **Edit**.
# If you want to define security for a role that is not listed, click **New Role Assignment**.

**To set permissions on a single report**
# In Team Explorer, expand you team project node.
# Right-click **Reports** and then click **Show Report Site**.
# On the report site, select the report for which you want to set permissions.
# Click the **Properties** tab.
# Click **Security**.
# Click **Edit Item Security**.
# If you want to edit security on a role that is already defined for the report, click **Edit**.
# If you want to define security for a role that is not listed, click **New Role Assignment**.

#### Additional Resources
* For more information about setting report permissions, see “How to: Set Permissions for a Report” at [http://msdn2.microsoft.com/en-us/library/ms181645(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181645(VS.80).aspx) 

## Creation / Customization
* **How to customize an existing report**
* **How to create a new report in Visual Studio**
* **How to create a new report in Excel**
* **How to create a scheduled report snapshot**
* **How to create a report subscription**
* **How to add a new report to an existing process template**

### How to Customize an Existing Report
You can modify reports by using the SQL Server 2005 Reporting Services Designer inside Visual Studio (Business Intelligence Development Studio), which ships with the SQL Server 2005 client tools. Modifying an existing report is often easier than creating a new report.

**To customize an existing report in TFS**
# Create a reporting project as follows:
## In Visual Studio, click **File**, click **New**, and then click **Project**.
## Select the **Business Intelligence Project** type.
## Select the **Report Server Project** template.
## Set your project’s **Name** and **Location** and then click **OK**.
# Export the report you want to customize as follows:
## Right-click your team project and then click **Show Project Portal**.
## In the Quick Launch bar on the left side of the portal Web site, click **Reports**.
## Click the report you want to customize.
## Click **Properties**.
## Select **Edit**.
## Save the report .rdl file into the reporting project folder you created in step 1.
# Add data sources as follows:
## To create the warehouse data source:
### In the Visual Studio Solution Explorer, right-click **Shared Data Sources** and then click **Add New Data Source**.
### On the **General** tab, in the **Name** text box, type **TfsReportDS** 
### In the **Type** combo box, select **Microsoft SQL Server**.
### Click **Edit**.
### Fill in your data tier server name. 
### Select the **TFSWarehouse** database. 
### Click the **OK** button twice to add the data source.
## To create the OLAP data source:
### In Solution Explorer, right-click **Shared Data Sources** and then click **Add New Data Source**.
### On the **General** tab, in the **Name** text box, type **TfsOlapReportDS**
### In the **Type** combo box, select **Microsoft SQL Server Analysis Services**.
### Click **Edit**.
### Fill in your data tier server name. 
### Select the **TFSWarehouse** database. 
### Click the **OK** button twice to add the data source.
# Add the report to your project as follows:
## In Solution Explorer, right-click **Reports** and then click **Add->Existing Item**.
## Browse to the rdl file you exported in step 2.
# Modify the report as follows:
## Modify query statements in the Data Pane.
## Drag new measures or members into the Data Pane.
## Modify the report layout in the Layout Pane.

**Note:** Although you can use the Report Builder that is available from the team reporting site, this tool is not well supported for Visual Studio reporting scenarios and therefore is not recommended. 

#### Additional Resources
* For more information, see “How To – Customize a Report in Visual Studio Team Foundation Server” in this guide.

### How to Create a New Report in Visual Studio
You can create reports by using the SQL Server 2005 Reporting Services Designer inside Visual Studio (Business Intelligence Development Studio), which ships with the SQL Server 2005 client tools. 

Create a new report if there are no existing reports that can be modified to meet your needs. Modifying an existing report is often easier than creating a new report.

**To create a new report in TFS**
# Create a reporting project as follows:
## In Visual Studio, click **File**, click **New**, and then click **Project**.
## Select the **Business Intelligence Project** type.
## Select the **Report Server Project** template.
## Set your project’s **Name** and **Location** and then click **OK**.
# Add data sources as follows:
## To create the warehouse data source:
### In Visual Studio Solution Explorer, right-click **Shared Data Sources** and then click **Add New Data Source**.
### On the **General** tab, in the **Name** text box, type **TfsReportDS** 
### In the **Type** combo box, select **Microsoft SQL Server**.
### Click **Edit**.
### Fill in your data tier server name. 
### Select the **TFSWarehouse** database. 
### Click the **OK** button twice to add the data source.
## To create the Online Analytical Processing (OLAP) data source:
### In Solution Explorer, right-click **Shared Data Sources** and then click **Add New Data Source**.
### On the **General** tab, in the **Name** text box, type **TfsOlapReportDS** 
### In the **Type** combo box, select **Microsoft SQL Server Analysis Services**.
### Click **Edit**.
### Fill in your data tier server name. 
### Select the **TFSWarehouse** database. 
### Click the **OK** button twice to add the data source.
# Create a new report as follows:
## In Solution Explorer, right-click **Reports**, point to **Add**,**** and then click** New Item**.
## Select the **Report** template.
## Name the report and then click **OK**.
# Modify the report as follows:
## If the Report Designer does not open automatically, open the report for modification by double-clicking it in Solution Explorer.
## In the **Dataset** drop-down list, select **<New Dataset...>**.
## Name the dataset; for example TestDataSet.
## Select **TFSOlapReportDS (shared)**.
## Click **OK**.
## Click the ellipsis (...**)** button next to **Build** (just below the **Dataset** drop-down list), and then select **Team System**.

You can now modify your report by dragging measures and dimensions from the **Dataset** tree into the Query Pane and Filter Pane.**** You can modify the report’s layout by clicking the **Layout** tab. You can preview your report by clicking the **Preview** tab.

**Note:** Although you**** can use the Report Builder that is available from the team reporting site, this tool is not well supported for Visual Studio reporting scenarios and therefore is not recommended. 

#### Additional Resources
* For more information, see “How To – Create a Custom Report for Visual Studio Team Foundation Server” in this guide.

### How to Create a New Report in Excel
You can create ad-hoc reports by connecting Microsoft Office Excel® directly to the TFS Reporting OLAP cube. By using Excel, you can display report data in the form of pivot tables or pivot charts.

**To create an Excel pivot table report**
# Ensure that you have the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB Provider installed. You can install it from [http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc](http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc) 
# Start Excel.
# Select the worksheet to which you want to add the pivot table report.
# On the **Data** menu, select **PivotTable** **and** **PivotChart Report**.
# Select **External Data Source**.
# Click **Next**.
# Click **Get Data**.
# Click the **OLAP Cubes** tab.
# Select **<New Data Source>** and then click **OK**.
# Enter a name for the data source.
# Select the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB provider.
# Click **Connect**.
# Select **Analysis Server**.
# Enter the name of your reporting server; for example, TFSRTM.
# Click **Next**.
# Select **TFSWarehouse** and then click **Finish**.
# Select the cube from which you want to build a report (e.g., Code Churn, Work Items, and Test Result) and then click **OK**.
# Click **OK** again to return to the Pivot Table and Pivot Chart Wizard.
# Click **Finish** to add the pivot table to the worksheet.

Use the **PivotTable Field List** to drag and drop columns and measures into the pivot table. For example, to see a line count for each Team Project on your server:
# Choose the **Code Churn** cube in step 17 above.
# Drag **TeamProject.TeamProject** into the **Column Fields** section of the pivot table. 
# Drag **Total Lines** into the **Data Items** section of the pivot table. 

#### Additional Resources
* For more information about using Excel to create ad-hoc reports, see “Using Microsoft Excel for Team Foundation Server Reporting” at [http://msdn2.microsoft.com/en-us/library/ms244713(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244713(VS.80).aspx) 
* Install the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB Provider from [http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc](http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc) 

### How to Create a Scheduled Report Snapshot
You can use scheduled report snapshots to better understand trends over time, or to remember important data points throughout the duration of your project.

**To create a scheduled report snapshot**
# In Team Explorer, right-click **Reports** for your team project, and then click **Show Report Site**.
# Open a report from the report site.
# Click the **Properties** tab.
# Click the **History** link.
# Set up a schedule for when you want the snapshot to run.

After the schedule has been set up, you can find the snapshots on the **History** tab for that report. You can also create manual snapshots on the **History** tab.

### How to Create a Report Subscription
You can use report subscriptions to generate reports and export them to a file share for further use. You can set the subscription to overwrite old reports, or you can build a set of reports over time to view snapshots of project data.

**To create a report subscription**
# In Team Explorer, right-click **Reports** for your team project, and then click **Show Report Site**.
# Open a report from the report site.
# Click the **Subscriptions** tab.
# Click **New Subscription** to create the report subscription.

### How to Add a New Report to an Existing Process Template
You can use the Process Editor tool, available with the latest version of the Team Foundation Server Power Tool, to add new reports to an existing process template. You can download the Team Foundation Server Power Tool from [http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx](http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx). 

**To add new reports**
# Download the process template that most closely meets your requirements as follows: 
## In Visual Studio, click **Team** and then select **Team Foundation Server Settings**.
## Click **Process Template Manager**.
## In the **Process Template Manager** dialog box, select the process template you want to modify, and then click **Download**.
## In the **Download Process Template** dialog box, select the folder location on your local drive, and then click **Save**.
# Open the Process Template in the Process Editor as follows:
## In Visual Studio, click the **Team** menu.
## Click **Process Editor**, and then click **Open Process Template**. 
## In the **Open Process Template fileset** dialog box, navigate to the downloaded process template and then click **Open**. This opens the ProcessTemplate.xml file in Visual Studio.
## Set the **Name** of the methodology to which you are applying customizations.
# In the Process Template Explorer, click **Reports**. 
# On the toolbar, click **Add**.
# In the **Report** dialog box, on the **Report Detail** tab, enter a name for the report. 
# Browse to the .rdl file you want to add in the **File Name** field. Leave the other fields unchanged and do not make any changes to the data on the **Properties** and** Parameters** tabs.
# On the **DataSources** tab, enter the appropriate data sources. The default data**** sources for process templates shipped with TFS are /TfsOlapReportDS and /TfsReportDS.
# Click **OK**.

#### Additional Resources
* You can download the Team Foundation Server Power Tool from [http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx](http://msdn2.microsoft.com/en-us/vstudio/aa718351.aspx) 
* For more information about using the Process Editor tool for customizing work item types, see “How To – Customize a Process Template in Visual Studio Team Foundation Server” in this guide.

## Viewing
* **How to analyze the status of a project**
* **How to analyze application quality**
* **How to review remaining work**
* **How to review build status**
* **How to review bugs and test results**
* **How to review scheduled work versus actual work on an iteration**
* **How to determine the owner of the last edit on a file**
* **How to discover all the code changes made by a developer**
* **How to discover all the code changes made to a file**
* **How to discover all the code changes associated with a specific work item** 
* **How to generate code churn metrics**
* **How to generate workspace metrics such as number of files, lines of code, and number of projects** 

### How to Analyze the Status of a Project
You can use the Velocity report to analyze the status of a project.

**To review application status**
# In Team Explorer, expand your team project node, right-click **Reports**, and then click **Show Report Site**.
# On the report site, select the **Velocity** report. 

This report shows how quickly the team is completing work and indicates rates of change from day to day.

### How to Analyze Application Quality
You can use the Quality Indicators report to analyze application quality.

**To analyze application quality**
# In Team Explorer, expand your team project node, right-click **Reports**, and then select **Show Report Site**.
# On the report site, select the **Quality Indicators** report. 

This report collects test results, bugs, code coverage, and code churn into a single report that you can use to track project health. 

### How to Review Remaining Work
You can use the Remaining Work report to review remaining work.

**To review the remaining work**
# In Team Explorer, expand your team project node, right-click **Reports**, and then select **Show Report Site**.
# On the report site, select the **Remaining Work** report. 

This report shows work that is remaining, resolved, and closed over time. By projecting remaining work trends forward, you can predict the point at which you will be code complete.

### How to Review Build Status
If you are using the Microsoft Solution Framework (MSF) for CMMI® (MS CMMI) process template, you can view the Builds report in order to see BVT results.

**To review build status**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Builds** report.

This report provides a list of available builds and includes build quality and other detailed information. 

### How to Review Bugs and Test Results
You can use the Bugs by Priority report to review bugs. This report shows you the rate of high-priority bugs found versus low-priority bugs.

You can use the Quality Indicators report to view test results, bugs, code coverage, and code churn in a single report.

**To view either the Bugs by Priority or Quality Indicators report**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# Select the **Bugs by Priority** report to review bugs, or select the **Quality Indicators** report to view test results.

### How to Review Scheduled Work versus Actual Work on an Iteration
You can use the Unplanned Work report to review scheduled work versus actual work. This report charts total work versus remaining work and distinguishes planned from unplanned tasks.

**To view the Unplanned Work report**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# In the report site, select the **Unplanned Work** report.

### How to Determine the Owner of the Last Edit on a File
You can use source file history from Source Control Explorer to determine the owner of the last edit on a file.

**To determine who made the last edit on a file**
# In Source Control Explorer, select the file of interest.
# Right-click the file and then click **View History**.
# In the History pane, review change history, including the owner.

#### Additional Resources
* For more information about Source Control Explorer, see “Using Source Control Explorer” at [http://msdn2.microsoft.com/en-us/library/ms181370(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181370(VS.80).aspx)++ 

### How to Discover All the Code Changes Made by a Developer
You can use the **TF History** command to find all the code changes in your project that have been made by a specific developer.

For example, the following command shows you all changes made by the user Mario:

{{ tf history $/ /r  /user:Mario }}

In the preceding example, $/ is used to search the entire repository. You can replace this with $/TeamProjectName to restrict your search to a specific team project.

#### Additional Resources
* For more information about the* TF History* command, see “History Command” at [http://msdn2.microsoft.com/en-us/library/yxtbh4yh(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/yxtbh4yh(VS.80).aspx) 

### How to Discover All the Code Changes Made to a File
You can use source file history from Source Control Explorer to determine the changes made to a file.

**To determine all changes made to a file**
# In Source Control Explorer, select the file of interest.
# Right-click the file and then click **View History**.
# In the History pane, review change history to see all changes that have been applied to this file.

#### Additional Resources
* For more information about Source Control Explorer, see “Using Source Control Explorer” at [http://msdn2.microsoft.com/en-us/library/ms181370(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181370(VS.80).aspx)++ 

### How to Discover All the Code Changes Associated with a Specific Work Item 
If a work item has been associated with a set of code changes at the time of check-in, you can view these changes from the work item **Links** tab.

**To view code changes associated with a work item**
# Open the work item in question.
# Click the **Links** tab. If a changeset is associated with this work item, it will be listed in the Links pane in the work item.
# Double-click the linked changeset to view the files and comments that were checked in.

#### Additional Resources
* For more information about changesets, see “Working with Source Control Changesets” at [http://msdn2.microsoft.com/en-us/library/ms181408(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181408(VS.80).aspx) 

### How to Generate Code Churn Metrics
You can use the Quality Indicators report to view code churn details.

**To view the Quality Indicators report**
# In Team Explorer, expand your team project node.
# Right-click **Reports** and then click **Show Report Site**.
# Select the **Quality Indicators** report.

This report collects test results, bugs, code coverage, and code churn into a single report that you can use to track project health. 

Alternatively, you use Excel to generate a report on code churn. To learn more, see “How to Create a New Report in Excel” in this document.

### How to Generate Workspace Metrics Such as Number of Files, Lines of Code, and Number of Projects 
Create reports on various workspace metrics by connecting Excel directly to the TFS Reporting OLAP cube. By using Excel, you can display report data in the form of pivot tables or pivot charts.

**To create an Excel pivot table report**
# Ensure that you have the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB Provider installed. You can install it from [http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc](http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc) 
# Start Excel.
# Select the worksheet to which you want to add the pivot table report.
# On the **Data** menu, select **PivotTable** **and** **PivotChart Report**.
# Select **External Data Source**.
# Click **Next**.
# Click **Get Data**.
# Click the **OLAP Cubes** tab.
# Select **<New Data Source>** and then click **OK**.
# Enter a name for the data source.
# Select the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB provider.
# Click **Connect**.
# Select **Analysis Server**.
# Enter the name of your reporting server; for example, TFSRTM.
# Click **Next**.
# Select **TFSWarehouse** and then click **Finish**.
# Select the **Code Churn** cube from which to build a report, and then click **OK**.
# Click **OK** again to return to the Pivot Table and Pivot Chart Wizard.
# Click **Finish** to add the pivot table to the worksheet.

You can use the **PivotTable Field List** to drag and drop columns and measures into the pivot table.  

**To view a file count for each team project on your server**
# Drag **TeamProject.TeamProject** into the **Page Fields** section of the pivot table. 
# Drag **File Name.FilePath** into the **Row Fields** section of the pivot table.
# Use the **Team Project** drop-down list in the **Page Fields** section of the pivot table to filter each team project.
Note the number of rows displayed. This will give you your file count.

**To view a line count for each team project on your server**
# Drag **TeamProject.TeamProject** into the **Column Fields** section of the pivot table. 
# Drag **Total Lines** into the **Data Items** section of the pivot table. 

**To view a team project count for your server**
* Drag **TeamProject.TeamProject** into the **Row Fields** section of the pivot table. 
Note the number of rows displayed. This will give you your project count.

#### Additional Resources
* For more information about using Excel to create ad-hoc reports, see “Using Microsoft Excel for Team Foundation Server Reporting” at [http://msdn2.microsoft.com/en-us/library/ms244713(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244713(VS.80).aspx) 
* Install the Microsoft SQL Server 2005 Analysis Services 9.0 OLE DB Provider from [http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc](http://www.microsoft.com/downloads/details.aspx?FamilyID=d09c1d60-a13c-4479-9b91-9e8b9d835cdc) 

## Team Foundation Reporting Resources
* For more information on reporting, see “Team Foundation Server Reporting” at [http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx)