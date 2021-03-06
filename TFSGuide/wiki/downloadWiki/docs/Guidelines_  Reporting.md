## Guidelines:  Reporting
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index

### Administration
* _Ensure that users are in the correct security groups._
* _Create a report dashboard to view project status and health metrics in one location._

### Creating / Customizing
* _Make sure that the server name is correct when deploying reports._
* _Create scheduled report snapshots that you can view over time._
* _Modify existing reports to gain access to additional data._

### Viewing
* _Ensure that the warehouse Web service has run if you want the latest data._

## Administration
* **Ensure that users are in the correct security groups.**
* **Create a report dashboard to view project status and health metrics in one location.**

### Ensure That Users Are in the Correct Security Groups
If you want a user to be able to deploy reports, make sure that the user is assigned the report server’s Content Manager Role. The Content Manager role is a predefined Report Services role for users who deploy and manage reports and data source connections on the Web server. For a Microsoft® Visual Studio® 2005 Team Foundation Server (TFS) user to be able to deploy reports to the report server, the user must be a member of this role.

**To add a user to the Content Manager role**
# Open the report site for the project. In Team Explorer, right-click the **Reports** entry for your team project and then select **Show Report Site**.
# At the top of the window, click** the* Properties* tab.
# At the left side of the window, click **Security**.
# Click **New Role Assignment**.**** 
# In the **Group or user name:** field, enter the name of the user or group you want to add to the Content Manager role 
# Select the **Content Manager** check box.
# Click **OK**.

#### Additional Resources
* For more information about the Content Manager role, see “Content Manager Role” at [http://technet.microsoft.com/en-us/library/ms159693(SQL.90).aspx](http://technet.microsoft.com/en-us/library/ms159693(SQL.90).aspx)
* For more information about security roles in the data tier, see “Securing Access Through Analysis Services” at [http://msdn2.microsoft.com/en-us/library/ms174839.aspx](http://msdn2.microsoft.com/en-us/library/ms174839.aspx) 
* For more information about security roles in the application tier, see “Securing Reporting Services” at [http://msdn2.microsoft.com/en-us/library/ms157198.aspx](http://msdn2.microsoft.com/en-us/library/ms157198.aspx) 

### Create a Report Dashboard to View Project Status and Health Metrics in One Location
A reporting dashboard allows you and your team to quickly access important project information on a single page. The default Microsoft Office SharePoint® portal page for Microsoft Solution Framework (MSF) for Agile Software Development (MSF Agile) projects contains a single report as well as links to others. To create a single repository for project information, you can modify the portal page for MS Agile or MSF for CMMI® (MS CMMI) projects to include as many reports on the page as you want.

For example, a useful reporting dashboard could contain the following reports:
* Remaining Work
* Quality Indicators
* Bug Rates
* Project Velocity

You can add new reports to your SharePoint portal page by adding a Report Viewer Web Part for each report you want displayed on the page.

**To modify the team project portal and create a reporting dashboard**
# Install the Report Viewer Web Part on your report server using the stsadm.exe tool and RSWebParts.cab, both of which are included with SharePoint and the Report Services installation package. 
## STSADM.EXE can be found in the following path: C:\Program Files\Common Files\Microsoft Shared\web server extensions\60\BIN
## RSWebParts.Cab can be found in the following path: C:\ Program Files\Microsoft SQL Server\90\Tools\Reporting Services\SharePoint 
Example: STSADM.EXE -o addwppack -filename "C:\ Program Files\Microsoft SQL Server\90\Tools\Reporting Services\SharePoint\RSWebParts.cab" -globalinstall
# In Team Explorer, right-click your project.
# Click **Show Project Portal**.
# Click **Modify Shared Page**.
# Point to **Browse** and then click **Add Web Parts**.
# Click **Virtual Server Gallery**.
# In the **Web Part List**, select **Report Viewer**.
# Click **Add**.
# Enter the Report Manager name, such as http://<_report server_>/reports.
# Enter the path for the report you want to display, such as <_my project_>/Quality Indicators.

#### Additional Resources
* For more information about adding a Report Viewer Web Part, see “Viewing Reports with SharePoint 2.0 Web Parts” at [http://msdn2.microsoft.com/en-us/library/ms159772(SQL.90).aspx](http://msdn2.microsoft.com/en-us/library/ms159772(SQL.90).aspx) 
* For more information about the team project portal, see “Using the Team Project Portal” at [http://msdn2.microsoft.com/en-us/library/ms242883(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242883(VS.80).aspx)

## Creating / Customizing
* **Make sure that the server name is correct when deploying reports.**
* **Create scheduled report snapshots that you can view over time.**
* **Modify existing reports to gain access to additional data.**

### Make Sure That the Server Name Is Correct When Deploying Reports 
If either the report server’s Uniform Resource Locator (URL) or Target Folder Name is specified incorrectly, your report cannot be deployed to the report server. When you deploy a report from Visual Studio 2005, specify the URL of the server to which the report should be deployed and the name of the team project of which the report is a part. The URL of the report server to which the report is to be deployed is http://TeamServerName/**ReportServer**, where** ReportServer** is the endpoint of the Report Server Web service.

Specify the team project name in the **TargetReportFolder** field of the deployment properties dialog box. This value is case-sensitive; if you get the case wrong, the report will be deployed but will not appear in the list of reports for your team project in Team Explorer.

#### Additional Resources
* For more information about setting the deployment properties, see “How to: Set Deployment Properties (Report Designer)” at [http://technet.microsoft.com/en-us/library/ms155802(SQL.90).aspx](http://technet.microsoft.com/en-us/library/ms155802(SQL.90).aspx)

### Create Scheduled Report Snapshots That You Can View over Time
Use report history to build snapshots of project data at regular intervals. You can view these snapshots over a specified time period to better understand trends, or to remember important data points throughout the duration of your project.

**To create a scheduled report snapshot**
# Open a report from the report portal.
# Click the **Properties** tab.
# Click the **History** link.
# Set up a schedule for when you want the snapshot to run.

After the schedule has been set up, you can find the snapshots on the **History** tab for that report. You can also create manual snapshots on the **History** tab.

### Modify Existing Reports to Gain Access to Additional Data
Modify reports by using the Microsoft SQL Server™ 2005 Reporting Services Designer inside Visual Studio (Business Intelligence Development Studio), which ships with the SQL Server 2005 client tools. 

Customizing a report enables you to add functionality to an existing report without having to build a new report. If a report you need is similar to one that already exists, customize the existing report to save time. To customize an existing report, you must export it from the report server, add it to an existing report project in Visual Studio, and then redeploy it to the reporting portal after changes are made.

**Note:** Although you can use the Report Builder that is available from the team reporting site, this tool is not well supported for Visual Studio reporting scenarios and therefore is not recommended. 

#### Additional Resources
* For a more detailed How To article, see “How To – Customize a Report in Visual Studio Team Foundation Server” in this guide.
* For more information about reporting, see “Chapter 15 – Reporting Explained” in this guide.
* For more tutorials explaining how to work with reporting projects, see “Reporting Services Tutorials” at [http://msdn2.microsoft.com/en-us/library/ms170246.aspx](http://msdn2.microsoft.com/en-us/library/ms170246.aspx) 
* To read a Microsoft MSDN® article about editing reports, see “How to: Edit Reports in Report Designer” at [http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244655(VS.80).aspx) 

## Viewing
* **Ensure that the warehouse Web service has run if you want the latest data.**

### Ensure That the Warehouse Web Service Has Run if You Want the Latest Data
Manually run the warehouse Web service if you want to ensure that your reports have the latest data. By default, the warehouse Web service runs once every hour to generate the data for your reports. If you are about run a report and want to ensure that your reports contain the latest data, you can run the service manually.

**To run the warehouse service manually**
# Open Internet Information Services (IIS) Manager.
# Select the **Team Foundation Server** Web site.
# Within the Web site, open the Warehouse\v1.0 directory. This displays a page with a list of the operations available on the warehouse.
# Right-click **warehousecontroller.asmx** and then click **Browse**.
# Click **Run** and then click **Invoke**. This opens a second browser window showing the status of the run request. It should show the value **true**.
# Go back to the first browser window and navigate back to the operations page.
# Select **GetwareHouseStatus** and then click **Invoke**. 
This displays the current status of the warehouse Web service. A value of **idle** indicates that the warehouse has run. Other values display the status of service.

#### Additional Resources
* For more information about troubleshooting the warehouse, see “Troubleshooting the Data Warehouse” at [http://msdn2.microsoft.com/en-us/library/ms244674(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms244674(vs.80).aspx)

## Team Foundation Reporting Resources 
* For more information about reporting, see “Team Foundation Server Reporting” at [http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx)