### How To: Create a “Risk over Time” Report for Visual Studio Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)
* Microsoft SQL Server™ Reporting Services

### Summary
This How To article walks you through the process of creating a new report that shows how **Risk** work items trend over time. The article then shows you how to publish it to the team reporting portal in TFS.

### Contents
* Objectives
* Overview
* Summary of Steps
* Before You Begin
* Step 1 – Create a New Reporting Project
* Step 2 – Create the Data Sources
* Step 3 – Create a New Report in Your Project
* Step 4 – Modify the Report
* Step 5 – Deploy the Report to your Team Foundation Server
* Step 6 – Test the Report
* Additional Resources

### Objectives
* Create a reporting project in Visual Studio.
* Create a new Risk over Time report in the reporting project.
* Publish the Risk over Time report to the report server.

### Overview
The reports that ship with VSTS are SQL Server Reporting Services reports. You can amend these reports or create your own custom reports by using the SQL Server 2005 Reporting Services Designer inside Visual Studio (Business Intelligence Development Studio[BISD](BISD)), which ships with the SQL Server 2005 client tools. To create a custom report, you create a Report Project in Visual Studio and then create data sources to connect to the TFS relational database and Online Analytical Processing (OLAP) database. This How To article shows how to create a simple report from scratch - the Risk over Time report that identifies number of Risk work items over a given period of time.
### Summary of Steps
* Step 1 – Create a New Reporting Project
* Step 2 – Create the Data Sources
* Step 3 – Create a New Report in Your Project
* Step 4 – Modify the Report
* Step 5 – Deploy the Report to your Team Foundation Server
* Step 6 – Test the Report

### Before You Begin
Before you can customize a report for TFS, you must ensure you have the following prerequisites in place:
* You must have Business Intelligence Development Studio (BIDS) installed on the machine you will be using to customize the report.  To verify whether BIDS is installed, check Visual Studio to see if you have the Business Intelligence Project type option when you create a new project.
* Your user account must be a member of the Microsoft Analysis Server TfsWarehouseDataReaders security role on the data-tier server.
* Your user account must have administrator rights to the TFSWarehouse database on the data tier.
* Your user account must be a member of the SQL Server Reporting Services Publisher role on the application-tier server.
* The project must contain Risk work items so that the report shows some data.

### Step 1 – Create a New Reporting Project
In this initial step, you create a new reporting project so that you can add a new report to the project and then customize the report. Perform the following steps to create a new reporting project in Visual Studio:
# Click **File**, then click **New**, and then click **Project.**
# Select the **Business Intelligence Project** type.
# Select the **Report Server Project** template.
# Set your project’s **Name** and **Location** and then click **OK**.

### Step 2 – Create the Data Sources
In order to edit and publish the customized report you first need to add data sources for the TFS data warehouse and OLAP cube.  Once these data sources are added to the Visual Studio project the report can pull data from the server.

**To create the warehouse data source:**
# In the Visual Studio **Solution Explorer**, right-click **Shared Data Sources** and then click **Add New Data Source**.
# On the **General** tab, in the **Name** text box , enter **TfsReportDS** . 
# Select **Microsoft SQL Server** from the **Type** combo box.
# Click the **Edit…** button.
# Fill in your data tier server name. 
# Select the **TFSWarehouse** database. 
# Click the **OK** button twice to add the data source.

**To create the OLAP data source:**
# In **Solution Explorer**, right-click **Shared Data Sources** and then click **Add New Data Source**.
# On the **General** tab, in the **Name** text box, enter **TfsOlapReportDS** . 
# Select **Microsoft SQL Server Analysis Services** from the **Type** combo box.
# Click the **Edit…** button.
# Fill in your data tier server name. 
# Select the **TFSWarehouse** database. 
# Click the **OK** button twice to add the data source.

### Step 3 – Create a New Report in Your Project
Now that the data sources have been added to your project you can add a new report. Perform the following steps to add a new report to your project and customize it:
# In **Solution Explorer**, right-click **Reports** and then select **Add->New Item...**
# Select the **Report** template.
# Name the report and click **OK**

### Step 4 – Modify the Report
After you have added a report to the project you can modify the report as follows:
# If the **Report Designer** doesn't open automatically, open the report for modification by double clicking it in the **Solution Explorer**.
# Click the **Dataset** drop down and the select **<New Dataset...>.**
# Name the dataset, example TestDataSet.
# Select **TFSOlapReportDS (shared)** and then**** click **OK.**
# Click the **...** button next to **Build** (just below the **Dataset** drop down list) and then select **Team System**.
# In the **Dataset Tree**, expand **Measures.**
# In the **Dataset Tree,** expand **Current Work Item.**
# Drag **Current Work Item Count** into the main query window.
# In the **Dataset Tree,** collapse **Measures.**
# Scroll down to **Team Project** and drag it into the **Dimensions** **Grid.**
# In the **Dimensions Grid,** click the **Filter Expression** cell and select your team project name. This filters the results to just your team project.
# Expand the **Work Item** dimension in the **Dataset Tree.**
# Drag **WorkItem.WorkItemType** from the **Dataset Tree** into the **Dimensions Grid.** You may see **System_WorkItemType** instead of **WorkItem.WorkItemType**, if this is the case it will still work, but it means you should apply SQL Server Service Pack 2.  
# Drag **WorkItem.WorkItemType** from the **Dataset Tree** into the main query window and drop it in front of the **work item count** column. You may see **System_WorkItemType** instead of **WorkItem.WorkItemType**, if this is the case it will still work, but it means you should apply SQL Server Service Pack 2.  
# In the **Dimensions Grid,** click the **Filter Expression** cell and then select the **Risk** type. This filters the results to include only Risk work item types.
# In the **Dataset Tree,** expand the **Date** dimension**.**
# Drag the **Date** dimension value into the main query window; dropping it in front of the **work item type** column.
# Click the **Layout** tab.
# Open the **Toolbox** window.
# Drag the **Chart** item from the **Toolbox** to the layout grid.
# Adjust the size of the chart to fit.
# Right-click on the chart and then select **Chart Type? Line? Smooth** **Line.**
#  Open the **Datasets** **Pane**.
#  Expand your data set, for example, TestDataSet.
#  Highlight the graph so that the **Data**, **Series** and **Category** drop targets appear.
#  Drop **Current_Work_Item_Count** into the **Drop Data Fields Here** drop target box.
#  Drop **Work_Item_Type** into the **Drop Series Fields Here** drop target box.
#  Drop **Date** into the **Drop Category Fields Here** drop target box.
#  Right-click the graph and then select **Properties.**
#  Enter a title for your graph and then click **OK**.
#  Click the **Preview** tab to view what the report will look like.

### Step 5 – Deploy the Report to your Team Foundation Server
After you’ve created the Risk over Time report, you can deploy it to your team project’s reporting portal by performing the following steps:
# In **Solution Explorer,** right-click on the report project and then click **Properties**.
# Ensure that **OverwriteDataSources** is set to **false**.
# Modify **TargetDataSourceFolder** to reflect your team project name; for  example: **TargetDataSourceFolder** = TestProject.
# Modify **TargetReportFolder** to reflect your team project name; for example:** TargetDataSourceFolder** = TestProject.
# Modify **TargetDataSourceFolder** _to http://<data-tier servername>/reportserver_; for example: **TargetDataSourceFolder** = http://tfsrtm/reportserver.
# Click **OK.**
# In **Solution Explorer,** right-click on the .rdl file and then click **Deploy.**
# Observe the **Output Pane** to verify for successful completion.

### Step 6 – Test the report
After you’ve published the report to your team project’s report server you can test it to make sure it was successfully deployed:
# In **Team Explorer** expand your team project node, right-click on **Reports** and then select **Show Report Site.**
# On the report site, select the report you just created.
# Verify that the report looks as you expected.

### Additional Resources
* For more tutorials explaining how to work with reporting projects, see “Reporting Services Tutorials” at [http://msdn2.microsoft.com/en-us/library/ms170246.aspx](http://msdn2.microsoft.com/en-us/library/ms170246.aspx) 
* For the MSDN article on editing reports, see “How to: Edit Reports in Report Designer” at [http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx) 
* For more information on security roles in the data-tier, see “Securing Access Through Analysis Services” at [http://msdn2.microsoft.com/en-us/library/ms174839.aspx](http://msdn2.microsoft.com/en-us/library/ms174839.aspx) 
* For more information on security roles in the application-tier, see “Securing Reporting Services” at [http://msdn2.microsoft.com/en-us/library/ms157198.aspx](http://msdn2.microsoft.com/en-us/library/ms157198.aspx)