## Practices at a Glance: Source Control
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index

### Accessing Version Control
* _How to use version control from non-Visual Studio clients_
* _How to automate common version-control tasks_ 
* _How to work offline_

### Administration
* _How to add a new developer to your project_
* _How to remove a developer who has left your project_
* _How to grant permissions within your source tree_
* _How to move Team Foundation Server Version Control to another server_

### Branch/Label/Merge
* _How to use labels_
* _How to branch_
* _How to plan your branching structure_
* _How to use branching to support a release_
* _How to use branching to maintain a previous release_
* _How to use branching to stabilize your development and build process_
* _How to use branching to stabilize feature development_
* _How to use branching to stabilize development across teams_
* _How to use branching to isolate external dependencies_
* _How to retire an old release_
* _How to perform a merge_
* _How to perform a baseless merge_
* _How to resolve merge conflicts_

### Builds
* _How to use TFS to perform Continuous Integration builds_

### Check-ins and Check-in Policies
* _How to work with source control change sets_
* _How to enforce coding standards prior to check-in_
* _How to override a check-in policy_
* _How to undo a check-in_
* _How to resolve a conflict_
* _How to avoid conflicts_ 
* _How to create a custom check-in policy_

### Checkout, Get, and Lock
* _How to synchronize your computer with TFS_
* _How to prepare a file for editing_

### Code Sharing
* _How to share code_
* _How to manage shared binaries_

### Dependencies
* _How to manage Web service dependencies_
* _How to manage database dependencies_

### Distributed/Remote Development
* _How to access TFS over the Internet_
* _How to optimize TFS Version Control proxy performance_

### Migration
* _How to migrate your source from Visual SourceSafe_
* _How to migrate your source from other version-control systems_

### Project/Workspace Management
* _How to choose one team project versus multiple team projects_
* _How to organize your source tree_
* _How to define workspace mappings_
* _How to use workspaces to isolate code changes on your computer_

### Security
* _How to secure the channel between a developer workstation and TFS_ 

### Shelving
* _How to use shelving to back up pending work_
* _How to use shelving to share code with a team member_

## Accessing Version Control
* **How to use version control from non–Visual Studio clients**
* **How to automate common version-control tasks** 
* **How to work offline**

### How to Use Version Control from Non–Visual Studio Clients
You can access Microsoft® Visual Studio® 2005 Team System (VSTS) Team Foundation Server (TFS) Version Control from other clients by using one of the following approaches:
* Microsoft Source Code Control Interface (MSSCCI) integration
* Third-party integration
* Custom integration

**MSSCCI Integration**  
The following clients can work directly with TFS Version Control by using the MSSCCI provider:
* Microsoft Visual Studio .NET 2003
* Microsoft Visual C++® 6 SP6
* Microsoft Visual Basic® 6 SP6
* Microsoft Visual FoxPro® 9 SP1
* Microsoft Access™ 2003 SP2
* Microsoft SQL Server™ Management Studio
* Sparx Systems Enterprise Architect 61
* Sybase PowerBuilder 105
* Toad for SQL Server 2.0

The MSSCCI provider behaves differently than TFS Version Control in Visual Studio 2005 in the following ways:
* Checkout also performs a **GetLatest** operation.
* An exclusive check-in lock is applied at checkout.
* **Open-from source control** and **save-to source control** behave as they do in Microsoft Visual SourceSafe® (VSS).

You can download the MSSCCI provider from Microsoft MSDN® at [http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en)

The MSSCCI provider is not supported by Microsoft. If you have questions, consult the MSDN forums at [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=22&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=22&SiteID=1)

**Third-Party Integration**  
The following clients have integration solutions provided by other vendors:
* Eclipse
* Linux client
* Apple Macintosh client
* HTML Web client

If you want to access TFS Version Control from Eclipse IDE, Linux, or Macintosh clients, consider installing Teamprise from [http://www.teamprise.com/](http://www.teamprise.com/)

If you would like read-only access to TFS Version Control from the Internet, consider using Team System Web Access from [http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx](http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx)

**Custom Integration**  
Other clients have no integration solution currently available. You can either access TFS Version Control from the command line or build your own integration solution.  

To learn more about working with TFS Version Control, see “Walkthrough: Working with Team Foundation Source Control from Command Line” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx)

You can use control scripts and command files to automate the use of the command line. To learn more about working with control scripts and command files, see “Team Foundation Source Control Scripts and Command Files” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/1az5ay5c(VS80).aspx](http://msdn2.microsoft.com/en-us/library/1az5ay5c(VS80).aspx)

#### Additional Resources
* To download the MSSCCI provider from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en)
* If you want to access TFS Version Control from Eclipse IDE, Linux, or Macintosh clients, consider installing Teamprise at [http://www.teamprise.com/](http://www.teamprise.com/)
* If you would like to access TFS Version Control from the Internet, consider installing Team System Web Access at [http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx](http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx)
* To learn more about working with TFS Version Control, see “Walkthrough: Working with Team Foundation Source Control from Command Line” at [http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx)
* To learn more about working with control scripts and command files, see “Team Foundation Source Control Scripts and Command Files” at [http://msdn2.microsoft.com/en-us/library/1az5ay5c(VS80).aspx](http://msdn2.microsoft.com/en-us/library/1az5ay5c(VS80).aspx)
* To learn more about TFS Version Control extensibility, see “Walkthru: The Version Control Object Model” at [http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx)

### How to Automate Common Version-Control Tasks
To automate common version-control tasks, use the Team Foundation command-line tool (tf.exe). With this tool, you can do everything that you can do with Source Control Explorer, including source control operations (**add**, **check-in**, **checkout**, **get**, **lock**, **label**, and more), branching, shelving, workspace manipulation, and general administration tasks. 
 
The main reasons for using the command-line tool include automating repetitive operations and scheduling operations to run at specific times or on specific events by using the Microsoft Windows® Task Scheduler. The following commands are also only available from the command line: 
* Deleting another user’s workspace
* Undoing another user’s checkout
* Unlocking another user’s lock
* Defining label scope 
* Performing a baseless merge

To ensure that the appropriate path and other environment variables are set up, run the command-line tool from the Visual Studio 2005 Command Prompt window, or run the Vsvars32 batch file, which is normally located in _DriveLetter:\_Program Files\Microsoft Visual Studio 8\Common7\Tools. 

Tf.exe is installed as part of the TFS client and is located by default in the following folder:
{{ C:\Program Files\Microsoft Visual Studio 8\Common 7\IDE.}}

To run the command-line tool, you must specify a server name with the **/s** switch. The following command shows how to view the files in source control on the server named YourTFSServer:

{{ tf.exe dir /s:YourTFSServer }}

#### Additional Resources
* For more information, see “Walkthrough: Working with Team Foundation Source Control from Command Line” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/zthc5x3f(VS.80).aspx)
* For more information, see “MSDN Team Foundation Source Control Command-Line Reference” at [http://msdn2.microsoft.com/en-us/library/cc31bk2e(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/cc31bk2e(VS.80).aspx)

### How to Work Offline
Offline working is not supported natively by TFS Version Control.  

To work offline, you need to use the following strict workflow:
# **Manually remove read-only flags.** By default, all files in the workspace that have not been checked out are marked as read-only. When you work without a server connection, you must manually remove the read-only flag from files before editing or deleting them. To do this, right-click the file in Windows Explorer, click **Properties**, clear the **Read-only** check box, and then click **OK**. Alternatively, you can use the DOS command **attrib -r** 
# **Edit files.** You can now edit any files for which you have removed the read-only flag.
# **Add or delete files.** You can add or delete files for which you have removed the read-only flag. Do not rename files, because the **TFPT** **online** tool cannot distinguish a **rename** from a **deletion** paired with an **add** operation. **Note:** You must specify an option to the **TFPT** **online** command to get it to look for deletions because this is a more time-consuming operation.
# **Run the TFPT online command.** When you are back online, run the **TFPT online** command by typing **TFPT online** at the command line. This command scans your workspace for writable files and determines what changes should be pended on the server. If you have deleted any files, use the /**delete** switch. This tells the tool to scan for deleted files in your local workspace as well. The tool then displays the online window from which you can choose which changes to pend into the workspace.

**Important:** You must not rename any files while you are offline.

#### Additional Resources
* To download the TFPT tool from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)
* To learn about the Visual Studio Team Foundation Power Tool, see “Power Toy: tfptexe” at [http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx](http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx)
 
## Administration
* **How to add a new developer to your project**
* **How to remove a developer who has left your project**
* **How to grant permissions within your source tree**
* **How to move Team Foundation Version Control to another server**

### How to Add a New Developer to Your Project
To add a new developer to your project, grant the developer appropriate access to the team project and associated Microsoft Office SharePoint® project site. To enable the developer to view reports, grant the developer’s account access to SQL Server Reporting Services.

**To grant access to the team project**
# Log on to Visual Studio with an account that is a member of the Team Foundation Administrators application group.
# Add the required project to Team Explorer (if it is not already listed).
# Right-click the team project, point to **Team Project Settings**, and then click **Group Membership**.
# Select **Project\Contributors**, click **Properties**, and then add the new developer’s account to this group. 

**Note:** Membership in the Contributors group provides the typical set of permissions that a developer requires, including the ability to add, modify, and delete items within the team project and perform builds.

**To grant access to the SharePoint project site**
# Access the team project site with an account that is a member of the SharePoint Administrator site group. The project site for a project named YourProject is located by default at [http://server/sites/YourProject/default.aspx](http://server/sites/YourProject/default.aspx)
# Click **Site Settings**.
# Under the **Administration** title, click **Manage Users**.
# Click **Add Users**.
# Enter the account name of the new developer’s account in the form domain\useraccount, select **Contributor**, and then click **Next**.
# Enter the developer’s e-mail address, and optionally type a message to welcome the developer to the site.
# Click **Finish**.

**Note:** Membership in the Contributors group provides the typical set of permissions that a developer requires, including the ability to add, modify, and delete items within the team project and perform builds. If you need to restrict access to specific Visual Studio solutions or to specific folders in your team project, you can also assign permissions at the folder or file level. 

**To grant access to SQL Server Reporting Services**
# Log on to the SQL Server Reporting Services administration Web site using an administrator account. The site is located at [http://server/reports.](http://server/reports.)
# Click your team project name.
# Click the **Properties** tab.
# Click the **Security** tab.
# Click **New Role Assignment**.
# Enter your developer’s Windows account name, select **Browser**, and then click **OK**.

**Note:** Membership in the Browser group enables the developer to view and subscribe to reports. 

#### Additional Resources
* For more information, see “Team Foundation Server Default Groups, Permissions, and Roles” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms253077.aspx](http://msdn2.microsoft.com/en-us/library/ms253077.aspx)
* For more information, see “Source Control Security Rights and Permissions” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms181761.aspx](http://msdn2.microsoft.com/en-us/library/ms181761.aspx)

### How to Remove a Developer Who Has Left Your Project
If a developer has left your project, make sure that you delete that developer’s workspace. This operation not only helps to ensure the security of your project, but also removes any of the developer’s pending changes and undoes any locks held by the developer. 

**Note:** You cannot undo the locks without undoing the changes if an exclusive lock has been turned on for the team project.
 
To find out which files the developer has locked out, run the following command:

{{ tf workspaces /owner:domain\devuser /computer:* /server:servername }}

To delete the workspace and remove locks, run the following command:

{{ tf workspace /delete workspacename;domain\devuser /s:servername }}

Next, remove the developer’s account from the security groups. To do so, make changes in the following three places:
* **TFS team project –** Log on to Visual Studio with an account that is a member of the Team Foundation Administrators application group. Using Team Explorer, right-click the project, point to **Team Project Settings**, click **Group Membership**, and then remove the developer’s account from the relevant groups (normally Contributors).
* **SharePoint team project site –** Log on to the team site, located at [http://server/sites/_yourprojectname_/default.aspx](http://server/sites/_yourprojectname_/default.aspx) with an administrator account. Click **Site** **Settings**, **Manage Users** and then remove the developer account.
* **SQL Server Reporting Services –** Log on to the SQL Server Reporting Services administration Web site using an administrator account. The site is located at [http://server/reports.](http://server/reports.) Click your team project name, click the **Properties** tab, click the **Security** tab, and then delete the developer’s account.

#### Additional Resources
* For more information about cleaning up after a developer who has left a project, see “How to: Clean Up Files When Users Leave” at [http://msdn2.microsoft.com/en-us/library/ms194958(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194958(VS.80).aspx)
* For more information about the **Workspace** command, see “Workspace Command” at [http://msdn2.microsoft.com/en-us/library/y901w7se(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/y901w7se(VS.80).aspx)
* For more information about finding pending changes, see “How do I tell who has files checked out or locked?” at [http://blogs.vertigosoftware.com/teamsystem/archive/2006/07/24/3125.aspx](http://blogs.vertigosoftware.com/teamsystem/archive/2006/07/24/3125.aspx)

### How to Grant Permissions Within Your Source Tree
You can set permissions on a file or folder within your source tree by right-clicking the file or folder in Source Control Explorer, clicking **Properties**, clicking the **Security** tab, selecting the user or group for which you want to change permissions, and then editing the permissions. You can also set permissions by using the **Permission** switch with the tf.exe command-line utility for source control.

Although you can apply source control permissions to specific folders and files, by default, permissions within your source tree are inherited from the permissions applied to the project folder. If your developers are members of the Project\Contributors application group, they will be able to read, check out, check in, label, and lock source files. If you need to provide restricted access to a subset of folders or source files within your team project—for example to enable a developer only to work on certain source files within your team project—you can set permissions at the folder or file level. 

#### Additional Resources
* For more information about granting permissions, see “Team Foundation Server Default Groups, Permissions, and Roles” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms253077.aspx](http://msdn2.microsoft.com/en-us/library/ms253077.aspx)
* For further information about granting permissions, see “Source Control Security Rights and Permissions” at [http://msdn2.microsoft.com/en-us/library/ms181761.aspx](http://msdn2.microsoft.com/en-us/library/ms181761.aspx)
* For more information about the **tf permission** command, see “Permission Command” at [http://msdn2.microsoft.com/en-us/library/0dsd05ft(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/0dsd05ft(VS.80).aspx)

### How to Move Team Foundation Version Control to Another Server
Team Foundation Server does not support copying a server from one location to another, nor does it support mirroring. You can back up and restore a complete server, move your existing server hardware to a new domain, or upgrade to a dual-server deployment. You cannot perform partial moves; for example, moving some projects from your server but keeping others.   

Team Foundation Server supports the following three move types:
* **Backup Restore** – Use this move type when you need to move your Team Foundation Server to a new machine. For specific steps, see “How to: Move Your Team Foundation Server from One Hardware Configuration to Another” at [http://msdn2.microsoft.com/en-us/library/ms404869(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404869(VS.80).aspx)
* **Environment** – Use this move type when you need to move your Team Foundation Server to a new domain or workgroup. For specific steps, see “How to: Move Your Team Foundation Server from One Environment to Another” at [http://msdn2.microsoft.com/en-us/library/ms404883(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404883(VS.80).aspx)
* **Single Server to Dual Server** – Use this move type when you need to move from a single-server deployment to a dual-server deployment. For specific steps, see “How to: Move from a Single-Server to a Dual-Server Deployment” at [http://msdn2.microsoft.com/en-us/library/ms404854(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404854(VS.80).aspx)

Keep the following considerations in mind when moving a Team Foundation Server:
# Changing the TFS application-tier server name requires that all TFS clients must connect to a new server name.
# All query-bound Microsoft Office documents will no longer work if the server name is changed. The documents are bound to the server for which they were created. This includes all of the query-bound Microsoft Office documents that are created automatically at project creation time in the project **Documents** node.
# Any embedded links to documents will point to an unknown server name if the server name is changed.
# Local accounts existed on the original TFS. You must decide whether these accounts will be re-created as local accounts on the moved TFS, or as domain accounts in the moved Team Foundation Server’s new domain.
# Domain accounts existed on the original TFS, but you are moving TFS to a domain that does not trust the original domain. You must decide whether these accounts will be re-created as local accounts on the moved TFS, or as domain accounts in the moved Team Foundation Server’s new domain. 

Test your server after the move to ensure that nothing serious was broken in the transition. Testing should check the following areas:
* Were all the assets moved correctly? Look at your source tree, work items, and team pages to be sure that they are all in place.
* Are the user accounts still operative? Try logging in with a few different account types to make sure that they still work.

#### Additional Resources
* For more information about moving TFS, see [http://msdn2.microsoft.com/en-us/library/ms404879(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms404879(VS.80).aspx)

## Branch/Label/Merge
* **How to use labels**
* **How to branch**
* **How to plan your branching structure**
* **How to use branching to support a release**
* **How to use branching to maintain a previous release**
* **How to use branching to stabilize your development and build process**
* **How to use branching to stabilize feature development**
* **How to use branching to stabilize development across teams**
* **How to use branching to isolate external dependencies**
* **How to retire an old release**
* **How to perform a merge**
* **How to perform a baseless merge**
* **How to resolve merge conflicts**

### How to Use Labels
Use labels to group a set of files and folders together for future operations. You can use labels for branching, merging, diffing, or getting files. A label provides a marker to which you can return when performing one of the above operations at a later date.

**To apply a label to a file or folder**
# Right-click the file or folder in Source Control Explorer and then click **Apply Label**.
# In the **Choose Item Version** dialog box, modify your choice of file or folder, choose the version of the file or folder that you would like to label, and then click **OK** to apply the label.

When applying labels, consider the following:
* Labels are markers that you can apply to only one version of a file or folder at a time.
* You can apply multiple labels to a version of a file or folder.
* Labels that you apply by using Source Control Explorer are automatically scoped to the root folder of the team project within which they are created. You cannot create two labels with the same name within the same scope.
* Labels are un-versioned objects and there is no history associated with them.
* Labels are applied instantly, and they do not require a check-in
* Team Build automatically assigns a label to the set of files associated with each build that it creates.
* Labels are not applied to deleted items; this means that merge-by-label will not pick up deleted files.

**To locate an existing label**
# On the **File** menu, point to **Source Control**, point to **Label**, click **Find Label**, and then navigate to the label. 
# After finding the label, you can modify it or delete it from within the **Find Label** dialog box.

#### Additional Resources
* For more information about using labels, see “Working with Labels” at [http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx)
* For more information about applying labels, see “How to: Apply Labels” at  [http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx)

### How to Branch
To create a branch, either use Source Control Explorer or use the **tf** **branch** command from the command line. 

To branch from Source Control Explorer, right-click the top-level folder containing your project source, click **Branch**, and then specify a target folder location with a folder name to indicate the purpose of the branch; for example, **MyProject_Release1.0_Branch**.

To branch from the command line, use the **tf branch** command from a Visual Studio 2005 Command Prompt; for example:

{{ tf branch C:\MyProject $/MyProject_Release1.0_Branch }}

Use branches only when you need to provide isolation while you do parallel development. When using branches you will have to eventually merge the changes to the main branch and as merging incurs overhead and requires you to manage conflicts, do not branch unless you need the file isolation that branching provides. You can label a build and branch later if needed.  

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Plan Your Branching Structure
Branches are a mechanism to enable isolation; they are used to allow multiple developers to work on the same files in isolation. To plan your branching approach, evaluate common branching scenarios and choose a strategy based on team size, composition, release schedule, and build stability requirements. 

Common branch scenarios include:
* **Release** – Branch to stabilize code you want to release. You can branch before release, avoiding the need to lock down the main branch.
* **Maintenance** – Branch to maintain a previously released build.
* **Feature** – Branch to isolate feature development that might make the rest of the project unstable. 
* **Team** – Branch to isolate sub-teams so that they can work without being subject to breaking changes, or that they can work towards unique milestones. These are very similar to feature branches.

Do not branch unless it becomes necessary for your development team. Branching introduces additional source tree maintenance and merging tasks. Most development teams working on short release cycles (e.g., Line-of-Business [LOB](LOB) applications) will never need a branch. Development teams working on longer release cycles (e.g., packaged Independent Software Vendor [ISV](ISV) applications) are more likely to employ branching as part of the development process.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Support a Release
Use a Release branch when you are ready to stabilize your build prior to release. 

The following is an example of what your branch structure might look like after you have created a Release branch:
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**
* **Releases** – Container for release branches
	* **Release 1** – Release branch
		* **Source**

Keep the following recommendations in mind when working with Release branch:
* **When to branch** – When you are ready to release, integrate everything into the Main branch and then create Release branch that can be used to stabilize the application prior to release.
* **When not to branch** – If you are using one TFS project per release, you can use the new project to continue development, instead of a branch in the current project.
* **Permissions on branch**: 
* **Prior to release** – assign read/write permissions to all developers.
* **After release** – Assign read/write permissions to developers working on hotfixes, read-only for everyone else.
* **Build frequency in branch** – The builds are performed on-demand.
* **Testing focus in branch** – Sign off on release.

You should use the Release branch for the targeted fixes and changes necessary in order to stabilize a build prior to release. Development of the next version of your application can occur in parallel in your Development or Main (integration) branches so that they can get the benefit of the stabilization changes you made prior to release. After a final release build has been created, you can merge the changes from the Release branch back into your Development and Main (integration) branches.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Maintain a Previous Release
Use maintenance branches to support previously released builds. This is very similar to branching for release, but at this point the branch is maintained over time in order to support the release.

The following is an example of what your branch structure might look like after you have released your application and maintain a branch to support the release:
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**
* **Releases** – Container for release branches
	* **Release 1** – Maintenance Branch
		* **Source**
		* **Other Asset Folders**

Keep the following recommendations in mind when working with a maintenance branch:
* **When to branch** – After you have released, support the release with a branch in the Releases folder.  
* **When not to branch** – If you will never need to maintain the release, you can use a label to mark the old released build and continue work in the main branch.
* **Permissions on branch** – Assign read/write permissions to developers working on hot fixes, and read-only permissions to everyone else.
* **Build frequency in branch** – The builds are performed on-demand.
* **Testing focus in branch** – Sign off on release.

You should use maintenance branches to support an older version of your application. You might choose to merge these changes into your Main (integration) branch, or leave them specific to the maintenance branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Stabilize Your Development and Build Process
Use a Development branch for active development and a Main branch for your integration build, thus avoiding build breaks.

The following is an example of what your branch structure might look like after you have created a Development branch:
* **Development** – Development Branch
	* **Source**
* **Main** – Integration Branch
	* **Source**
	* **Other Assets folders**

Keep the following recommendations in mind when working with a Development branch:
* **When to branch** – If you are creating daily builds and are having problems with build stabilization and integration, create both a Main and a Development branch to provide more predictability to your daily build. You might also want to consider more stringent check-in policies to improve check-in quality. 
* **When not to branch** – If you are only creating Continuous Integration (CI) builds, or your daily builds are already predictably stable, you might not need the extra overhead of an integration branch.
* **Permissions on branch**: 
	* The Main branch should be read/write for developers responsible for merging and integration, but read-only for everyone else. 
	* The Development branch should be read/write for everyone.
* **Build frequency in branch**: 
	* Daily builds on the Main branch.
	* Continuous Integration builds on the Development branch.
* **Testing focus on branch:** 
	* Perform integration, performance, and security testing on the Main branch.  
	* Perform feature and quick feedback testing on the Development branch.

Use the Main branch as a staging ground for integrating changes that have been checked into the development branch. Perform all active development in the Development branch, and integrate non-breaking changes into the Main branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Stabilize Feature Development
Use Feature branches to improve the integration and stabilization of breaking changes across features. 

The following is an example of what your branch structure might look like after you have created Feature branches:
* **Development –** Container for feature branches
	* **Feature A –** Feature branch
		* **Source**
	* **Feature B –** Feature branch
		* **Source**
	* **Feature C –** Feature branch
		* **Source**
* **Main –** Integration branch
	* **Source**
	* **Other Asset Folders**

Keep the following recommendations in mind when working with Feature branch:
* **When to branch** – Feature teams often have source file overlap, increasing the potential for build breaks and check-in conflicts. If you are experiencing these problems, consider feature branches for each feature to provide feature isolation. You can create these off  Main branch for small teams, or off a Team branches for larger teams.
* **When not to branch** – If you are only creating CI builds, or your daily builds are already predictably stable, you might not need the extra overhead of Feature branches.
* **Permissions in branch** – Assign read/write permissions to developers on the feature branch, and read-only permissions to everyone else.
* **Build frequency on branch** – Continuous integration builds are performed on the branch. 
* **Testing focus in branch** – Perform feature and quick feedback testing.

Use the Feature branch to allow each feature to be developed in parallel. Perform all active development in the Feature branches and then integrate your code into the Main branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Stabilize Development Across Teams
Use Team branches to improve the integration and stabilization of breaking changes across teams. 

The following is an example of what your branch structure might look like after you have created Team branches:
* **Development -** Container for team branches
	* **Team 1 -** Team branch
		* **Source**
	* **Team 2 -** Team branch**** 
		* **Source**
* **Main –** Integration branch
	* **Source**
	* **Other Asset Folders**

Keep the following recommendations in mind when you work with Team branch:
* **When to branch** – If your development teams overlap on files and components, use Team branches to isolate each team’s work. You might also choose to create Feature branches beneath the Team branches.
* **When not to branch** – If your source tree is organized by component, and you are confident that there will not be breaking interface changes or a large number of check-in conflicts across your teams, you probably do not need Team branches.
* **Permissions in branch** – Assign read/write permissions to developers on the team, and read-only permissions to everyone else
* **Build frequency on branch** – Continuous integration builds are performed on the branch.
* **Testing focus in branch** – Perform feature and quick feedback testing.

The Team branches should be used to allow teams to complete development tasks in parallel. This can be useful to isolate teams from breaking changes originating on other teams, or to allow teams to work toward unique milestones. All active development should occur in the Team branches and then be integrated into the Main branch. You might also want to create Feature branches beneath each Team branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Use Branching to Isolate External Dependencies
Use an External branch to improve the integration and stabilization of breaking changes caused by external dependencies. 

The following is an example of what your branch structure might look like after you have created an External branch:
* **External –** External branch
	* **Source**
* **Main –** Integration branch
	* **Source**
	* **Other Asset Folders**

Keep the following recommendations in mind when working with an External branch:
* **When to branch** – When you have external dependencies that might cause breaking changes in your project. If your dependencies are making interface changes or substantial logic changes that will impact your code, create an External branch to isolate these changes.
* **When not to branch** – When your external dependencies are stable or you are confident they will not introduce breaking changes.
* **Permissions in branch** – Read/write for developers responsible for external dependency integration, read-only for everyone else.
* **Build frequency on branch** – Builds are performed on-demand.
* **Testing focus in branch** – Integration testing.

You should use the External branch as an isolated location to test changes in external dependencies before you integrate them into the Main branch. This can be useful to isolate the development team from breaking changes caused by external dependencies such as headers and libraries. 

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Retire an Old Release
When a Release branch in your Releases folder is old enough that you no longer have to support it, create a Safe Keeping folder in which to store the old release. The following is an example of what your branch structure might look like after you have created a Safe Keeping folder:
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**
* **Releases** – Container for release branches
	* **Release 2** – Maintenance Branch
		* **Source**
		* **Other Asset Folders**
* **Safe Keeping -** Container for safe keeping branches
	* **Release 1 -** Safe keeping branch
		* **Source**
		* **Other Asset Folders**

The goal of moving the branch from the Releases folder to the Safe Keeping folder is to reduce clutter in the Releases folder without having to delete old releases. This is not a new branch, but rather the moving of an old branch to a new folder.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How to Perform a Merge
Use the **merge** command to integrate changes from one branch into another. To perform a merge, you can use the merge functionality in Source Control Explorer, or you can use the **tf** **merge** command line. You can merge by changeset, label, date, or version. To start a merge, right-click the branch in Source Control Explorer and then click **Merge**. The Source Control Merge Wizard allows you to choose the target branch with which to merge.  

Depending on your branch structure, you might need to merge changes up the branch hierarchy, down the hierarchy, or across the hierarchy. If you are merging across the hierarchy, you are performing a baseless merge and you must use the **tf** **merge** command line, because you cannot do this with Visual Studio. A baseless merge allows you to merge files and folders that do not have a branch/merge relationship. After a baseless merge, a merge relationship exists and future merges are not baseless. You still need to execute the merges from the command line, but the number of merge conflicts will be reduced. 

Keep the following in mind when performing merges:
* Merging along the hierarchy—from parent to child or from child to parent—results in fewer conflicts than merging across the hierarchy.
* The branch hierarchy is based on the branch parent and branch child, which might be different from the physical structure of what you see in Source Control Explorer; for example:
	* **Physical structure**:
		* **Development –**Development branch
		* **Main –** Integration branch
		* **Releases** – Container for release branches
			* **Release 1** – Release Branch
	* **Logical structure**:
		* **Main**
			* **Development**
			* **Release 1**

#### Additional Resources
* For more information about merging, see “Understanding Merging” at [http://msdn2.microsoft.com/en-us/library/ms181427(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181427(VS.80).aspx)
* For a walkthrough describing how to perform a merge, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)

### How to Perform a Baseless Merge
To perform a baseless merge, you use the **tf merge /baseless** command from the Visual Studio 2005 Command Prompt. 

For example, the following command line will perform a baseless merge from the source branch to the target branch. The **/recursive** switch is used to perform a recursive merge of all the files and folders within the specified branch path:

{{ tf merge /baseless <<source path>> <<target path>> /recursive }}

**Example**
{{
 tf merge /baseless c:\data\proj1 c:\data proj2 /recursive
}}
The process of merging items that are not directly branched from each other is known as a _baseless_ _merge_. For example, you might want to merge a change between two release branches that are siblings of each other without merging up to the parent branch. Baseless merging only works from the command line; you cannot perform a baseless merge from Visual Studio.

When you perform a baseless merge, TFS does not have any information about the relationship between the files in the branches. For instance, a file rename will be viewed as a deleted file and a new file in the branch. For this reason you will have to perform more manual conflict resolution than you would when performing a normal merge. However, you only have to perform this conflict resolution one time. After you have performed the baseless merge, TFS records history and establishes a relationship between the folders/files.

Baseless merges can only be created from the command line. Even after the first baseless merge, when a relationship has been created between the branches, future merges still need to be created from the command line.

#### Additional Resources
* For an explanation of **merge** command syntax, see “Merge Command” at [http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx)
* For more information about merging, see “Understanding Merging” at [http://msdn2.microsoft.com/en-us/library/ms181427(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181427(VS.80).aspx)
* For a walkthrough describing how to perform a merge, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)

### How to Resolve Merge Conflicts
To resolve merge conflicts, you use the Visual Studio merge tool. If a conflict is detected during a merge, you can resolve conflicts either automatically or manually. If you choose to resolve the conflict manually, you can keep the source changes, keep the target changes, or resolve the conflict in the merge tool.

You might need to resolve conflicts when merging changes between branches, getting files into your workspace, or checking in new versions of files. There are three conflict types:
* **Version** – The file has evolved along divergent paths. This could be the result of a file edit, rename, delete, or undelete operation. 
* **File Name Collision** – Two or more items are trying to occupy the same path.
* **Local Overwrite** – Only occurs during a **get** operation, if you are trying to overwrite a local, editable file.

Most conflicts can be resolved automatically; version conflicts are the only conflict type that might result in a manual merge operation. Manual merge is most common in the following scenarios:
* A file has been edited in both branches, with changes to the same lines of code.
* A baseless merge is being conducted in which the branch file relationships are not known to TFS.

The merge tool shows you the details for each conflict and allows you to choose which change you want to keep in the final merged file. You can choose to keep the source change or the destination change, integrate both changes, or manually modify the final version by typing directly into the file.

After resolving every conflict in the file, save the final version as a pending change to be checked into the target branch.

Be careful when merging because it is easy to make mistakes that may result in build instability. After you have finished merging, compile the resulting source and run unit tests to test for major breaks.

#### Additional Resources
* For more information about resolving conflicts, see “How to: Resolve Conflicts” at [http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx)

## Builds
* **How to use TFS to perform Continuous Integration builds**

### How to Use TFS to Perform Continuous Integration Builds
To perform continuous integration and rebuild your project every time a file is checked in, you need to use a Web service to trigger the build process. You subscribe the Web service to check-in events so that the build is triggered each time someone checks in a file. To trigger the build, you also need to use an appropriate build type that determines what configuration is built, what post-build steps and tests are executed, what drop location is used, and so on. 

#### Additional Resources
* To download a Web service to trigger the build process available from Microsoft, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)

## Check-ins and Check-in Policies
* **How to work with source control change sets**
* **How to enforce coding standards prior to check-in**
* **How to override a check-in policy**
* **How to undo a check-in**
* **How to resolve a conflict**
* **How to avoid conflicts** 
* **How to create a custom check-in policy**

### How to Work with Source Control Change Sets
A _changeset_ groups together a set of changes associated with a given check-in. The common operations you need to perform on changesets are:
* Checking in a changeset associated with a work item
* Labeling a changeset
* Viewing details about a changeset.
* Changing details about a changset.
* Rolling back a changeset

**To check in a changeset associated with a work item**
# On the Visual Studio **View** menu, point to **Other Windows** and then click **Pending Changes**.
# Enter a suitable comment to reflect the nature of the changes.
# Click the **Work Items** icon to display the list of associated work items.
# Update the associated work items by selecting them and then specifying the check-in action **Associate** or **Resolve** (if the check-in means that the work item is resolved).
# Click **Check In** to check the changeset into the source control server.

**To label a change set**
# In Visual Studio, in Source Control Explorer, right-click your Team Project folder and then click **Apply Label**. 
# In the **Version** drop-down list, select **Changeset**, enter a **Changeset number**, and then click **OK**.
# In the **Apply Label** dialog box, enter a label name and comment, and then click **OK**.

**To view changeset details**
* Use the **tf** **changeset** command. 
The following command displays details about changeset number 1234 by displaying the **Details for Changeset** dialog box:

{{ tf changeset 1234 }}

By using the dialog box, you can view the source files contained in the changeset, view the check-in comments and notes, view associated work items, and view any policy warnings that were generated when the changeset was checked into the server.

**To change details about a changeset**
* Use the **tf** **changeset** command to alter the comments and/or notes associated with the changeset. 
The following command displays the **Details for Changeset** dialog box for changeset 1234 and updates the displayed comment field, allowing you to change the comment:
 
{{ tf changeset /comment:"This is a much better comment than the last one." 1234 }}

The following command updates the code reviewer and security reviewer notes associated with changeset 1234:

{{ tf changeset /notes:"Code Reviewer"="C Davis";"Security Reviewer"="F Smith" 1234 }}

To roll back a changeset and remove the changes from the source control server, you use the Team Foundation Power Tool.

**To roll back a changeset using the Team Foundation Power Tool**
* Use the **Tfpt** **rollback** command. 
The following command rolls back change set number 1234.

{{ TFPT rollback /changeset:1234 }}

This command causes the Roll Back Changeset window to display. You can select the files contained within the changeset to roll back. 

#### Additional Resources
* For more information about the **tf changeset** command, see “Changeset Command” at [http://msdn2.microsoft.com/en-us/library/w51xa47k(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/w51xa47k(VS.80).aspx)
* For more information about retrieving changesets, see “How to: Retrieve Old Versions of Files from Changesets” at [http://msdn2.microsoft.com/en-us/library/ms181416(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181416(VS.80).aspx)
* To download the Team Foundation Power Tool (TFPT) from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)
* To learn more about the Team Foundation Power Tool, see “Power Toy: tfptexe” at [http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx](http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx)

### How to Enforce Coding Standards Prior to Check-in
Use TFS check-in policies to ensure that all code checked into the server meets your required coding standards. 

The following check-in policies are available by default:
# **Code Analysis –** Requires that code analysis be run before check-in.
# **Test Policy –** Requires that check-in tests be completed before check-in.
# **Work Items –** Requires that one or more work items be associated with the check-in.

The default code analysis check-in policy provides code analysis checks for both managed and unmanaged code. Managed code statically analyzes your code to ensure that it conforms to standard .NET design rules, globalization rules, interoperability rules, naming rules, performance rules, security rules, and more. If you need to extend the code analysis, you can develop your own code analysis rules.

**To configure the code analysis check-in policy**
# In Team Explorer, right-click your team project, point to **Team Project Settings**, and then click **Source Control**. 
# Click **Check-in Policy** and then click **Add**. 
# In the **Check-in policy** list, select **Code Analysis** and then click **OK**. 
# Specify the type of code analysis that you want performed by selecting the appropriate check boxes. If you select **Enforce Code Analysis For Managed Code**, select the required rules in the **Rule settings for Managed Code Analysis** list. 
# Click **OK** twice. 

**Important:** Although the above procedure ensures that the configured policy is executed whenever a developer checks in a source file, developers can always override policy at check-in time. If you want to monitor this in order to manage this scenario, you can hook the policy override event. 

You can create your own custom check-in policies that will enforce your project-specific quality gates; for example, if you want to enforce the following:
* Users should add comments at the time of check-in.
* Users should run additional acceptance tests before checking in the code.
* Users do not use certain pragma directives in C# to suppress XML documentation warnings 
* Ensure that the projects are configured to generate XML documentation during compilation.

To create custom policy plug-ins that will appear in the **Add Checkin Policy** dialog box, use the extensibility features provided in the Visual Studio Team Foundation Server Software Development Kit (SDK).

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Create Custom Check-In Policies in Visual Studio Team Foundation Server” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx)
* To view sample code that will disallow selected patterns upon check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To view sample code that will enforce comments upon check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)
* For more information about how to use code analysis tools, see “Guidelines for Using Code Analysis Tools” at [http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx)

### How to Override a Check-in Policy
To override a check-in policy, select the **Override policy failure and continue check-in** check box in the **Policy Failure** dialog box. Any user who has permission to check in files can override a check-in policy.

If you would like to detect when a member of your team overrides a check-in policy, you can use the Team Foundation Eventing Service to hook check-in events.  

#### Additional Resources
* To learn more about overriding a check-in policy, see “How to: Override a Check-in Policy” at [http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx)
* To learn more about the Team Foundation Eventing Service, see “Eventing Service” at [http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx)
* To learn how to use the TFS Object Model to detect a policy override, instead of eventing, see James Manning’s blog post on MSDN at [http://blogs.msdn.com/jmanning/archive/2005/11/04/489193.aspx](http://blogs.msdn.com/jmanning/archive/2005/11/04/489193.aspx)

### How to Undo a Check-in
To undo the check-in of a file, use the Team Foundation Power Tools (TFPT) **rollback** command to revert the file to the previous version. The **rollback** command enables you to roll back an entire changeset at a time, but you can also select individual files from within the changeset to roll back. This is useful if you need to undo a change to a file that was mistakenly checked in, or where you want to undo the check-in because the changes are causing serious integration build issues. 

**To undo a file check-in and revert to the previous version**
* Run the following command from a command window that includes the \program files\microsoft team foundation server power tools folder in the path:
 
{{ TFPT rollback filename.cs }}

**Note:** If you know the changeset number of the changeset containing the check-in you want to undo, you can supply the changeset number on the command line as follows:

{{ TFPT rollback filename.cs /changeset:54 }}

* The **rollback** command needs to ensure that your local workspace is up to date. Click **Yes** in response to the **Roll Back Changeset** message. At this point your workspace is updated with files from the server. 
* If you did not specify a changeset number on the command line, the **Find Changeset** dialog box is displayed. Enter search criteria, or simply click **Find** and then locate and select the changeset that contains the check-in you want to undo, and then click **Roll Back**. 
* The **Roll Back Changeset** dialog box is displayed .Because the changeset might contain multiple check-ins, you should select the file for which you want to undo the check-in and then click **Roll Back**. 
**Note:** If you specified the filename on the command line, only this file in the changeset will be selected. 

When undoing check-ins by using the **TFPT** **rollback** command, you should be aware of the following:
* **Workspace location –** TFPT locates workspaces as follows: If you specify a file path as an argument to filter the rollback, the file paths are used to find the workspace. If you do not specify file paths, the local directory is used to identify the workspace, if the local directory is mapped. The simplest approach to ensure that the tool locates the right workspace is to run the command from a locally mapped directory.
* **Pending changes –** You cannot roll back a changeset that contains pending changes. If you attempt to do so, the tool reports an error. In this instance, you must move pending changes to a shelveset and then undo or check in all pending changes before running the **rollback** command.
* **Merge scenarios –** If you are undoing the check-in of a file that has very recently been checked in, you probably will not need to merge changes because it is unlikely that anyone else will have updated the item in the intervening period. However, if you want to undo a check-in, and the check-in to be undone is not the latest change to a file, a three-way merge is required. The current version on the server, the version you have in your workspace, and the version you want to roll back to must be merged together. If there are no conflicts, the changes from the version to be rolled back are extracted from the file, and any changes that came after that version are preserved. 
* **Resolving conflicts –** If you do need to perform a merge, the merge window is displayed. To resolve the merge, select the item and then click **Merge**. An automatic merge is initially attempted; if it fails, the merge tool is invoked to resolve the merge. The **Auto-Merge All** button attempts to automatically merge each of the items in the merge list, but does not attempt to invoke the merge tool.

#### Additional Resources
* To download the TFPT tool from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)
* To learn more about the TFPT, see “Power Toy: tfptexe” at [http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx](http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx)

### How to Resolve a Conflict
To resolve merge conflicts, use the Visual Studio merge tool. If a conflict is detected during a merge, you can resolve conflicts either automatically or manually. If you choose to resolve the conflict manually, you can keep the source changes, keep the target changes, or resolve the conflict in the merge tool.

You might need to resolve conflicts when merging changes between branches, getting files into your workspace, or checking in new versions of files. There are three conflict types:
* **Version** – The file has evolved along divergent paths. This could be the result of a file edit, rename, delete, or undelete operation. 
* **File Name Collision** – Two or more items are trying to occupy the same path.
* **Local Overwrite** – Only occurs during a **get** operation, if you are trying to overwrite a local, editable file.

Most conflicts can be resolved automatically; version conflicts are the only conflict type that might result in a manual merge operation. Manual merge is most common in the following scenarios:
* A file has been edited in both branches, with changes to the same lines of code.
* A baseless merge is being conducted in which the branch file relationships are not known to TFS.

The merge tool shows you the details for each conflict and allows you to choose which change you want to keep in the final merged file. You can choose to keep the source change or the destination change, integrate both changes, or manually modify the final version by typing directly into the file.

After resolving every conflict in the file, save the final version as a pending change to be checked into the target branch.

Be careful when merging because it is easy to make mistakes that might result in build instability. After you have finished merging, compile the resulting source and run unit tests to test for major breaks.

#### Additional Resources
* For more information about resolving conflicts, see “How to: Resolve Conflicts” at [http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx)

### How to Avoid Conflicts
To help avoid conflicts:
* **Ensure effective team communication.** When you work on a source file, let other team members know that you are working on the file and which aspects you will be updating. Although automatic conflict resolution can resolve many conflicts, you should avoid situations where two or more developers are working on the same functional areas in the same source file where there is a strong likelihood of you both making changes to the same lines of code. Conflicts on the same lines of code require manual conflict resolution, which complicates the merge operation.
* **Determine who else has a file checked out.** Before updating a file, check to see if another team member has already checked out the file. If so, ask your colleague what he or she is working on and then decide if you can wait until they complete their changes or if it is safe to continue to work in parallel on the same file because you are working on separate functionality in separate source code regions within the file.

**To view pending changes**
# In Source Control Explorer, right-click the solution, project, folder, or file for which you want to see pending changes.
# Select **View Pending Changes**.

This method shows you all of the pending changes within the scope you have selected. You can also use the command-line checkout tool as follows to learn about pending changes:

{[ tf status /format:detailed /user:* }}

This command displays detailed status information about any pending changes made by all users. In the resulting list, you can see who has which files checked out, along with pending changes. To view the pending changes for a specific file, specify the filename as the first argument to tf.exe.

#### Additional Resources
* For more information about viewing pending changes in your workspace, see “How to: View and Manage All Pending Changes in Your Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx)
* For more information about viewing pending changes in other workspaces, see “How to: View Pending Changes in Other Workspaces” at [http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx)
* For more information about the **tf status** command see “Status Command” at [http://msdn2.microsoft.com/en-us/library/9s5ae285(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/9s5ae285(VS.80).aspx)

### How to Create a Custom Check-in Policy
To create a custom check-in policy, use the plug-in model exposed by the policy framework.

You can create a custom check-in policy to implement your own policy logic; for example, if you want to check if users have been adding comments or using regular expressions correctly at the time of check-in.

Plug-ins are used both within the policy definition process and during the policy evaluation process. Policy plug-ins are installed either as stand-alone utilities or as part of a separate application, and are registered with the policy framework so that they can be loaded as needed.

A policy plug-in must expose the following interfaces:
* **IPolicyDefinition** – The **IPolicyDefinition** interface exposes methods that are used in the process of defining policy requirements for a team project. This interface includes methods for invoking a user interface specific to the policy plug-in in order to allow users to easily define a check-in policy.
* **IPolicyEvaluation** – The **IPolicyEvaluation** interface exposes methods that are used in the process of evaluating policy compliance during the check-in process. This interface includes methods that accept the contents of a check-in operation and analyze them to establish whether the defined policy is satisfied.
You can package multiple policy plug-ins n the same assembly. The only requirement is that you implement the plug-ins as separate classes.
**Note:** These interfaces are exposed in **PolicyBase** class. As an alternative to implementing **IPolicyDefinition** and **IPolicyEvaluation** interfaces, you can derive a class from **PolicyBase**.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To - Create Custom Check-In Policies in Visual Studio Team Foundation Server” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx)
* To view sample code that will disallow selected patterns upon check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments upon check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)
* For more information about using code analysis tools, see “Guidelines for Using Code Analysis Tools” at [http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms182023(VS.80).aspx)
* For more information about creating a new policy, see “Policy Plug-ins” at [http://msdn2.microsoft.com/en-us/library/bb130343(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bb130343(VS.80).aspx)

## Checkout, Get, and Lock
* **How to synchronize your computer with TFS**
* **How to prepare a file for editing**

### How to Synchronize Your Computer with TFS
To synchronize your computer with the version control server, use the **tf** **get** command. This is a quick way of ensuring that your computer is synchronized with the rest of your team to ensure that you have the latest copy of shared work. To download all files and not just those that are out of date, run the following command from a Visual Studio 2005 command prompt window:

{{ tf get /all }}

When you use this command, any local writable files that you might have on your computer are not overwritten. If you want to overwrite local writable files to completely synchronize your computer with the server, use the /**force** switch as follows:

{{ tf get /force }}

Although this command overwrites local writable files, it does not overwrite writable files for which you also have pending edits. If you have pending edits on a file that you need to keep, check in or shelve your edits prior to re-synchronizing with the server. 

To perform the same operation from Visual Studio: 
# In Team Explorer, double-click the Source Control folder, right-click your server or team project, and then click **Get Specific Version**. 
# Select **Overwrite writable files that are not checked out** and **Force get of file versions already in workspace**. 
# In the **Type** drop-down list, ensure that **Latest Version** is selected, and then click **Get**.

If you want to completely synchronize your computer with the version control server, do not use the **Get Latest Version** option available in Visual Studio. Because this command only downloads those files that are not already in your workspace and does not overwrite writable files that you have checked out in your local directory, your computer remains out of synchronization with the server. 

#### Additional Resources
* For more information about the **get** command, see “Get Command” at [http://msdn2.microsoft.com/pt-br/library/fx7sdeyf(VS.80).aspx](http://msdn2.microsoft.com/pt-br/library/fx7sdeyf(VS.80).aspx)

### How to Prepare a File for Editing
In order to prepare a file for editing you must first get the latest version from Team Foundation Server source control and then check it out for editing.

**To prepare a file for editing**
# In Source Control Explorer, select the file, right-click and then click **Get Latest Version**. This downloads a read-only copy of the latest version of the file into the workspace on your computer. 
# Right-click the file and then click **Check Out for Edit**. 
# Choose your required lock type. Select **None** to allow other users to check the file in and out during the time period when you are working on the file. This type of shared checkout is generally recommended because most conflicts that might arise can be resolved automatically. 

**Note:** The **get latest version** operation does not check out the file, and the **check out for edit** operation does not perform a **get**. You need to perform both steps individually. This behavior is different from Microsoft Visual SourceSafe behavior. 

When selecting your lock type, consider the following:
* A shared checkout (**None**) avoids introducing potential bottlenecks into your development process by preventing someone else from working in the same file. 
* You should only lock a file while editing it if you are concerned that there will be a conflict resulting in a complicated manual merge operation. 
* Select the **Check Out** lock type to prevent other users from checking out and checking in the file. This option prevents other people from editing the file, which could represent a potential bottleneck in your development process. This option ensures that you can apply your changes back to the source control database without the possibility of other changes having been made to the file by other users. 
* Select the **Check In** lock type to allow other users to check out the file while preventing them from checking it in. Again, this option ensures that you will be able to check in your edits without conflicts. 

#### Additional Resources
* For more information about the **checkout** command, see “Checkout and Edit Commands” at [http://msdn2.microsoft.com/pt-br/library/1yft8zkw(VS.80).aspx](http://msdn2.microsoft.com/pt-br/library/1yft8zkw(VS.80).aspx)

## Code Sharing
* **How to share code**
* **How to manage shared binaries**

### How to Share Code
If you have source code that is used by multiple team projects, you can either manage the source code within the team project of the owning team or create a team project specifically for the shared source code. 

Teams consuming shared source code have the following two options:
# Reference the code from a shared location.
# Branch the shared code.

**1. Reference the code from a shared location.**
In this case, the projects consuming the shared code can simply map the source from the shared location into their workspaces on the client machine. This creates a configuration that unifies the source from the shared location with the projects on the client-side. 

The advantage of this approach is that changes to shared source are picked up every time the latest source is retrieved into the workspace. For example, consider that you have two team projects named Client and Shared Code, where Shared Code is the location of the shared source. To reference the code from a shared location, these projects will share a common path on the client’s hard drive as shown below: 
* c:\TestProject\Client 
* c:\TestProject\Shared Code
Both projects will have workspace mappings to those local hard drive paths. 
||**Source control folder**	||**Local folder** ||
||$/Client	||c:\TestProject\Client||
||$/Shared Code	||c:\TestProject\Shared Code||

For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)
**2. Branch the shared code.**
In this case, the projects consuming the shared code can branch the source from the shared location into their respective team projects. This creates a configuration that unifies the source from the shared location with the projects on the server-side. 

The difference is that changes to the shared source are picked up as part of a merge process between the branches. This makes the decision to pick up changes in the shared source much more explicit. 

For example, consider that you have two team projects named Client and Shared Code, where Shared Code is the location of the shared source. Use the following steps to branch the code from the shared location:
# In Source Control Explorer, right-click the root folder of Shared Code.
# Select the **Branch** option.
# In the **Branch** dialog box, set the **Target** to the root folder of the Client team project, and then click **OK**.
# After the branch operation completes, do not forget to check in the branched source code. 

#### Additional Resources
* For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about project references, see “Project References” at  [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)

### How to Manage Shared Binaries
Managing shared binaries is similar to managing shared source: you must decide where you want to store the binaries and how you want your team to access the binaries.

The following options are available for storing the binaries:
* If the shared binaries are clearly owned by a particular team, store the binaries in their team project.
* If the shared binaries have no clear ownership, create a team project specifically for the shared binaries.

The following options are available for using the binaries in another project:
* Shared binaries are usually updated only periodically. If this is the case, branch from the shared location into the consuming team project. When the binaries change, you can execute a merge to get the latest version.
* If you need to stay synchronized with the shared binaries at all times, map the source from the shared location into a local workspace on the client machines.

**To branch shared binaries into your project**
# In Source Control Explorer, right-click the root folder of Shared Binaries.
# Select the **Branch** option.
# In the **Branch** dialog box, set the **Target** to the root folder of the Client team project, and then click **OK**.
# After the branch operation has completed, do not forget to check in the branched source code. 

Whether you use workspace mapping or branching, you should se naming conventions that make it clear where the shared binary location is in your project; for example:
* **Main**
	* **Source** – Contains code for this project
	* **Lib** – Contains shared binaries

#### Additional Resources
* For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about project references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)

## Dependencies
* **How to manage Web service dependencies** 
* **How to manage database dependencies**

### How to Manage Web Service Dependencies
Generally, the Web service Uniform Resource Locator (URL) reference in production is different from that for the development and test environments. To facilitate management of each of these Web service URL references, the URL value should be specified in a user configuration file that can be changed by individual developers and testers without impacting the main App.config file. To do this, you set the **URL Behavior** property of your Web service reference to **Dynamic**.**** Store and reference the Web service URL from a user configuration file.

By default, Visual Studio sets the value of this property to **Dynamic** when you add a Web reference. 

**To verify that this value is still set to Dynamic**
# In Solution Explorer, expand the list of Web references. 
# Select each Web reference in the list.
# For each Web reference, check that the value of the **URL Behavior** property is set to **Dynamic**.

**Specify a Web Service URL in a user configuration file** 
When you first add a Web reference, the App.config file looks like the following:
{{
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, 
               System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name=" SomeService.Properties.Settings" type="System.Configuration.ClientSettingsSection,
               System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
        </sectionGroup>
    </configSections>
    <applicationSettings>
        <YourProject.Properties.Settings>
            <setting name="SomeService_ localhost _Service" serializeAs="String">
                <value>http://localhost/someservice/Service.asmx</value>
            </setting>
        </ YourProject.Properties.Settings>
    </applicationSettings>
</configuration>
}}
This file has a new configuration section that contains the address of the Web service that Visual Studio found when generating this proxy. 

**To create a User.config file**
* In Solution Explorer, right-click the project that contains the Web service reference, point to **Add**, and then click **New Item**.
* Select **Application Configuration File**, change the name to **User.config**, and then click **Add**.
* Copy the _<YourProject.Properties.Settings>_ element setting from your application configuration file (App.config) to the User.config file. This file should contain only the element for which the runtime is redirected. Delete the <?xml> directive and the <configuration> element if present, as shown in the following example:
{{
<YourProject.Properties.Settings>
    <setting name="SomeService_localhost_Service" serializeAs="String">
       <value>http://localhost/someservice/Service.asmx</value>
    </setting>
</YourProject.Properties.Settings>
}}
* In Solution Explorer, right-click the User.config file, click **Properties**, and then set the **Copy To Output Directory** property to **Copy if newer**.

Individual developers should set their User.config file to reference the appropriate Web service URL reference. 

**To update the App.config file to reference User.config file when accessing the Web service URL**
* Add a **configSource**=**"user.config"** attribute to the _<YourProject.Properties.Settings_> element of your main application configuration file. 
This silently redirects the runtime to the named user configuration file when it accesses information from this section.  
* Delete the content from the _<YourProject.Properties.Settings>_ element. 

Your App.config should now look like the following:
{{
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, 
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="SomeService.Properties.Settings" type="System.Configuration.ClientSettingsSection,
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
        </sectionGroup>
    </configSections>
  <applicationSettings>
    <YourProject.Properties.Settings  configSource="user.config">
    </YourProject.Properties.Settings>
   </applicationSettings>
</configuration>
}}
In the preceding example, _YourProject_ is the name of the project that contains the Web service reference. Make sure that the _<SomeService.Properties.Service>_ element is empty in the App.config file. 

**Important:**
* Do not add your User.config file to source control. By not doing so, each developer (and the test team) can explicitly bind to specific URLs by using his or her own User.config files. To prevent this, clear the User.config file check box when you first check in the file. You can then right-click the file in Solution Explorer and select the **Undo Pending Changes** option to ensure that the file is not subject to source control.
* Source control may contain other User.config files; for example, for testing and production. These files should be managed by the users responsible for managing the testing and production environments. These test and production User.config files should not be stored as part of the Web service projects but should be in different areas of the source control system.
* Store a global User.config file in source control. This could either contain only the root element (no <setting> element), or it could specify the default location of the Web service. The User.config file must be present for the configuration system to work.
 
It is important to understand that the User.config file must be present if you are using this mechanism. Some team member must be responsible for ensuring that the environment is correct when creating builds for production releases and for any test environments. As part of this build step, the appropriate User.confg file must be retrieved from the source control system and copied into the correct location in order for MSBuild to be able to find it.

#### Additional Resources
* For more information, see “Web Projects and Source Control Integration in Visual Studio .NET” at [http://msdn2.microsoft.com/en-US/library/aa290068(VS.71).aspx](http://msdn2.microsoft.com/en-US/library/aa290068(VS.71).aspx)
* For more information about the **ApplicationSettingsGroup** class, see “ApplicationSettingsGroup Class” at [http://msdn2.microsoft.com/en-us/library/system.configuration.applicationsettingsgroup.aspx](http://msdn2.microsoft.com/en-us/library/system.configuration.applicationsettingsgroup.aspx)

### How to Manage Database Dependencies
The following procedure explains how to store and then reference a database connection string within a user configuration file.

**To use a user configuration file to store database connection strings**
* Add a **configSource="user.config"** attribute to the <connectionStrings> element of your main application configuration file as follows: 
{{
<configuration>
   <connectionStrings configSource=”user.config”/>
</configuration>
}}  
* To override the main application configuration file, create a User.config file (located in the same folder as the application configuration file), and then add a similar <connectionStrings> entry to the file. 
Notice that the following connection string references a local database: 
{{
<connectionStrings>
      <add name="DBConnStr"
     connectionString="server=localhost;Integrated Security=SSPI;database=Accounts"/>
   </connectionStrings>
</configuration>
}}
* Within your project, use the following code to obtain the connection string from the user configuration file. 
This code uses the static **ConnectionStrings** property of the **System.Configuration.ConfigurationManager** class. In the Win Form application, you must add a reference to **System.Configuration.dll** explicitly. 
{{
using System.Configuration;
private string GetDBaseConnectionString()
{
  return ConfigurationManager.ConnectionStrings["DBConnStr"](_DBConnStr_).ConnectionString;
}
}}
* Ensure that the User.config file is deployed along with the application code. To do so, in Solution Explorer, right-click the User.config file, click **Properties**,**** and then**** in the Properties pane, set the **Copy To Output Directory** property to **Copy if newer**.

Do not add the User.config file to source control. By not doing so, each developer (and the test team) can explicitly specify the connection string through his or her own User.config file. Source control might contain other User.config files; for example, for testing and production. These files should be managed by the users responsible for managing the testing and production environments. These test and production User.config files should not be stored as part of the database projects but should be stored in different areas of the source control system.

In source control you should have a User.config file for each of the environments that you use, such as production and test. These configuration files should specify the connection string for the database. The User.config file must be present for the configuration system to work.
 
**Tip:** By default, the user configuration file is automatically added to source control when you add the solution. To prevent this, when you first check in the files, clear the User.config file check box. You can then right-click the file in Solution Explorer and select **Undo Pending Changes** to ensure that the file never comes under source control.

It is important to understand that the User.config file must be present if you are using this mechanism. Some team member will need to be responsible for ensuring that the environment is correct when creating builds for production releases and for any test environments. As part of this build step, the appropriate User.confg file will need to be retrieved from the source control system and copied into the correct location in order for MSBuild to be able to find it.

#### Additional Resources
* For more information about using a configuration file to define a data source, see “Walkthrough: Using a Configuration File to Define a Data Source” at [http://msdn2.microsoft.com/en-us/library/ms243192(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms243192(VS.80).aspx)
* For more information about the **configSource** attribute, see “SectionInformation.ConfigSource Property” at [http://msdn2.microsoft.com/en-us/library/system.configuration.sectioninformation.configsource.aspx](http://msdn2.microsoft.com/en-us/library/system.configuration.sectioninformation.configsource.aspx)

## Distributed/Remote Development
* **How to access TFS over the Internet**
* **How to optimize TFS Version Control proxy performance**

### How to Access TFS over the Internet
You can choose from one of the following three solutions to provide access to TFS over the Internet:
* **Use a VPN connection.** You can provide access to TFS over a virtual private network (VPN).
* **Publish your TFS through a reverse proxy.** You can provide access to TFS through a reverse proxy such as Microsoft Internet Security and Acceleration (ISA) Server.
* **Locate your TFS in the extranet (“hosted scenario”).** You can host your TFS server on an extranet.

If you are supporting remote users with VPN access, use the VPN solution. This is the easiest solution to enable, provides well-understood security, allows remote access to all TFS features, and allows you to use the TFS Proxy to improve performance. In this solution Your TFS sits inside the internal network, and external users access it over a VPN. Internal users access a TFS directly

If you are supporting remote users without VPN access or without access to the domain, use the reverse proxy scenario. This solution is more difficult to set up, but it enables remote users to access an internally located TFS without the need for VPN. In this solution your TFS sits inside the internal network, and one or more reverse proxy machines, such as ISA Server, bring in client requests from the Internet to your TFS.

If you are supporting a set of remote users who will be using a TFS installation dedicated to their use, such as a community development site, use the extranet scenario. This solution gives you the most separation between the remote users and your internal network resources. In this solution only external clients access your TFS, and it is located outside of the firewall on an extranet

If you are supporting an office with multiple clients connecting to a remote Team Foundation Server, you should install and configure Team Foundation Server Proxy in the remote office. This improves performance by caching source control files on the remote office’s proxy server.

If you are supporting a single client connecting to a remote TFS, configure the client to connect directly to the TFS.

#### Additional Resources
* To learn more about TFS remote access scenarios, see “Ch 17 - Providing Internet Access to Team Foundation Server” in this guide
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)
* For more information about examining TFS proxy performance, see “How to: Examine Cache Performance for Team Foundation Server Proxy” at [http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx)

### How to optimize TFS Version Control proxy performance
At your remote location, install and configure Team Foundation Server Proxy. This improves performance by caching source control files in the remote office’s proxy. 

To configure and optimizing proxy performance:
# Make sure that caching is enabled, and monitor the performance of your cache. Monitor the performance counters (installed by default) and event logs (for errors/warnings) on your proxy server on a periodic basis, to see how your proxy is performing. **Note:** The TFS proxy saves cache performance statistics to an XML file named ProxyStatistics.xml; you can change the interval for saving these statistics. The ProxyStatistics.xml file is located in the App_Data folder in the proxy installation directory.
# Run a scheduled task to retrieve the latest files to the proxy server on a periodic basis. This helps to ensure that the latest versions of the files are available in the proxy cache, and to ensure that subsequent client requests for these files result in a cache hit.
# If you know that large files are going to be downloaded over a low-bandwidth (< 3 megabits per second [Mbps](Mbps)) network, set the **executionTimeout** configuration to an appropriate value in Web.config. The default value is one hour <httpRuntime executionTimeout="3600"/>.

#### Additional Resources
* To learn more about TFS remote access scenarios, see “Ch 17 - Providing Internet Access to Team Foundation Server” in this guide
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)
* For more information about examining TFS proxy performance, see [http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx)
* To learn more about the TFS Proxy File Cache Server, see the MSDN Webcast at [http://msevents.microsoft.com/CUI/WebCastEventDetails.aspx?culture=en-US&EventID=1032291120&CountryCode=US](http://msevents.microsoft.com/CUI/WebCastEventDetails.aspx?culture=en-US&EventID=1032291120&CountryCode=US)

## Migration
* **How to migrate your source from Visual SourceSafe**
* **How to migrate your source from other version-control systems**

### How to Migrate Your Source from Visual SourceSafe
To migrate your source from VSS, perform the following steps. 
**Note:** To perform these steps, you must be a member of the Team Foundation Administrators group.

**1. Prepare VSS.** Prepare to migrate by backing up your VSS database, ensuring that files are checked in and running the Visual SourceSafe Analyze tool to identify and resolve data integrity issues in your existing database.

**2. Analyze your projects.** Use the converter command-line tool (VSSConverter.exe), passing the analyze command switch together with the name of a settings XML file as follows 

**VSSConverter analyze conversionsettings.xml**

The following is a sample XML settings file:
{{
   <?xml version="1.0" encoding="utf-8"?>
   <SourceControlConverter>
      <ConverterSpecificSetting>
            <Source name="VSS">
                  <VSSDatabase name="c:\VSSDatabase"></VSSDatabase>
            </Source>
            <ProjectMap>
            <Project Source="$/MyFirstProject"></Project>
            <Project Source="$/MySecondProject"></Project>
            </ProjectMap>
      </ConverterSpecificSetting>
   </SourceControlConverter>
}}
The settings file contains the name of the VSSDatabase. You set the **name** attribute to point to the folder that contains your source safe .ini file. The Project elements define the path to the projects you want to convert within your VSS database. To migrate an entire VSS database, use <Project Source="$/"></Project>.

The VssConverter.exe **analyze** command also generates a usermap.xml file. By adding mappings to this file, you can change the names associated with version history and so on from VSS login names to your TSF Windows login names.

**3. Migrate your projects.** Choose the folders you want to migrate and then use VSSConverter.exe with the **migrate** argument as follows: 

VSSConverter migrate conversionsettings.xml

You again pass the configuration settings XML file, but with two important additions as follows:
{{
   <?xml version="1.0" encoding="utf-8"?>
   <SourceControlConverter>
      <ConverterSpecificSetting>
            <Source name="VSS">
                  <VSSDatabase name="c:\VSSDatabase"></VSSDatabase>
            </Source>
            <ProjectMap>
              <Project Source="$/MyFirstProject" Destination="$/MyTeam_ProjectOne"></Project>
              <Project Source="$/MySecondProject" Destination="$/MyTeam_ProjectTwo"></Project>
            </ProjectMap>
      </ConverterSpecificSetting>
      <Settings>
        <TeamFoundationServer name="YourTFSServerName" port="PortNumber" protocol="http"></TeamFoundationServer>
      </Settings>
   </SourceControlConverter>
}}
Notice the addition of the **Destination** attribute on the <Project> elements. This attribute points to your team project in TFS (which you must have previously created). Also notice the addition of the <Settings> element that contains connection details for your TFS application tier. 

#### Additional Resources
* For more information about how to prepare for migration, see “Walkthrough: Preparing to Migrate from Visual SourceSafe to Team Foundation” at [http://msdn2.microsoft.com/en-us/library/ms181246(en-us,vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181246(en-us,vs.80).aspx)
* For more information about how to perform the migration, see “Walkthrough: Migrating from Visual SourceSafe to Team Foundation” at [http://msdn2.microsoft.com/en-us/library/ms181247(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181247(VS.80).aspx)
* For more information about the limitations of the Visual SourceSafe converter, see “Visual SourceSafe Converter Limitations” at [http://msdn2.microsoft.com/en-us/library/ms252491(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252491(VS.80).aspx)

### How to Migrate Your Source from other Version-Control Systems
You can manually export files from the version-control system you are migrating from and then import them into Team Foundation Server Version Control. If you want to preserve file history or other attributes from the version-control system you are migrating from, you can use the Team Foundation Server Version Control object model to write your own migration tool.

Microsoft is currently working on a ClearCase converter. When this converter is ready, it will be announced on the TFS Migration blog at [http://blogs.msdn.com/tfs_migration](http://blogs.msdn.com/tfs_migration)

ComponentSoftware has created a converter that is compatible with GNU RCS, CS-RCS, GNU CVS, Subversion (SVN), and Visual SourceSafe (VSS).

#### Additional Resources
* To download the Visual Studio Team Foundation Server SDK, go to [http://go.microsoft.com/fwlink/?linkid=68586](http://go.microsoft.com/fwlink/?linkid=68586)
* To learn more about Team Foundation Version Control extensibility, see “Walkthru: The Version Control Object Model” at [http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx)
* For more information about the ComponentSoftware converter, see the ComponentSoftware Web site at [http://www.componentsoftware.com/Products/Converter/](http://www.componentsoftware.com/Products/Converter/)

## Project/Workspace Management
* **How to choose one team project versus multiple team projects** 
* **How to organize your source tree**
* **How to define workspace mappings**
* **How to use workspaces to isolate code changes on your computer**

### How to Choose One Team Project vs. Multiple Team Projects
To plan your project structure, evaluate common project organization strategies and choose the one that best fits your organization’s size, server constraints, and process workflow. Projects are intended to represent the largest unit of work possible in your organization. You should preferably choose a single project versus creating multiple projects. Use multiple projects when there is strong reason for doing so; for example, the team changes, or there is significant change from one release to another and you do not want to carry the unwanted work items (bugs, etc.) forward, or there is change in the process template, and so on.

The main advantages of creating a single project versus multiple projects are that it simplifies the moving of requirements, features, scenarios, and bugs between releases.

The most important decision points are:
* Do you want to maintain work items and other assets from release to release? If so, choose to keep all releases in the same project. 
* Do you want to create a new process and work item structure from scratch when you move to a new release? If so, choose to create a new project for each release. 

Common project structures include:
* **One project per application.** Use a single project to contain all versions of your application. Create one branch per release within that project.
	* **Reasons to use this structure:** Makes it easy to carry forward code, work items and other assets.
	* **Reasons not to use this structure:**
		* Releases in parallel are forced to share work items’ schema, check-in policies, and process guidance.  
		* Reporting is more difficult; because reports default to the entire project, you must add filtering by release.
		* If you have hundreds of applications, each in its own project, you may run up against TFS scalability limits. 
		* You will accumulate ‘baggage’ over multiple releases. The easiest way to clean this up is to create a new project and branch the code you want to carry forward into that project.
* **One project per release.** Create a new project for each version of your application.
	* **Reasons to use this structure:**
		* It works well if you want to start with a clean project after every release.
		* The old project can be used for maintenance and handed off to a separate sustained engineering team.
		* It is easy to move source from one project to another.
	* **Reasons not to use this structure:**
		* It is difficult to move work items and TFS assets from one project to another. Work items can only be copied one at a time to another project. If you want to move sets of items, you will need to do so manually or write your own utility.
		* If you are managing hundreds of projects, you may run up against TFS scalability limits.

Keep the following considerations in mind when choosing your strategy:
* Choose a structure you can live with in the long term because restructuring existing team projects can be difficult.
* Source can be easily shared among team projects:
	* Branch source from one project to another.
	* Map source from another project into your workspace.
* Team Foundation Server can scale to ~500 projects using the Microsoft Solution Framework (MSF) for Agile Software Development Process (MS Agile) or 250 projects using the MSF CMMI process. If you create your own process or customize an existing process, keep in mind that the work item schema has the greatest impact on server scalability. A complex schema will result in a server capable of supporting fewer projects. 

#### Additional Resources
* For more information about project strategy, see Eric Lee’s blog post “When to use Team Projects” at [http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx](http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx)

### How to Organize Your Source Tree
Your source tree structure consists of a combination of folder structure, file structure, and branch structure. Within your main branch, the following folder and file structure has been proven to work for teams of various sizes:
* **Main** – Container for all assets you need in order o ship the product
	* **Source** – Container for everything you need to build
		* **Code** - Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** - Container for unit tests
		* **Lib** - Container for binary dependencies
	* **Docs** – Container for documentation that ships with your product 
	* **Installer** – Container for installer source code and binaries 
	* **Tests** – Container for test team tests 

Any branches that you create off of the Main branch will copy this folder and file structure into the new branch; for example:
* **Development** – Development branch
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
* **Main** – Integration branch
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
	* **Docs** – Container for documentation that ships with your product 
	* **Installer** – Container for installer source code and binaries 
	* **Tests** – Container for test team tests

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)

### How to Define Workspace Mappings
Define a workspace mapping to map source control files and folder on the server to your local drive. 

**To create a workspace mapping for a project that is not yet on your hard drive**
# In Source Control Explorer, select the root source folder.
# Right-click and select **Get Latest Version**.
# Choose the local folder to which you want to map the workspace.

**To modify a workspace mapping for a project that is already on your hard drive**
# Select **File->Source Control->Workspaces**.
# Use the **Manage Workspaces** dialog box to add, remove, or edit existing workspaces.

**To view an existing workspace mapping**
# In Source Control Explorer, select a source folder. 
# Right-click and then click **Properties**.
The workspace mapping to your local drive appears in the **Local Name** field.

Consider the following best practices for creating workspace mappings:
* **Create mappings at the team project root level.** For new team projects, map your team project root ($/MyTeamProject) to a folder with the same name on your local drive; for example, C:\TeamProjects. Because mappings are recursive, your entire local folder structure is created automatically and will be exactly the same as the structure in source control.
* **On shared computers, use a unique local folder path.** Two users of a single computer cannot share the same workspace mapping. For example, you and a colleague cannot map the same team project ($/MyTeamProject) to the same folder on the local computer. Instead, create mappings beneath My Documents (although this leads to long location paths) or establish a team folder-naming convention on the local computer (e.g., C:\TeamProjects\User1, C:\TeampProjects\User2 etc).
* **You might not need the entire tree.** To improve performance and reduce disk size requirements, only map the files you need for your development project. In general, you will only need the files and projects associated with the solution on which you will work.  
* **Avoid using workspace mapping to support cross-project dependencies.** In general, you should avoid dependencies that cross team projects and try to have all the related/dependent solutions/projects under same team project. This reduces the need for build script customization. If you have a dependency, use project references to define the dependency, or branch the dependency from a shared project into your project. You should avoid file references because they are more difficult to manage. The exception is when the dependent project is developed in parallel and you need real-time changes. In this case, you can consider the **using workspace** mapping. You can still consider branching to create a buffer of isolation, if the dependent code is causing too many breaking changes.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx)

### How to use Workspaces to Isolate Code Changes on Your Computer
As a developer, you can create two workspaces, one containing references to files and folders being worked on by the rest of the team, and another containing files and folders that you want to isolate. You might want to isolate these files in order to evolve specific files in parallel with work that is happening elsewhere. For instance, this can be used to work on risky pending changes, or to conduct a code review.

**To create a secondary workspace**
# In Source Control Explorer, click the **Workspace** drop-down list and then click **Workspaces**.
# In the **Manage Workspaces** dialog box, click **Add**.
# In the **Add** **Workspace** dialog box, enter a new workspace name such as **MyIsolatedWork** and provide a comment to serve as a future reminder about the purpose of the workspace.
# In the **Working** **folders** list, set the workplace status to **Active**, identify the source control folder to be included in the workspace (this can be the team project root folder or any subfolder), and then specify a local folder path on your own computer to contain the files from the workspace. 
# Click **OK** and then click **Close** to create the isolated workspace.

**To retrieve the latest set of source to begin work in your isolated workspace**
# In Source Control Explorer, make sure that your isolated workspace name is selected in the **Workspace** drop-down list.
# Select your team project root folder (or a subfolder if you only need part of the source tree), right-click, and then click **Get Latest Version**. 
This copies the folder structure and latest file set from the source control server to the local directory on your computer that you mapped to the new workspace.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx)
 
## Security
* **How to secure the channel between a developer workstation and TFS** 

### How to Secure the Channel Between a Developer Workstation and TFS_
To secure the channel between a developer workstation and TFS, you can configure your TFS to use HTTPS and Secure Sockets Layer (SSL) encryption. You can configure your TFS to use only HTTPS and SSL while disallowing HTTP connections. In order to do this, you must first configure TFS to allow HTTPS and SSL, and then perform the additional steps to require HTTPS and SSL.

Using HTTPS and SSL encrypts the network traffic between TFS and the Team Foundation clients that request access to Team Foundation Server’s Web resources, including team project portals, reports, and work items. 

#### Additional Resources
* For more information, see “Securing Team Foundation Server with HTTPS and Secure Sockets Layer (SSL)”at [http://msdn2.microsoft.com/en-us/library/aa395265(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa395265(VS.80).aspx)
* For more information on how to set up TFS with Secure Socket Layer (SSL), see “Walkthrough: Setting up Team Foundation Server with Secure Sockets Layer (SSL)” at  [http://msdn2.microsoft.com/en-us/library/ms242875(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242875(VS.80).aspx)
* For more information on how to configure TFS for HTTPS and SSL only, see “How to: Configure Team Foundation Server for HTTPS and SSL Only” at [http://msdn2.microsoft.com/en-us/library/aa395285(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa395285(VS.80).aspx)

## Shelving
* **How to use shelving to back up pending work**
* **How to use shelving to share code with a team member**

### How to Use Shelving to Back Up Pending Work
To back up pending changes to the server, shelve the files that you are not yet ready to check in. This ensures that the source is uploaded to the server without checking in partially completed work that could potentially lead to build instability.

**To shelve a set of pending changes**
# View the pending changes by right-clicking your solution in Solution Explorer and then clicking **View Pending Changes**. 
# Select the files you want to shelve and then click **Shelve**. 
# Type a shelveset name and a comment that identifies the purpose of the shelveset, and then click **Shelve**. 

**To restore your work the following day**
# On the **File** menu, point to **Source Control** and then click **Unshelve**. 
# Select the required shelveset and click **Unshelve**. 
Team Foundation Server restores each shelved revision into the destination workspace as a pending change, as long as the revision does not conflict with a change that is already pending in your workspace.

#### Additional Resources	
* For more information about shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)

### How to Use Shelving to Share Code with a Team Member
To shelve source code for sharing with a team member, perform a **Get Latest** operation to synchronize your workspace with the latest server version and then build your application to ensure that it compiles. Shelve the source using Source Control Explorer. The team member to whom you have handed off the code then needs to unshelve the code. 

Shelving is useful when you have work in progress that is to be completed by another team member; in this case, you can shelve your changes to make a handoff easier. By synchronizing the latest code, you get an opportunity to incorporate changes to source files that have been made outside of your workspace. 

**To shelve folders and files from Source Control Explorer**
# In Source Control Explorer, right-click and then select **Shelve Pending Changes**.
# In the **Shelve - Source Files** dialog box, in the **Shelveset name** box, type the shelveset name; for example, **shelvetest**.
# In the **Comment** box, type **Testing my shelveset** and then click **Shelve**. 
The files and folders are copied to the source control server and are available for other team members to unshelve.

When the other team member unshelve a shelveset, TFS restores each shelved revision into the destination workspace as a pending change, as long as the revision does not conflict with a change that is already pending in the workspace. 

**To unshelve a set of pending changes**
# In Visual Studio 2005 Team System, click **File**, point to **Source Control**, and then click **Unshelve**.
# In the **Owner name** box, type the shelveset creator’s name (for example, ADVENTUREWORKS\JuanGo or simply juango) and then click **Find**.
# In the Results pane, select the shelveset you want to unshelve into your workspace, and then click **Details**. 
# If you want to delete the shelveset from the TFS source control server, clear the **Preserve shelveset on server** option.
# (Optional) Clear the **Restore work items and check-in notes** option if you do not want to have the work items and check-in notes associated with the shelveset restored. 
# When the **Details** dialog box appears, select the shelveset or shelveset items you want to unshelve into your workspace, and then click **Unshelve**.

#### Additional Resources
* For more information, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)
## Source Control Resources
* For more information about Team Foundation Server Source Control, see “Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx)