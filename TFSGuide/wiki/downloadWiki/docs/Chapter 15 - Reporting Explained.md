### Chapter 15 – Reporting Explained
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Describe Microsoft® Visual Studio® Team Foundation Server (TFS) reporting architecture.
* Identify the components that make up TFS reporting.
* Describe the purpose of each available report.
* Know which process template contains which report.
* Customize and create new reports.

### Overview
This chapter describes TFS reporting architecture and the common reports that you can use with new team projects. It also connects common reporting scenarios with reports available in TFS, and describes common reasons to customize existing reports or create new reports. TFS reporting enables you to view aggregated data over many aspects of your team project. You can use this information to analyze project progress, project health, and the effectiveness of your development and test teams.  

TFS reporting uses Microsoft SQL Server™ 2005 Reporting Services to create, manage, and run reports. Each process template contains a set of predefined reports which are deployed to the project’s report folder when the project is created. By using Reporting Services you can also amend these reports and create custom reports for your project. You can add new reports to an existing process template so that they are available for other team projects.

### How to Use This Chapter
Use this chapter to understand how TFS reporting works and how it can help you assess project health and status. To gain the greatest benefits from this chapter, you should:
* **Read the “Scenarios and Solutions” section**. Understand common reasons to use TFS reporting and learn the purpose of each standard report. 
* **Read the “Physical Architecture” section**. Learn what components make up the reporting system and how they interrelate.
* **Read the “Customizing Reports” section**. Learn the mechanisms available for report customization and creation.
* **Read the companion How To articles**. Read the following companion How To articles for a step-by-step walk through of various procedures discussed in this chapter. 
	* How To - Customize a Report with Visual Studio 2005 Team Foundation Server”
	* How To - Create a Custom Report in Visual Studio 2005 Team Foundation Server
	* How To - Create a Risk Over Time Report with Visual Studio 2005 Team Foundation Server

### Scenarios and Solutions
Reports are the primary way project managers and team leaders keep up to date with an ongoing project. After you create a new team project, a set of reports is generated for you based on the process template you chose. These reports are available to you from the project’s Microsoft Office SharePoint® portal site or from the reports node in Team Explorer inside Visual Studio. 

The following are common questions that can be answered by using TFS reports:
* When will my application be ready to ship?
* Is work proceeding according to plan?
* What is the quality of the build?
* What is the status of development against defined scenarios?
* How quickly is development work getting completed?
* Are bugs getting fixed?
* Are bugs regressing?

### Team Foundation Server Reports
Both the Microsoft Solution Framework (MSF) for Agile Software Development (MSF Agile) and MSF for CMMI® Process Improvement (MSF CMMI) process templates each include a set of reports by default.

#### Bugs
The bug-related reports in the process templates enable you to see what types of bugs are being generated and fixed and to identify trends. The following bug related reports are available:
* **Bugs by Priority**. Are the correct bugs being found? This report shows you the rate of high-priority bugs found versus low priority bugs. This report is available in both of the supplied process templates.
* **Bug Rates**. How effectively are bugs being found, fixed, and closed? This report shows trends over time for new bugs, bug backlogs, and bug resolution. This report is available in both of the supplied process templates.

#### Release Management
Release management reports enable you to judge how close your software is to being fit for release. The following release management reports are available:
* **Actual Quality versus Planned Velocity**. How many scenarios can be completed before quality is unacceptable? This report presents the relationship for each iteration, of estimated size to overall quality. This report is available in both process templates.
* **Builds**. What is the quality of a build? This report provides a list of available builds including build quality and other detailed information. This report is available in MSF for CMMI Process Improvement.
* **Quality Indicators**. What is the quality of the software? This report collects test results, bugs, code coverage and code churn into a single report to track project health. This report is available in MSF Agile and MSF CMMI.
* **Velocity**. How quickly is the team completing work? This report shows how quickly the team is completing planned work and show rates of change from day to day. This report is available in MSF Agile and MSF CMMI.
* **Scenario Details**. What scenarios are we building the application against? This report provides information on each scenario including completion status, risks and testing progress. This report is available in MSF CMMI.

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
* **Unplanned Work**. How much unplanned work is there? This report charts total work versus remaining work and distinguishes planned from unplanned tasks. This report is available in MSF Agile and MSF CMMI.
* **Work Items**. What are the active work items? This report lists every active work item. This report is available in MSF CMMI.
* **Work Items by Owner**. How much work is assigned to each member of the team? This report shows work items per team member. This report is available in MSF CMMI.
* **Work Items by State**. How many active, resolved and closed work items are there? This report lists work items organized by state. This report is available in MSF CMMI.

### Customizing Reports
You might want a report that does not exist in either of the MSF process templates. You can customize reports in one of three ways:
* **Use a filter on an existing report**. Many reports provide parameters that you can use to filter the report. For example date, area, iteration, and priority filters are available. Use these filters to review a subset of the data provided in the report.  Note that these filters are temporary and are lost when you browse away from the report.
* **Customize an existing report**. If a report you want is similar to an existing report, it is often easiest to make a copy of the existing report and then modify it. For example, you might want to plot risks over time to analyze how well your team is working with project risks. 
* **Create a new report**. You can create a new report from scratch.

If you modify an existing report or create a new report from scratch you can publish it to the Report Server so that it is available to the rest of your team. If you want to modify an existing report or create a new report, you can use one of the following methods:
* Use Microsoft Office Excel® to create pivot tables from data in the reporting databases.
* Create a new Report Server project in Visual Studio and then create new reports or import existing reports.

Creating a Report Server project in Visual Studio is the most powerful and flexible method for report creation and modification. 

**Note:** It is possible to use the Report Builder, available from the team reporting site; however this tool is not well supported for Visual Studio reporting scenarios and is not recommended. 

#### More Information
* For more information about customizing an existing report, see “How To: Customize a Report with Visual Studio Team Foundation Server.” 
* For more information about creating a custom report, see “How To: Create a Custom Report in Visual Studio Team Foundation Server.”
* For a step-by-step guide to creating a Risk over Time report, see “How To: Create a Risk over Time Report with Visual Studio Team Foundation Server.”

### Physical Architecture
Team Foundation Server is built on SQL Server 2005 and uses SQL Server Analysis Services to aggregate data and drive reports. You can create new reports by using Microsoft Excel or Visual Studio 2005 Report Designer. Reports are hosted on SQL Server 2005 Reporting Services and can be viewed from the report server Web site, team SharePoint project portal or from the Reports node in Team Explorer. Figure 15.1 shows the physical reporting architecture.

 
![](Chapter 15 - Reporting Explained_Fig15.1.GIF)
**_Figure 15.1** Physical Reporting Architecture_

Each TFS component maintains its own set of transaction databases. This includes work items, source control, tests, bugs, and Team Build. This data is aggregated into a relational database. The data is then placed in an Online Analytical Processing (OLAP) cube to support trend-based reporting and more advanced data analysis. 

The TfsWarehouse relational database is a data warehouse designed to be used for data querying rather than transactions. Data is transferred from the various TFS databases, which are optimized for transaction processing, into this warehouse for reporting purposes. The warehouse is not the primary reporting store, but you can use it to build reports.  The TfsReportDS data source points to the relational database. The Team System Data Warehouse OLAP Cube is an OLAP database that is accessed through SQL Server Analysis Services. The cube is useful for reports that provide data analysis of trends such as ‘how many bugs closed this month versus last month?’ The TfsOlapReportDS data source points to the Team System Data Warehouse OLAP cube in the analysis services database.

#### Components of the Reporting System
The reporting system consists of the following server-side and client-side components.

##### Server-Side Components
Server-side components include:
* **Report server databases**. These databases contain the report definitions, historical reports, and configuration data.
* **Report server Web service**. This Web service provides programmatic access to the Report Server.
* **Report Manager Web site**. This site provides user access to Report Server through a Web browser.
* **Windows service**. This service provides the scheduling and delivery of report snapshots.

##### Client-Side Components
Client-side components include:
* **Browser**. This component provides access to the Report Manager Web site.
* **Team Explorer**. This component provides access to reports through Visual Studio.

##### Report Development Tools
Development tools include:
* **Business Intelligence Designer Studio (BIDS)**. This component enables developers to design and deploy reports from within Visual Studio 2005.
* **Excel**. Excel can be used to generate pivot tables from the reporting store.
* **Report** **Builder**. This component allows end users to design ad-hoc reports. It is not well supported for Team Foundation reporting scenarios and is not recommended.

### Summary
The MSF Agile and MSF CMMI process templates each provide a set of default reports for bugs, release management, testing, and work item tracking: 
* Bug-related reports in the process templates enable you to see what types of bugs are being generated to help identify bug trends.
* Release management reports help you judge if your application is fit for release. 
* Testing reports enable you to monitor the effectiveness and progress of your testing efforts. 
* Work item reports enable you to assess the current state of your project and current project progress.

If you want to modify an existing report or create a new report, you can use the Report Builder available from the team reporting site, use Excel to create pivot tables from data in the reporting databases, or create a new Report Server project in Visual Studio.

### Additional Resources
* For more information about Team Foundation Server Reporting, see [http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194922(VS.80).aspx)