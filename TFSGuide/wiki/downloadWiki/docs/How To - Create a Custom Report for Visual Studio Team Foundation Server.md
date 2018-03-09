### How To:  Create a Custom Report for Visual Studio Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System
* Microsoft SQL Server™ Reporting Services

### Summary
This How To article walks you through the process of creating a new custom report and then publishing it to the team reporting portal in Team Foundation Server.

### Contents
* Objectives
* Overview
* Summary of Steps
* Before You Begin
* Step 1 – Create a new Reporting Project
* Step 2 – Create the data sources
* Step 3 – Create a new report in your project
* Step 4 – Modify the report
* Step 5 – Deploy the report to your Team Foundation Server
* Step 6 – Test the report
* Additional Resources

### Objectives
* Learn how to create a reporting project in Visual Studio
* Learn how to create a new custom report in the reporting project
* Learn how to publish the new report to the report server

### Overview
The reports that ship with VSTS are SQL Server Reporting Services reports. You can amend these reports or create your own custom reports by using the SQL Server 2005 Reporting Services Designer inside Visual Studio (Business Intelligence Development Studio), which ships with the SQL Server 2005 client tools. To create a custom report, you create a reporting project in Visual Studio, and then create data sources to connect to the TFS relational database and Online Analytical Processing (OLAP) database.

### Summary of Steps
* Step 1 – Create a new reporting project
* Step 2 – Create the data sources
* Step 3 – Create a new report in your project
* Step 4 – Modify the report
* Step 5 – Deploy the report to your Team Foundation Server
* Step 6 – Test the report

### Before You Begin
Before you can customize a report for Team Foundation Server, you must ensure you have the following prerequisites in place:
* You must have Business Intelligence Development Studio installed on the machine you will be using to customize the report.  To test if it is installed, check Visual Studio to see if you have Business Intelligence Project type when you create a new project.
* Your user account must be a member of the Microsoft Analysis Server TfsWarehouseDataReaders security role on the data-tier server.
* Your user account must have administrator rights to the TFSWarehouse database on the data tier.
* Your user account must be a member of the SQL Server Reporting Services Publisher role on the application-tier server.

### Step 1 – Create a new reporting project
Create a new reporting project so that you can add a new report to the project and customize it. Perform the following steps to create a new reporting project in Visual Studio:
# In Visual Studio, click **File**, then click **New**, then click **Project.**
# Select the **Business Intelligence Project** type.
# Select the **Report Server Project** template.
# Set your project’s **Name** and **Location** and then click **OK**.

### Step 2 – Create the data sources
In order to edit and publish the customized report, you need to add data sources for the Team Foundation Server data warehouse and OLAP cube.  Once these data sources are added to the Visual Studio project the report can pull data from the server.

**To create the warehouse data source:**
# In the Visual Studio **Solution Explorer**, right click **Shared Data Sources** and then click **Add New Data Source**.
# On the **General** tab, enter **TfsReportDS** into the **Name** text box. 
# Select **Microsoft SQL Server** from the **Type** combo box.
# Click the **Edit…** button.
# Fill in your data tier server name. 
# Select the database **TFSWarehouse** database. 
# Click the **OK** button twice to add the data source.

**To create the OLAP data source:**
# In **Solution Explorer**, right click **Shared Data Sources** and then click **Add New Data Source**.
# On the **General** tab, enter **TfsOlapReportDS** into the **Name** text box. 
# Select **Microsoft SQL Server Analysis Services** from the **Type** combo box.
# Click the **Edit…** button.
# Fill in your data tier server name. 
# Select the database **TFSWarehouse** database. 
# Click the **OK** button twice to add the data source.

### Step 3 – Create a new report in your project
Now that the data sources have been added to your project you can add a new report. Perform the following steps to add a new report to your project and customize it:
# In **Solution Explorer**, right click **Reports** and then click **Add->New Item...**
# Select the **Report** template.
# Name the report and then click **OK**

### Step 4 – Modify the report
After you have added a report to the project, you can modify it as follows:
# If the **Report Designer** doesn't open automatically, open the report for modification by double clicking it in the **Solution Explorer**.
# Click the **Dataset** drop down and then select **<New Dataset...>**
# Name the dataset, for example TestDataSet.
# Select **TFSOlapReportDS (shared).**
# Click **OK.**
# Click the **...** button next to **Build** (just below the **Dataset** drop down list) and then select **Team System**.

You are now set up to modify report by dragging measures and dimensions from the **Dataset** tree into the **Query Pane** and **Filter Pane.** You can modify the report’s layout by clicking the **Layout** tab. You can preview your report by clicking on the **Preview** tab.

### Step 5 – Deploy the report to your Team Foundation Server
After you have modified the report, you can deploy it to your team project’s reporting portal by performing the following steps:
# In Solution Explorer, right click on the report project and then click **Properties**.
# Ensure that **OverwriteDataSources** is set to **false**.
# Modify **TargetDataSourceFolder** to reflect your team project name; for example: **TargetDataSourceFolder** = TestProject.
# Modify **TargetReportFolder** to reflect your team project name; for example:** TargetDataSourceFolder** = TestProject.
# Modify **TargetDataSourceFolder** to _http://<data-tier servername>/reportserver_. For example: **TargetDataSourceFolder** = http://tfsrtm/reportserver.
# Click **OK.**
# In Solution Explorer, right click on the rdl file and then click **Deploy.**
# Watch the **Output Pane** to confirm successful completion.

### Step 6 – Test the report
After you have published the report to your team project’s report server you can test it to make sure it was successfully deployed:

# In **Team Explorer** expand your team project node, right click **Reports** and then click **Show Report Site**
# In the report site, select the report you just created.
# Verify that the report looks the way you expected.

### Additional Resources
* For more tutorials explaining how to work with reporting projects, see “Reporting Services Tutorials” at [http://msdn2.microsoft.com/en-us/library/ms170246.aspx](http://msdn2.microsoft.com/en-us/library/ms170246.aspx) 
* To read the Microsoft MSDN®  article on editing reports, see “How to: Edit Reports in Report Designer” at [http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx) 
* For more information on security roles in the data-tier, see “Securing Access Through Analysis Services” at [http://msdn2.microsoft.com/en-us/library/ms174839.aspx](http://msdn2.microsoft.com/en-us/library/ms174839.aspx) 
* For more information on security roles in the application-tier, see “Securing Reporting Services” at [http://msdn2.microsoft.com/en-us/library/ms157198.aspx](http://msdn2.microsoft.com/en-us/library/ms157198.aspx) 