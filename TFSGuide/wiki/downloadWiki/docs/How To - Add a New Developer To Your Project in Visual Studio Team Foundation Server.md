### How To:  Add a New Developer to Your Project in Visual Studio 2005 Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System
* Microsoft SQL Server™ Reporting Services

### Summary
This How To article walks you through the process of adding a new developer to your team project in Team Foundation Server.  

### Contents
* Objectives
* Overview
* Summary of Steps
* Step 1 – Grant Access to the Team Project
* Step 2 – Grant Access to the Microsoft Office SharePoint® project site
* Step 3 – Grant Access to SQL Server Reporting Services
* Additional Resources

### Objectives
* Allow a developer to access the team project
* Grant a developer Read and Contributor access to SharePoint
* Allow a developer to view and subscribe to reports

### Overview
Whenever you add a new developer to a project, you need to grant the developer appropriate permissions to access your team foundation project and its associated SharePoint project site. The new developer's account must also have sufficient permissions with SQL Server Reporting Services to be able to view reports such as those presented by the team site portal.

### Summary of Steps
* Step 1 – Grant Access to the Team Project
* Step 2 – Grant Access to the Microsoft Office SharePoint® project site
* Step 3 – Grant Access to SQL Server Reporting Services

### Step 1 – Grant Access to the Team Project
In this step you grant your new team member access to the Team Foundation Server.

**To grant access to the team project:**
# Logon to Visual Studio with an account that is a member of the Team Foundation Administrators application group.
# Add the required project to **Team Explorer** (if it is not already listed)
# In **Team Explorer** right-click the team project, point to **Team Project Settings** and click **Group Membership**.
# Select **Project\Contributors** and click **Properties** and then add the new developer's account to this group. 

Note that membership in the Contributors group provides the typical set of permissions that a developer requires, including the ability to add, modify and delete items within the team project and perform builds.

### Step 2 – Grant Access to the SharePoint Project Site
In this step you grant your new team member access to the SharePoint project site.

**To grant access to the SharePoint project site:**
# Access the team project site with an account that is a member of the SharePoint Administrator site group. 
## Note that the project site for a project named YourProject is located by default at http://server/sites/YourProject/default.aspx
# Click **Site Settings**.
# Under **Administration** title, Click **Manage Users**.
# Click **Add Users**.
# Enter the account name of the new developer’s account in the form **domain\useraccount** of the new developer's account, select **Contributor** and then click **Next**.
# Enter the developer's e-mail address in the address field, and optionally type a message to welcome them to the site.
# Click **Finish**.

Note that membership in Contributors group allows the developer to view and add content to existing document libraries and lists. Membership in the Reader group, provides read only access to the site, it may be sufficient depending on the needs of the new developer. 

### Step 3 – Grant Access to SQL Server Reporting Services
In this step you grant your new team member access to SQL Report Services.

**To grant access to SQL Server Reporting Services**
# Logon to the SQL Server Reporting Services administration Web site at http://server/reports by using an administrator account. .
# Click your team project name.
# Click the **Properties** tab.
# Click the **Security** tab.
# Click **New Role Assignment**.
# Enter your developer's Microsoft Windows® account name, select **Browser** and then click **OK**.

Note that membership in the Browser group enables the developer to view and subscribe to reports.

### Additional Resources
* For a tutorial explaining how to work set permissions in SQL Server Reporting Services, see “Setting Permissions in Reporting Services” at [http://msdn2.microsoft.com/en-us/library/aa337491.aspx](http://msdn2.microsoft.com/en-us/library/aa337491.aspx)
* For more information on security roles in the application-tier, see “Securing Reporting Services” at  [http://msdn2.microsoft.com/en-us/library/ms157198.aspx](http://msdn2.microsoft.com/en-us/library/ms157198.aspx) 
* To view _SharePoint Administrators Guide_ to “Managing Site and Group Permissions”, see  [http://www.microsoft.com/resources/documentation/wss/2/all/adminguide/en-us/stsf03.mspx?mfr=true](http://www.microsoft.com/resources/documentation/wss/2/all/adminguide/en-us/stsf03.mspx?mfr=true)
* For more information on managing permissions in TFS see “Managing Permissions” at  [http://msdn2.microsoft.com/en-us/library/ms253094(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms253094(VS.80).aspx)