## Questions and Answers:  Source Control 
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Accessing Version Control
* _What is the MSSCCI Provider and when is it used?_
* _What other IDEs support TFS?_
* _When should I use the Team Foundation Server Power Tool?_
* _What are the most common version control extensibility scenarios?_
* _How do I work with version control from the command line?_

### Administration
* _How do I grant permissions on a file within a folder that has inherited permissions?_
* _What should I do if a developer has left the project?_
* _How do I manage interns or other developers that I do not trust to perform check-ins?_
* _How should I modify permissions after my application has shipped?_

### Branch/Label/Merge
* _When should I use labels?_
* _How do TFS labels differ from VSS labels?_
* _What is branching?_
* _When should I consider branching?_
* _What are the reasons not to branch?_
* _How do I use branching to release my application?_
* _How do I use branching to maintain my application?_
* _How do I use branching to reduce conflicts between teams?_
* _How do I use branching to reduce conflicts between features?_
* _What are the proven practices for branching and merging?_
* _What is the difference between branching and labeling?_
* _What is the "path space" branching model?_
* _How does the TFS promotion model work?_
* _How do I merge two branches?_
* _Can I merge across team projects?_
* _What is a baseless merge?_
* _What is the code promotion model?_
* _What is the difference between the logical and physical view of branches?_
* _If I use the code promotion model, how often should I merge?_

### Check-ins and Check-in Policies
* _What is a changeset?_
* _What is a check-in policy?_
* _When and how can I override a check-in policy?_
* _How do I enforce a policy?_
* _How do I use a check-in verification system?_
* _If I modify file names or delete files on the disk, does version control get out of sync?_
* _How does automatic conflict resolution work?_
* _How do I resolve conflicts manually?_
* _How do I avoid conflicts?_

### Checkout, Get, and Lock
* _How do I find out who was the last developer to modify a file?_
* _How does the get command work?_
* _What is the difference between shared and exclusive checkout?_
* _When should I use the lock command?_
* _What lock types does TFS support?_

### Distributed/Remote Development
* _How do I work offline?_
* _How do I optimize for distributed team development?_
* _What is the TFS Version Control proxy?_
* _How do I optimize TFS Version Control proxy performance?_

### Migration
* _How is TFS version control different from VSS?_
* _How is the checkout model different from VSS?_
* _How should I migrate my source from VSS to TFS?_
* _How should I migrate my source from other version-control systems?_

### Project/Workspace Management
* _How should I organize my team projects?_
* _How should I manage dependencies between projects?_
* _What is a workspace?_
* _How do I use workspaces to isolate a developer?_
* _What are the proven practices for workspace mapping?_
* _What are the proven practices for managing shared components and code?_
* _When should I create a new team project versus a new branch?_
* _How should I manage source code that is shared across multiple projects?_
* _How should I manage binaries that are shared across multiple projects?_
* _How should I organize my source tree?_

### Shelving
* _What is shelving?_
* _What is a shelveset?_
* _When would I typically use shelving?_
* _How do I use shelving to back up my work?_
* _Why would I want to unshelve a shelveset?_

## Accessing Version Control
* **What is the MSSCCI Provider and when is it used?**
* **What other IDEs support TFS?**
* **When should I use the Team Foundation Server Power Tool?**
* **What are the most common version control extensibility scenarios?**
* **How do I work with version control from the command line?**

### What is the MSSCCI Provider and when is it used?
The Microsoft® Source Code Control Interface (MSSCCI) provider is used to provide an integrated version control user experience with products that do not support the Microsoft Visual Studio® Team Explorer. For example, if you use Visual Studio 6.0, you can use the MSSCCI client or command line to interact with Microsoft Visual Studio Team System (VSTS) Team Foundation Version Control.

The following clients can work directly with Team Foundation Version Control by using the MSSCCI provider:
* Microsoft Visual Studio .NET 2003
* Microsoft Visual C® 6 Service Pack 6 (SP6)
* Microsoft Visual Basic® 6.0 SP6
* Microsoft Visual FoxPro® 9.0 SP1
* Microsoft Access 2003 SP2
* Microsoft SQL Server™ Management Studio
* Sparx Systems Enterprise Architect 6.1
* Sybase PowerBuilder 105
* Toad for SQL Server 2.0

The MSSCCI Provider behaves differently from Team Foundation Version Control in Visual Studio 2005 in the following ways:
* Checkout also performs a **GetLatest** operation.
* An exclusive check-in lock is applied at checkout.
* The **Open from Source Control** and **Save to Source Control** menu options behave similarly to Microsoft Visual SourceSafe®.

#### Additional Resources
* To read more about MSSCCI on Microsoft MSDN®, see “The Microsoft Source-Code Control Interface” at [http://msdn.microsoft.com/library/default.asp?url=/library/en-us/vcug98/html/_asug_the_microsoft_source_code_control_interface.asp](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/vcug98/html/_asug_the_microsoft_source_code_control_interface.asp)
* To learn more about the MSSCCI Provider, see “Update on the TFS MSSCCI Provider” at [http://blogs.msdn.com/bharry/archive/2006/03/24/559876.aspx](http://blogs.msdn.com/bharry/archive/2006/03/24/559876.aspx)
* The MSSCCI add-in is a TFS Power Tool developed but not officially supported by Microsoft. To download the tool from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=87E1FFBD-A484-4C3A-8776-D560AB1E6198&displaylang=en)

### What other IDEs support TFS?
Team Foundation Server can be used from any edition of Visual Studio 2005 that has Team Explorer installed. You can also run Team Explorer side-by-side with any non–Visual Studio 2005 integrated development environment (IDE) in order to work with team projects and manage work items.

The following clients have integration solutions provided by other vendors:
* Eclipse
* Linux client
* Apple Macintosh client
* Hypertext Markup Language (HTML) Web client

If you want to access Team Foundation Version Control from Eclipse IDE, Linux, or Macintosh clients, consider installing the Teamprise suite of client applications, available at [http://www.teamprise.com/](http://www.teamprise.com/)

If you want read-only access to Team Foundation Version Control from the Web, consider installing Team System Web Access, available at [http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx](http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx)

#### Additional Resources
* For more information about using Team Explorer, see “Working with Older Visual Studio Projects or Other Code Projects” at [http://msdn2.microsoft.com/en-us/library/ms242912(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms242912(vs.80).aspx)
* For more information on Teamprise, see [http://www.teamprise.com](http://www.teamprise.com)
* For more information on Team System Web Access, see [http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx](http://msdn2.microsoft.com/en-us/teamsystem/bb676728.aspx)

### When should I use the Team Foundation Server Power Tool?
The Team Foundation Power Tool (TFPT) provides version-control functionality that is not available from the Visual Studio 2005 user interface (UI). For example, you can use TFPT to help support working offline, or to perform rollback operations to undo check-ins of a changeset. Consider using TFPT if you need to perform any of the following operations:
* **Unshelve** – The **unshelve** operation that is supported by TFS does not allow shelved changes and local changes to be merged together. When you use TFPT to unshelve a change from a changeset, if an item in your local workspace has a pending change that is an edit, and the shelved change is also an edit, then TFPT can merge the changes by performing a three-way merge.
* **Roll back** – The ability to undo a check-in of a changeset is not directly supported by TFS. By using the TFPT **rollback** command, you can attempt to undo any changes made in a specified changeset. Not all changes can be rolled back, but the rollback works for most scenarios.
* **Work offline** – The TFPT online tool allows you to work without a server connection for a period of time by providing functionality that informs the server about changes you make to your local workspace.
* **Get a changeset** – The TFPT **GetCS** command enables you to get all the items listed in a changeset based on the given changeset version. This is useful if a colleague has checked in a change that you need to have in your workspace, but you cannot update your entire workspace to the latest version.
* **Remove pending edits** – The TFPT **UU** (Undo Unchanged) command removes pending edits from files that have not actually been edited. This is useful in a scenario where you check out a large number of files for edit, but only actually make changes to a small number of the files. You can back out your edits on the unchanged files by running the TFPT **UU** command, which compares hashes of the files in the local workspace to hashes on the server in order to determine whether the file has actually been edited.

You run each of these commands from the command line by using Tfpt.exe. 

#### Additional Resources
* To download TFPT, go to [http://www.microsoft.com/downloads/details.aspx?FamilyID=7324c3db-658d-441b-8522-689c557d0a79&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=7324c3db-658d-441b-8522-689c557d0a79&DisplayLang=en)
* To view a forum discussing TFPT, go to [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1)

### What are the most common version control extensibility scenarios?
The most common version control extensibility scenario is customizing a check-in policy in order to enforce standards at check-in time. To create custom policy plug-ins that appear in the **Add Checkin Policy** dialog box, use the extensibility features provided in the Visual Studio Team Foundation Server Software Development Kit (SDK). You can download the TFS SDK from [http://go.microsoft.com/fwlink/?linkid=68586](http://go.microsoft.com/fwlink/?linkid=68586)

Although not as common, it is also possible to write an integration layer to allow a non–Visual Studio 2005 client to work with Team Foundation Version Control.

#### Additional Resources
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx)
* To see sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)
* To download the TFS SDK, go to [http://go.microsoft.com/fwlink/?linkid=68586](http://go.microsoft.com/fwlink/?linkid=68586)
* To learn more about Team Foundation Version Control extensibility, see “Walkthru: The Version Control Object Model” at [http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx)

### How do I work with version control from the command line?
Team Foundation Server provides the TF command line tool (Tf.exe) to enable you to perform source control operations. For example, you can use the command line to schedule operations by using the Microsoft Windows® Task Scheduler. 

To ensure that the appropriate path and other environment variables are set up, run the tool from the Visual Studio 2005 Command Prompt window, or run the Vsvars32 batch file, which is normally located in _DriveLetter_:\Program Files\Microsoft Visual Studio 8\Common7\Tools. The command line supports most source control commands, including **Checkin**, **Checkout**, **Get**, **History**, **Shelve**, **Branch**, **Merge**, **Label**, **Status**, **Undelete**, and **Undo**. 

The following are common operations you might want to execute from the command line:
* Synchronize files from the server to your local machine – **tf get**
* Add a file to the server – **tf add**
* Check out a file for editing – **tf checkout**
* Check in pending changes – **tf checkin**
* Retrieve a particular changeset from the server – **tf get /version**

The following operations can only be performed from the command line:
	* Delete another user’s workspace – **tf workspace /delete**
	* Undo another user’s check-in – **tf undo**
	* Unlock another user’s lock – **tf lock**
	* Define label scope – **tf label**
	* Perform a baseless merge – **tf merge**

#### Additional Resources
* For more information about working with Tf.exe commands, see “MSDN: Walkthrough: Working with Team Foundation Source Control from Command Line” at [http://msdn2.microsoft.com/en-us/library/zthc5x3f.aspx](http://msdn2.microsoft.com/en-us/library/zthc5x3f.aspx)
* For more information about commands that are only available from the command line, see “Operations Available Only From the Command-Line (Team Foundation Source Control)” at [http://msdn2.microsoft.com/en-us/library/ms194957(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194957(VS.80).aspx)

## Administration
* **How do I grant permissions on a file within a folder that has inherited permissions?**
* **What should I do if a developer has left the project?**
* **How do I manage interns or other developers that I do not trust to perform check-ins?**
* **How should I modify permissions after my application has shipped?**

### How do I grant permissions on a file within a folder that has inherited permissions?
You set permissions by right-clicking the folder or file in Source Control Explorer, clicking **Properties**, and then on the **Security** tab, selecting the user or group for which you want to change permissions, and editing the permissions listed under **Permissions**. You can also set these permissions on the command line by using the **Permission** command of the TF command-line utility.

Team Foundation Source Control allows you to grant access-control permissions to Windows Groups, Windows Users, and Team Foundation Groups. Permissions can be inherited from the containing folder, or you can declare permissions explicitly.

Permission settings are in the form of either Allow or Deny. Deny always overrides Grant, even if Deny is inherited and Grant is explicitly defined. The inherited permissions are combined with the explicit permissions to determine a user’s or group’s effective permissions on an item. Because Deny always overrides Allow, you can keep inherit turned on and deny check-in, for example.

Be careful when turning inheritance off; for example, you should first set the explicit permissions required and make sure to assign your own account-specific permissions before turning inheritance off. If you turn inheritance off without setting the desired permissions, you can lock yourself out of a file or folder and require a TFS administrator who is also an administrator on the application tier computer to fix the permissions. Application tier local administrators can never completely lock themselves out by design.

#### Additional Resources
* For more information about permissions, see “Team Foundation Server Default Groups, Permissions, and Roles” on MSDN at [http://msdn2.microsoft.com/en-us/library/ms253077.aspx](http://msdn2.microsoft.com/en-us/library/ms253077.aspx)
* For further information about permissions, see “Source Control Security Rights and Permissions” on MSDN at [http://msdn2.microsoft.com/en-us/library/ms181761.aspx](http://msdn2.microsoft.com/en-us/library/ms181761.aspx)

### What should I do if a developer has left the project?
If a developer has left your project, make sure that you delete that developer’s workspace. This operation also removes any of the developer’s pending changes and undoes any locks held by the developer.  

**Note:** You cannot undo the locks without undoing the changes if an exclusive lock has been turned on for the team project.
 
To find out which files the developer has locked out, run the following command:

**tf workspaces /owner:domain\devuser /computer:** /server:servername**

To delete the workspace and remove locks, run the following command:

**Tf workspace /delete workspacename;domain\devuser /s:servername**

#### Additional Resources
* For more information about cleaning up after a developer who has left a project, see “How to: Clean Up Files When Users Leave” at [http://msdn2.microsoft.com/en-us/library/ms194958(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194958(VS.80).aspx)
* For more information about the **Workspace** command, see “Workspace Command” at [http://msdn2.microsoft.com/en-us/library/y901w7se(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/y901w7se(VS.80).aspx)

### How do I manage interns or other developers that I do not trust to perform check-ins?
If your team includes developers that you do not yet trust, such as new hires or interns, you can deny these developers check-in permission on the source tree. Make sure that you set your desired permissions (including permissions for your own account) before turning off inheritance. Rather than check in directly, untrusted developers can make pending changes and then shelve these changes. A more experienced developer can then unshelve the changes, review them, and check them in later.

#### Additional Resources
* For more information about removing permissions, see “How to: Remove Access to Source Control Files” at [http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx)

### How should I modify permissions after my application has shipped?
When a branch is in maintenance mode?for example, after it has been shipped?you can turn off permissions inheritance to lock down the tree. After you have turned off the permissions, you can allow individual users the **pend-change** and **check-in** permissions as needed for hotfixes.

#### Additional Resources
* For more information about removing permissions, see “How to: Remove Access to Source Control Files” at [http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx)

## Branch/Label/Merge
* **When should I use labels?**
* **How do TFS labels differ from VSS labels?**
* **What is branching?**
* **When should I consider branching?**
* **What are the reasons not to branch?**
* **How do I use branching to release my application?**
* **How do I use branching to maintain my application?**
* **How do I use branching to reduce conflicts between teams?**
* **How do I use branching to reduce conflicts between features?**
* **What are the proven practices for branching and merging?**
* **What is the difference between branching and labeling?**
* **What is the "path space" branching model?**
* **How does the TFS promotion model work?**
* **How do I merge two branches?**
* **Can I merge across team projects?**
* **What is a baseless merge?**
* **What is the code promotion model?**
* **What is the difference between the logical and physical view of branches?**
* **If I use the code promotion model, how often should I merge?**

### When should I use labels?
Use labels to group a set of files and folders together for future operations. You can use labels for branching, merging, diffing, or getting files. A label provides a marker to which you can return when performing one of the above operations at a later date.

Team Foundation Build automatically labels the file versions associated with each build that it creates.

**Note:** If you are unsure whether or not you need a branch, you can label a set of files and later create a branch based on this label.

#### Additional Resources
* For more information about labels, see “Working with labels” at [http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx)
* For further information about labels, see “How to: Apply Labels” at [http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx)

### How do TFS labels differ from VSS labels?
Team Foundation Server labels differ significantly from VSS labels. Because VSS labels are “point in time” labels that you normally assign to all or part of a tree in VSS, VSS displays labels according to time sequence along with the file history. Everything that appears on the list before the labeled file is included in the label, while everything later in the list is not. 

In TFS, instead of being a single point in time, labels tie together specific versions of a set of source files. A common scenario for labels is to use them to mark daily builds. This allows you to easily retrieve the source file set corresponding to a particular build; for example, if you need to apply a fix.

#### Additional Resources
* For more information about comparing TFS and VSS labels, see “Comparing SourceSafe Labels to Team Foundation Server Labels” at [http://blogs.vertigosoftware.com/teamsystem/archive/2006/05/03/Comparing_SourceSafe_Labels_to_Team_Foundation_Server_Labels.aspx](http://blogs.vertigosoftware.com/teamsystem/archive/2006/05/03/Comparing_SourceSafe_Labels_to_Team_Foundation_Server_Labels.aspx)

### What is branching?
_Branching_ (also known as forking) is the act of splitting a collection of files into separate development paths. Team Foundation Server supports branching and sophisticated merging that allows you to join together files from separate branches. For example, you can use branching to isolate major releases of your application. After you have branched the released version of your application, you can more easily maintain it in the future. Merging allows you to selectively make fixes to both branches.

The purpose of branching and merging is to allow you to isolate concurrent streams of development. For instance, you create a branch when your team has produced a build that you want to maintain going forward. You could also choose to branch in order to isolate feature teams in a very large development organization, or to support development on multiple versions of your application at once.

Because TFS Version Control does not make separate copies of the file content when you branch, it does not consume a lot of additional space in the source control database. A branch consists of a pointer in the database to the source content in the list of deltas that modify it from the base version.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### When should I consider branching?
Branches enable multiple developers to work on the same files in isolation. Because merging incurs overhead and requires you to manage conflicts, you should not branch unless you need the file isolation that branching provides. You can label a build and branch later if needed.  

The decision whether to create a branch can be summarized as follows: will the cost of merging conflicts in real time be higher, or will the overhead cost of merging conflicts between branches be higher?

Common reasons to branch include:
* **Release** – Branch for builds you want to maintain, or branch for multiple releases in parallel.
* **Maintenance** – Branch to maintain a previously released build.
* **Feature** – Isolate work on experimental or risky features that might make the rest of the project unstable. Isolate work on interface changes that will cause instability for the rest of the project.
* **Team** – Isolate sub-teams so that they can work without being subject to breaking changes from other teams. Isolate sub-teams so they can work toward unique milestones. These are very similar to feature branches.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### What are the reasons not to branch?
Do not branch unless development team members need to work on the same set of files concurrently. If you are unsure, you can label a build and then create a branch from that labeled build at a later point. Merging branches can be costly, especially if there are significant changes between the branches being merged.

Merging requires one or more developers to execute the merge and sort out conflicts. The merged source must be thoroughly tested because it is not uncommon to make bad merge decisions that can destabilize the build.

Merging across the branch hierarchy is especially difficult and requires you to manually handle many conflicts that could otherwise be handled automatically.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How do I use branching to release my application?
Use a Release branch when you are ready to stabilize your build prior to release. 

The following is an example of what your branch structure might look like after you have created a Release branch:
* **Main** – Integration branch
	* **Source**
	* **Other asset folders**
* **Release 1** – Release branch
	* **Source**

Keep the following recommendations in mind when working with a Release branch:
* **When to branch:** When you are ready to release, integrate everything into the Main branch and then create a Release branch that can be used to stabilize the application prior to release.
* **When not to branch:** If you are using one TFS project per release, you can use the new project to continue development instead of a branch in the current project.
* **Permissions on branch:** 
* Prior to release – Read/write for all developers.
* After release – Read/write for developers working on hotfixes, read-only for everyone else.
* **Build frequency on branch:** On-demand builds.
* **Testing focus on branch:** Sign off on release.

You should use the Release branch for the targeted fixes and changes necessary in order to stabilize a build prior to release. Development of the next version of your application can occur in parallel in your main Development or Integration branch so that the new version can get the benefit of the stabilization changes you made prior to release. After a final release build has been created, you can merge the changes from the Release branch back into your main Development and Integration branches.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How do I use branching to maintain my application?
Use Maintenance branches to support previously released builds. 

The following is an example of what your branch structure might look like after you have moved a release to the Maintenance folder:
* **Main** – Integration branch
	* **Source**
	* **Other asset folders**
* **Releases** – Container for Release branches
	* **Release 1** – Maintenance branch
		* **Source**

Keep the following recommendations in mind when working with a Maintenance branch:
* **When to branch:** After you have released, support the release with a branch in the Maintenance folder.  
* **When not to branch:** If you will never need to maintain the release, you can use a label to mark the old released build and continue work in the Main branch.
* **Permissions on branch:** 
	* Read/write for developers working on hotfixes.
	* Read-only for everyone else.
* **Build frequency on branch:** On-demand builds.
* **Testing focus on branch:** Sign off on release.

You should use Maintenance branches to support an older version of your application. You might choose to merge these changes into your main Integration branch, or leave the changes specific to the Maintenance branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How do I use branching to reduce conflicts between teams?
Use Team branches to improve the integration and stabilization of breaking changes across teams. 

The following is an example of what your branch structure might look like after you have created Team branches:
* **Development -** Container for Team branches
	* **Team 1 -** Team branch
		* **Source**
	* **Team 2 -** Team branch**** 
		* **Source**
* **Main –** Integration branch
	* **Source**
	* **Other asset folders**

Keep the following recommendations in mind when working with a Release branch:
* **When to branch:** If your development teams’ work overlaps on files and components, use Team branches to isolate each team’s work. You might also choose to create Feature branches beneath the Team branches.
* **When not to branch:** If your source tree is organized by component, and you are confident that there will not be breaking interface changes or a large number of check-in conflicts across your teams, you probably do not need team branches.
* **Permissions on branch:** 
	* Read/write for developers on the team.
	* Read-only for everyone else.
* **Build frequency on branch:** Continuous Integration (CI) builds.
* **Testing focus on branch:** Feature and quick feedback testing.

Use the Team branches to allow teams to complete development tasks in parallel. This can be useful to isolate teams from breaking changes originated by other teams, or to allow teams to work toward unique milestones. All active development should occur in the Team branches and then be integrated into the Main branch. You might also want to create Feature branches beneath each team branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### How do I use branching to reduce conflicts between features?
Use Feature branches to improve the integration and stabilization of breaking changes across features. 

The following is an example of what your branch structure might look like after you have created Feature branches:
* **Development –** Container for Feature branches
	* **Feature A –** Feature branch
		* **Source**
	* **Feature B –** Feature branch
		* **Source**
	* **Feature C –** Feature branch
		* **Source**
* **Main –** Integration branch
	* **Source**
	* **Other asset folders**

Keep the following recommendations in mind when working with Release branches:
* **When to branch:** Feature teams often have source file overlap, thereby increasing the potential for build breaks and check-in conflicts. If you are experiencing these types of problems, consider feature branches for each feature to provide feature isolation. You can create these off a Main branch for small teams, or off Team branches for larger teams.
* **When not to branch:** If you are only creating CI builds, or your daily builds are already predictably stable, you might not need the extra overhead of feature branches.
* **Permissions on branch:** 
	* Read/write permissions for developers on the Feature branch.
	* Read-only for everyone else.
* **Build frequency on branch:** CI builds.
* **Testing focus on branch:** Feature and quick feedback testing.

Use Feature branches to allow each feature to be developed in parallel. Perform all active development on the Feature branches and then integrate your code into the Main branch.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at  [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### What are the proven practices for branching and merging?
When branching, consider the following guidelines:
* Structure your branch trees so that you only need to merge along the hierarchy (up and down the branch tree) rather than across the hierarchy. Branching across the hierarchy requires that you use a baseless merge, which requires more manual conflict resolution.
* The branch hierarchy is based on the branch parent and branch child, which may be different than the physical structure of the source code on disk. When planning your merges, keep the logical branch structure in mind rather than the physical structure on disk.
* Do not branch too deeply. Because there is latency involved in merging branches, a deep branching structure can mean that changes in a child branch might take a very long time to propagate to the main branch. This can negatively impact project schedules and increase the time required to fix bugs.
* Branch at a high level, and include configuration and source files.
* Allow your branching structure to evolve over time to suit changing needs.
* Do not branch unless your development team needs to work on the same set of files concurrently. If you are unsure, you can label a build and then create a branch from the labeled build at a later point. Merging branches can be costly, especially if there are significant changes between them.
* Merging requires one or more developers to execute the merge and sort out conflicts. The merged source must be thoroughly tested because it is not uncommon to make bad merge decisions that can destabilize the build.
* Merging across the branch hierarchy is especially difficult and requires you to manually handle many conflicts that could otherwise be handled automatically.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### What is the difference between branching and labeling?
Branches are designed to split a collection of files into separate development paths. You use branching to isolate two sets of file versions so that you can evolve the two paths separately. For example, you can use branches to manage and maintain older released versions of your application. You can also use branches to isolate risky code changes that span multiple developers, so that team impact is minimized. However, if you need to isolate only a single developer, use workspaces to reduce branch and merge complexity.

Labels are used to tag a file or collection of files with distinct notation so that the file or collection can be easily retrieved later. For instance, you can use labels to mark daily builds in order to ease future retrieval; for example, if you want to address an issue related to that release.

#### Additional Resources
* For more information about the **branch** command, see “Branch Command” at [http://msdn2.microsoft.com/en-us/library/d73s8b27(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/d73s8b27(VS.80).aspx)
* For more information about the **label** command, see “Label Command” at [http://msdn2.microsoft.com/en-us/library/9ew32kd1(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/9ew32kd1(VS.80).aspx)

### What is the "path space" branching model?
Branches are created within the path structure of the repository, similar to file copy operations. This is different than the pin-and-share mechanism used by Visual SourceSafe. This approach makes it easier to maintain old versions of your software, because it is simpler to merge changes from one branch to another or make changes in two branches at once.

Team Foundation Server Version Control does not make separate copies of the file content when you branch it, so it does not consume a lot of additional space in the source control database. A branch consists of a pointer in the database to the source content in the list of deltas that modify it from the base version.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at  [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)

### How does the TFS promotion model work?
A _promotion model_ is the means by which a change is propagated from one branch to another. Visual SourceSafe also allowed branching and merging, but in practice customers used pinning and sharing as a crude promotion model. Team Foundation Server Version Control uses branching and merging to support promotion modeling. You can use multiple branches to isolate specific versions of the application on which you are working. You can propagate a change by merging from files in one branch to the files in another branch.

#### Additional Resources
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* To learn more about the differences between Visual SourceSafe and Team Foundation Server Version Control, see “Visual Source Safe vs. Team Foundation Server” at [http://msmvps.com/blogs/vstsblog/archive/2005/07/02/56401.aspx](http://msmvps.com/blogs/vstsblog/archive/2005/07/02/56401.aspx)

### How do I merge two branches?
To perform a merge, you can use the merge functionality in Source Control Explorer, or you can use the **merge** command-line tool. You can merge based on changeset, label, date, or version.

You might find that your branching structure becomes deeper than one level. If this happens, keep in mind that it is only possible to merge one level at a time. For example, consider the following source tree structure:
* **Development** – Container for isolation development branches.
	* **Feature A**
		* **Source**
	* **Feature B**
		* **Source**
* **Main** – Main integration build branch
	* **Source**
	* **Other asset folders**
* **Releases**– Container for Release branches
	* **Release 1**
		* **Source**
	* **Release 2 –** Current release being locked down
		* **Source**

When the source code contained in the **Release 2** branch changes, you might want to eventually merge that change into a Feature branch; for example, to incorporate a bug fix into the latest feature code. It is not easy to merge directly from **Release 2** into **Feature B**; instead, you merge from **Release 2** into its logical parent, **Main**, and then from **Main** into its logical child **Feature B**. If you need to merge between branches that do not have a direct parent-child relationship, you need to perform a baseless merge.

#### Additional Resources
* To learn how to merge files and folders, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* To learn more about baseless merge, see the **/baseless** option in “Merge Command” at [http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx)

### Can I merge across team projects?
Yes, there is nothing special about merging across team projects. Regular merges work in this scenario. The Team Project Creation Wizard enables you to create a team project as a branch of a different project. 

#### Additional Resources
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)

### What is a baseless merge?
The **branch** command will create a relationship between two folders. You can leverage this connection to perform merges of code between the branches. Branches that are not a direct child or a direct parent of the merge target do not have this relationship. As defined in MSDN, a _baseless merge_ “performs a merge without a basis version. That is, allows the user to merge files and folders that do not have a branch/merge relationship. After a baseless merge, a merge relationship exists and future merges do not have to be baseless”.

A baseless merge will result in many more conflicts than a normal merge. However, after the first baseless merge, future merges between these branches will no longer be baseless, thus minimizing conflicts.

Baseless merges can only be created from the command line. Even after the first baseless merge, when a relationship has been created between the branches, future merges still need to be created from the command line.

#### Additional Resources
* To learn how to merge files and folders, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* To learn more about baseless merges and other merging options, see the **/baseless** option in “Merge Command” at [http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx)

### What is the code promotion model?
_Code promotion_ is a strategy that uses branches to promote code through some stabilization phases. For example, you might have a Development branch in which your team does active development, a Main branch in which your team is integrating and testing, and a Production branch that your team uses for final release stabilization.

#### Additional Resources
* For more information on branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)

### What is the difference between the logical and physical view of branches?
The _physical view_ is the hierarchy that appears within your source tree, as shown in the following example:
* $/MyTeamProject
	* **Development**
		* Source
	* **Main**
		* Source
	* **Releases**
		* **Release1**
			* Source
		* **Release2**
			* Source

Development, Main, Release1, and Release2 are branches that directly contain source code. Releases is a folder that contains multiple branches.

The _logical view_ is the hierarchy of parent and child branches as they were created. This hierarchy is not shown in the source tree but can be visualized based on how each branch was created; for example:
* **Main**
* **Development**
* **Release1**
* **Release2**

The logical view is important because merging is easiest when you do it up and down, rather than across, the logical hierarchy. If you execute a merge across the hierarchy, you must perform a baseless merge, which requires use of the command line and significantly more conflict resolution.

#### Additional Resources
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* To learn how to merge files and folders, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)
* To learn more about baseless merges, see the **/baseless** option in “Merge Command” at [http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bd6dxhfy(VS.80).aspx)

### If I use the code promotion model, how often should I merge?
Merge frequency depends on your branch structure. For example, a common branch structure is as follows:

* **Development** – Container for isolation development branches
	* **Feature A**
		* **Source**
	* **Feature B**
		* **Source**
* **Main** – Main integration build branch
	* **Source**
	* **Other asset folders**
* **Releases**– Container for Release branches
	* **Release 1**
		* **Source**
	* **Release 2 –** Release currently locked down
		* **Source**

In this case, active development is occurring in the Feature branches and you have two merge frequency decisions to make:
# How often should feature teams merge changes from the Main branch into their Feature branch?
# How often should feature teams merge their changes into the Main branch? 

The following merge frequency is a proven strategy to reduce breaking changes and reduce migration times:
## Feature teams should merge their changes into the Main branch as soon as the feature is complete.
## Feature teams should merge changes from the Main on a regular basis to ensure integration compatibility of their features when they are complete. Ideally, you should merge once per day, and not go more than two days between merges.

#### Additional Resources
* To learn how to merge files and folders, see “How to: Merge Files and Folders” at  [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx)

## Check-in and Check-in Policies
* **What is a changeset?**
* **What is a check-in policy?**
* **When and how can I override a check-in policy?**
* **How do I enforce a policy?**
* **How do I use a check-in verification system?**
* **If I modify file names or delete files on the disk, does version control get out of sync?**
* **How does automatic conflict resolution work?**
* **How do I resolve conflicts manually?**
* **How do I avoid conflicts?**

### What is a changeset?
A _changeset_ represents the set of changes associated with a check-in. All changes in the changeset are applied to TFS in an atomic fashion when you check-in the changeset. Changesets are identified by unique, sequentially increasing numbers.

You can retrieve a changeset at a later time to view details of what files changed, check-in comments, and associated work items. You can also retrieve the file versions associated with the changeset if you need to review, test, or build with the old change.

#### Additional Resources
* For more information about retrieving changesets, see “How to: Retrieve Old Versions of Files from Changesets” at [http://msdn2.microsoft.com/en-us/library/ms181416(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181416(VS.80).aspx)

### What is a check-in policy?
You can use check-in policies to enforce coding standards upon check-in. For example, you can require that each developer runs static code analysis on the code before it is checked in,.

The following check-in policies are available by default with VSTS:
* **Code Analysis** – Requires that code analysis be run before check-in.
* **Test Policy** – Requires that check-in tests be completed before check-in.
* **Work Items** – Requires that one or more work items be associated with the check-in.

You can create a custom check-in policy to perform checks that are not available by default. For example, you can disallow code patterns such as banned API calls, force the use of check-in comments, or check against your team’s style guidelines.

#### Additional Resources
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx)
* To see sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)

### When and how can I override a check-in policy?
You can override a check-in policy by selecting the **Override policy failure and continue check-in** checkbox. Any team member who has permission to check in files can override a check-in policy.

If you want to detect when a member of your team overrides check-in policy, you can use the Team Foundation Eventing Service to hook check-in events. 

#### Additional Resources
* To learn more about overriding a check-in policy, see “How to: Override a Check-in Policy” at [http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx)
* To learn more about the Team Foundation Eventing Service, see “Eventing Service” at [http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx)

### How do I enforce a policy?
Team Foundation Version Control will not prevent someone from overriding a policy. However, you can use the following steps to detect if a policy has been overridden:
* Use the Team Foundation Eventing Service (from the Team Foundation Core Services API) for hooking into check-in events.
* Write a **Notify** method that parses the details of the changeset, and then react to it if an override has occurred.

Alternatively, you can manually scan changeset history to discover policy overrides.

#### Additional Resources
* To learn how to receive an e-mail notification when a policy has been violated, see [http://blogs.infosupport.com/marcelv/archive/2005/10/18/1635.aspx](http://blogs.infosupport.com/marcelv/archive/2005/10/18/1635.aspx)

### How do I use a check-in verification system?
You can use Team Foundation Version Control check-in policies as a check-in verification system. Team Foundation Server ships with check-in policies to ensure that the following is true before a check-in can be committed:
* A work item is associated with the change.
* Unit tests have all passed.
* Static analysis has run cleanly.

You can create your own check-in requirements by creating new policy plug-ins. Your plug-in can ensure that code matches your team’s coding standards, has run build verification tests, or any other requirement that is critical to your team’s needs.

#### Additional Resources
* To learn more about creating and customizing check-in policies, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx)

### If I modify file names or delete files on the disk, does version control get out of sync?
Yes. If you accidentally delete files or folders, the TFS server still thinks you have the latest versions on your local machine. This means that the **get latest version** command will not add the deleted files back onto your disk. In this case, use the **force get** command to restore the files or folders.

If you need to rename files or delete files or folders, do so by using Source Explorer so that the server stays synchronized with your local changes.

### How does automatic conflict resolution work?
A conflict can occur as a result of a pending **change**, **merge**, or **get** operation. When you opt to resolve the conflict, you can choose to have Visual Studio resolve the conflict automatically. Automatic conflict resolution only works on non-binary files that have no overlapping changes (for example, changes applied to the same line of code). In this case, changes for both file versions are merged into a new file version.

If automatic conflict resolution does not work, you can choose to only accept changes from one of the files, or you can perform a manual merge by using the graphical compare and differencing tools provided by VSTS.

#### Additional Resources
* For more information about resolving conflicts, see “How to: Resolve Conflicts” at [http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx)

### How do I resolve conflicts manually?
To resolve merge conflicts, use the Visual Studio merge tool. If a conflict is detected during a merge, you can resolve the conflict either automatically or manually. If you choose to resolve the conflict manually, you can keep the source changes, keep the target changes, or resolve the conflict in the merge tool.

You might need to resolve conflicts when merging changes between branches, getting files into your workspace, or checking in new versions of files. There are three conflict types:
* **Version** – The file has evolved along divergent paths. This could be the result of a file edit, rename, delete, or undelete. 
* **File name collision** – Two or more items are trying to occupy the same path.
* **Local overwrite** – Only occurs during a **get** operation, if you are trying to overwrite a local, editable file.

Most conflicts can be resolved automatically; version conflicts are the only conflict type that might result in a manual merge operation. Manual merge is most common in the following scenarios:
* A file has been edited in both branches, with changes to the same lines of code.
* A baseless merge is being conducted in which the branch file relationships are not known to TFS.

The merge tool shows you the details for each conflict and allows you to choose which change you want to keep in the final merged file. You can choose to keep the source change, keep the destination change, integrate both changes, or manually modify the final version by typing directly into the file.

After resolving every conflict in the file, save the final version as a pending change to be checked into the target branch.

Be careful when merging because it is easy to make mistakes that might result in build instability. After you have finished merging, compile the resulting source and run unit tests to test for major breaks.

#### Additional Resources
* For more information about resolving conflicts, see “How to: Resolve Conflicts” at [http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181433(VS.80).aspx)

### How do I avoid conflicts?
Most conflicts can be automatically resolved by Team Foundation Version Control. The scenarios in which you are most likely to need a manual merge?and therefore are worth avoiding?are scenarios in which there are overlapping changes to the same lines of code, or where more than two developers are working on a file at the same time.

**To view pending changes**
# In Source Control Explorer, right-click the solution, project, folder, or file for which you want to see pending changes.
# Select **View Pending Changes**.

This method will show you all of the pending changes within the scope you have selected.

If you use the command line checkout tool, it will indicate which other users have checked out this file, including information about the nature of the users’ pending changes. In the following example, a file named Math.cs is checked out, and TFS provides a notification that two other users (James and Sally) are working on the file. The notification indicates exactly what type of pending change each user has in his or her local workspace (Edit and Rename) and confirms that the local version of the file (the current workspace version) is not based on the latest repository version. 
{{
c:\dev\projects\calc\src>tf edit math.cs
ExplorerScc.cs

$/MathProject/dev/calc/src/math.cs:
   opened for edit in Workspace21;contoso\james
   opened for rename in WS24;contoso\sally
   newer version exists in the repository
}}
Communicate regularly with other developers to indicate the nature of your changes to a particular file, to help avoid overlapping changes that would need to be manually merged. Coordination is a good way to make sure that two developers do not work on the same part of the code, but otherwise there is nothing wrong with having two or more people editing different parts of the same file.

#### Additional Resources
* For more information about viewing pending changes in your workspace, see “How to: View and Manage All Pending Changes in Your Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx)
* For more information about viewing pending changes in other workspaces, see “How to: View Pending Changes in Other Workspaces” at [http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx)

## Checkout, Get, and Lock
* **How do I find out who was the last developer to modify a file?**
* **How does the get command work?**
* **What is the difference between shared and exclusive checkout?**
* **When should I use the lock command?**
* **What lock types does TFS support?**

### How do I find out who was the last developer to modify a file?
You can determine who last modified a file by examining the file’s history. To do so, right-click the file in Solution Explorer and then click **View History**. This displays the History window, which shows a list of modifications and the users who made those modifications. The last developer to modify a given file is shown at the top of the list. You can also view version history for a file from the command line by using the **history** command from the tf.exe command line tool.

#### Additional Resources
* For more information about file history, see “How to: View Historical Data” at [http://msdn2.microsoft.com/en-us/library/ms181415(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181415(VS.80).aspx)

### How does the get command work?
Use the **get** command to synchronize the files on your machine with the files on the Team Foundation Server. When you perform a **get** operation, Visual Studio performs the following steps. Note that the following sequence assumes that you have installed TFS proxy in order to boost performance:
# The server determines which files are out of date based on the fact that it knows which versions are on your disk.  
# The server then tells the client what it needs to do to update its workspace. 
# The client downloads, moves, and deletes files as necessary and then notifies the server of which operations it accomplished.

A **get** operation does not mark any files for editing and by default will not overwrite any files you have checked out for editing.

#### Additional Resources
* For more information about the **get** command, see “Get Command” at [http://msdn2.microsoft.com/pt-br/library/fx7sdeyf(VS.80).aspx](http://msdn2.microsoft.com/pt-br/library/fx7sdeyf(VS.80).aspx)

### What is the difference between shared and exclusive checkout?
Team Foundation Server source control supports both shared and exclusive checkouts. 

With an _exclusive checkout_, nobody else can check out a file until you check it back into source control. This can lead to bottlenecks in the development process. 

By default, TFS also enables multiple users to check out the same source-controlled item concurrently. This is referred to as _shared checkout_. With this model, multiple developers can be working on copies of the same source file in their own workspaces. Team Foundation Server knows which version is in a given developer’s workspace, and that developer must resolve conflicts prior to check-in.

In most collaborative development environments, it is unlikely that that you will make a change in your workspace that conflicts with a pending change in another user’s workspace, or vice versa. A great majority of the workspace conflicts that do occur are resolved automatically by TFS. For conflicts that cannot be resolved automatically, you can use the **resolve** command to safely decide which change (yours or someone else’s) you want to keep. 

#### Additional Resources
* For more information about locks, see “How to: Lock and Unlock Folders or Files” at [http://msdn2.microsoft.com/en-us/library/ms181420(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181420(VS.80).aspx)

### When should I use the lock command?
Use the **lock** command to prevent other developers from checking out or checking in their changes until you unlock the file on which they are working. You should only lock a file if you are concerned that there will be a conflict resulting in a complicated manual merge operation. Because most conflicts can be resolved automatically, you should use the **lock** command sparingly, if at all.

#### Additional Resources
* For more informational about lock types, see [http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx)

### What lock types does TFS support?
Team Foundation Server provides two types of locks: check-in and checkout locks. A check-in lock is less restrictive than a checkout lock. When you apply a check-in lock, users can continue to make local changes to the item in other workspaces. The changes cannot be checked in until you explicitly remove the check-in lock from the workspace or you check in the file. 

A checkout lock is more restrictive than a check-in lock. When you apply a checkout lock to a source-controlled file or folder, users can neither check out the file for editing nor check in pre-existing pending changes. You cannot acquire a checkout lock if an item currently has any pending changes.

#### Additional Resources
* For more informational about lock types, see [http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx)

## Distributed/Remote Development
* **How do I work offline?**
* **How do I optimize for distributed team development?**
* **What is the TFS Version Control proxy?**
* **How do I optimize TFS Version Control proxy performance?**

### How do I work offline?
Team Foundation Version Control does not natively support offline working. If you want to work offline you must strictly adhere to the following workflow:
# Manually remove read-only flags.
# Edit files.
# Add or delete files.
# Run the Team Foundation Power Tool (TFPT) online command.

**Note:** You must not rename any files while you are offline.

**1. Manually remove read-only flags.**
By default, all files in the workspace that have not been checked out are marked as read-only. When you are working without a server connection, you must manually remove the read-only flag from files before editing or deleting them. To do this, right-click the file in Windows Explorer, click **Properties**, clear the **Read-only** check box, and then click **OK**. Alternatively, you can use the DOS command **attrib -r** 

**2. Edit files.**
You can now freely edit any files for which you have removed the read-only flag.

**3. Add or delete files.**
You can add files or delete files for which you have removed the read-only flag. Do not rename files, as the TFPT online tool cannot distinguish a rename from a delete paired with an add. 
**Note:** You must specify an option to the TFPT online command to get it to look for delete instances, as this is a more time-consuming operation.

**4. Run the TFPT online command.**
When you are back online, run the TFPT online command by typing **TFPT online** at the command line. This command scans your workspace for writable files and determines what changes should be pended on the server. If you have deleted any files, use the **/deletes** command-line option to scan for deleted files in your local workspace as well. The tool then displays the **Online** window from which you can choose which changes to pend into the workspace.

#### Additional Resources
* To download the TFPT online tool from MSDN, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)
* To learn more about the Team Foundation Power Tool, see “Power Tools: tfpt.exe” at  [http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx](http://blogs.msdn.com/buckh/archive/2005/11/16/493401.aspx)

### How do I optimize for distributed team development?
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
* To learn more about the TFS Proxy, see “Team Foundation Server Proxy and Source Control” on MSDN at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)
* To learn more about the TFS Proxy File Cache Server, see the MSDN Webcast at [http://msevents.microsoft.com/CUI/WebCastEventDetails.aspx?culture=en-US&EventID=1032291120&CountryCode=US](http://msevents.microsoft.com/CUI/WebCastEventDetails.aspx?culture=en-US&EventID=1032291120&CountryCode=US)

### What is the TFS Version Control proxy?
Client-server communication in TFS uses Hypertext Transfer Protocol (HTTP). The TFS Version Control proxy is installed on a server at remote locations?team locations separated by a wide-area network (WAN) connection from the TFS database?to boost performance and to avoid unnecessary roundtrips to the server. The proxy caches copies of source-controlled files in the remote location, away from the central TFS server. When a file is not in the local cache, the file is downloaded by the proxy to the local cache from TFS before returning the files to the client.

Although remote access is the most common scenario for using the proxy, you can also use it anytime you want to take load off of the main server. For instance, if your server is overloaded by many local simultaneous requests to get the latest source, you can offload this work to the proxy. Because every application tier install includes a proxy. there is generally nothing to be gained by putting a proxy in front of an AT.

#### Additional Resources
* For more information about the TFS Version Control proxy, see “Team Foundation Server Proxy and Source Control” at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx)

### How do I optimize TFS Version Control proxy performance?
Consider the following approaches to optimizing proxy performance:
* Make sure that caching is enabled, and monitor the performance of your cache. Monitor the performance counters (installed by default) and event logs (for errors/warnings) on your proxy server on a periodic basis, to see how your proxy is performing. Note that TFS Proxy saves cache performance statistics to an Extensible Markup Language (XML) file named ProxyStatistics.xml, and that you can change the interval for saving these statistics. The ProxyStatistics.xml file is located in the App_Data folder in the proxy installation directory.
* Run a scheduled task to retrieve the latest files to the proxy server on a periodic basis. This helps to ensure that the latest versions of the files are available in the proxy cache, and to ensure that subsequent client requests for these files result in a cache hit.
* If you know that large files are going to be downloaded over a low bandwidth (< 3-Mbps) network, set the **executionTimeout** configuration to an appropriate value in Web.config. The default value is one hour <httpRuntime executionTimeout="3600"/>.

#### Additional Resources
*  For more information about examining TFS proxy performance, see [http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252455(VS.80).aspx)

## Migration
* **How is TFS version control different from VSS?**
* **How is the checkout model different from VSS?**
* **How should I migrate my source from VSS to TFS?**
* **How should I migrate my source from other version-control systems?**

### How is TFS version control different from VSS?
Microsoft Visual SourceSafe is targeted at individual developers and small teams, while TFS version control is designed for professional developers and very large teams with up to 2,500 users per server. Other major improvements introduced with TFS version control include deep integration with Visual Studio 2005 as well as distributed team support enabling efficient file access over WANs. The major differences between the two systems include the following:
* **Code churn –** Visual SourceSafe has no features that support code churn metrics. TFS version control gives you code churn metrics for every file that you check into the data warehouse, and you can slice the data in any way that you want.
* **Checkout –** Visual SourceSafe always gets the latest file or the pinned file from the database and overwrites your local version. TFS version control makes your workspace version of the file writable, but does not overwrite your version with a version from the database.
* **File locking –** Visual SourceSafe automatically applies an exclusive lock to a file when you check it out. By default, TFS version control allows multiple developers to check out a file concurrently. When conflicts do occur, they usually can be automatically resolved.
* **Branching –** Visual SourceSafe uses a pin-and-share branching method. Pinning is not supported in TFS version control, which instead uses path-space branching. This makes it easier to maintain old versions of your software, because it facilitates merging changes from one branch to another or making changes in two branches at once.
* **Sharing –** TFS version control does not support sharing. The migration of a shared file results in copying the file to the destination folder.
* **Workflow integration –** Visual SourceSafe is a stand-alone version-control system. TFS version control is integrated with work item tracking and TFS reporting.

#### Additional Resources
* To learn more about the differences between Visual SourceSafe and TFS version control, see “Visual Source Safe vs. Team Foundation Server” at [http://msmvps.com/blogs/vstsblog/archive/2005/07/02/56401.aspx](http://msmvps.com/blogs/vstsblog/archive/2005/07/02/56401.aspx)

### How is the checkout model different from VSS?
When you check out a file from TFS version control, the file is marked as writable in your workspace but is not synchronized with the database server. To get the latest version from the database server, you must first use the **get** command. In contrast, a VSS check-out operation gets the file from the database server and marks it as writable in your workspace.

Visual SourceSafe uses exclusive checkout by default, while TFS uses shared checkout by default. Shared checkout enables multiple developers to make changes to a file at the same time. Unlike in Visual SourceSafe, most conflicts in TFS can be resolved automatically.

#### Additional Resources
* For more information about the differences between VSS checkout and TFS version control checkout, see “Team Foundation vs. SourceSafe | Checking Out” at [http://blogs.msdn.com/korbyp/archive/2004/07/28/199720.aspx](http://blogs.msdn.com/korbyp/archive/2004/07/28/199720.aspx)

### How should I migrate my source from VSS to TFS?
Team Foundation Server ships with a VSS converter that allows you to migrate files, folders, version history, labels, and user information from a VSS database to TFS version control.  

The converter does have some limitations that are important to understand; for example:
* Historical information about file sharing is not preserved. Team Foundation Server does not support sharing. The migration of a shared file results in copying the file to the destination folder.
* Historical information about branching is not preserved.
* Team Foundation Server does not support pinning. Pinned files are migrated by creating two labels.
* Timestamps associated with actions are not preserved during migration.

#### Additional Resources
* For more information about how to prepare for migration, see [http://msdn2.microsoft.com/en-us/library/ms181246(en-us,vs.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181246(en-us,vs.80).aspx)
* For more information about how to perform the migration, see [http://msdn2.microsoft.com/en-us/library/ms181247(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181247(VS.80).aspx)
* For more information about the limitations of the VSS converter, see [http://msdn2.microsoft.com/en-us/library/ms252491(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252491(VS.80).aspx)
* For more information about the VSS Analyze tool, see [http://msdn2.microsoft.com/en-us/library/ysxsfw4x.aspx](http://msdn2.microsoft.com/en-us/library/ysxsfw4x.aspx)
* For more information about the VSSConverter command-line utility’s **migrate** command, see [http://msdn2.microsoft.com/en-us/library/ms400685(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400685(VS.80).aspx)

### How should I migrate my source from other version-control systems?
You can manually export files from the version-control system from which you are migrating and then import the files into TFS version control. To preserve file history or other attributes from the version-control system from which you are migrating, you can use the TFS version control object model to write your own migration tool.

Microsoft is currently working on a ClearCase converter; when it is ready, it will be announced on the TFS Migration blog at [http://blogs.msdn.com/tfs_migration](http://blogs.msdn.com/tfs_migration)

Component Software has created a converter that is compatible with VSS, GNU RCS, CS-RCS, GNU CVS, and Subversion (SVN).

#### Additional Resources
* For more information about TFS version control extensibility, see “Walkthru: The Version Control Object Model” at [http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/bb187335(VS.80).aspx)
* For more information about the Component Software converter, see [http://www.componentsoftware.com/Products/Converter/](http://www.componentsoftware.com/Products/Converter/)

## Project/Workspace Management
* **How should I organize my team projects?**
* **How should I manage dependencies between projects?**
* **What is a workspace?**
* **How do I use workspaces to isolate a developer?**
* **What are the proven practices for workspace mapping?**
* **When should I create a new team project versus a new branch?**
* **How should I manage source code that is shared across multiple projects?**
* **How should I manage binaries that are shared across multiple projects?**
* **How should I organize my source tree?**

### How should I organize my team projects?
Team projects are intended to represent the largest unit of work possible in your organization. Most often this will be a product under development.

Consider one of the following strategies for managing team projects:
* **Create one project per application.**
* **Create one project per release.**
**Create one project per application**
If you want to carry forward not only source code but also work items and other TFS assets between releases, consider using one project per application. When you use a single project for multiple versions of the application, all of the TFS assets are carried forward automatically for you for the next release. When you are ready to release a new version of your application, you can create a branch within the project to represent the release and isolate that code.

The following are reasons not to use one project per application:
* Releases in parallel are forced to share work item schemas, check in policies, and process guidance.  
* Reporting is more difficult; because reports default to the entire project, you must add filtering by release.
* If you have hundreds of applications, each in its own project, you will run up against TFS performance and scale limits.
* You will accumulate ‘baggage’ over multiple releases. The easiest way to eliminate this baggage is to create a new team project and then branch code you want to carry forward into that project.
**Create one project per release**
If you want each release to start fresh without carrying forward work items and other TFS assets, consider using one project per release. When you use a new project for each release, you can modify work item schemas, workflow, check-in policies, and other assets without impacting the old release. This can be especially useful if the old release will be maintained by a separate team, such as a sustained engineering team who may have a different process and workflow than your main development team.

The following are reasons not to use one project per release:
* While it is very easy to move the source code from one project to another, it is difficult to move work items and other TFS assets from one project to another.  Work items can only be copied one at a time to another project, if you want to copy sets of work items you’ll need to write your own utility.
* If you have hundreds of applications and releases, each in its own project, you’ll hit Team Foundation Server performance and scale limits.

Keep the following considerations in mind when choosing your strategy:
* Choose a structure that will suit your purposes in the long term, because restructuring existing team projects is difficult.
* Source can be easily shared among team projects as follows:
	* Branch source from one project to another.
	* Map source from another project into your workspace.
* Team Foundation Server can scale to ~500 projects by using the Microsoft Solution Framework (MSF) for Agile Development (MSF Agile) process template, or 250 projects using the MSF for CMMI® (MSF CMMI) process template. If you create your own process or customize an existing template, keep in mind that work item schemas have the largest impact on server scalability. A complex schema will result in a server capable of supporting fewer projects. 

#### Additional Resources
* For more information about using team projects, see “When to use Team Projects” at [http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx](http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx)

### How should I manage dependencies between projects?
If you need to reference an external assembly that is not built as part of your Visual Studio solution, such as a third-party assembly for which you only have the binary dynamic-link library (DLL), you have the following three choices: 
* You can store the external assembly as a binary resource as part of your project. This works well if you plan to maintain the dependency for other projects that might want to reference it, or if yours is the only project that relies on this dependency.
* You can reference an assembly on your build server by using either a virtual drive letter or a Universal Naming Convention (UNC) path. 
* You can store the set of external assemblies in a folder in a shared team project. This approach works well if there are many projects that want to reference this shared dependency and your project is not the clear owner of it.  
	* If you want to receive immediate updates to the binary when it is changed, you can create a workspace mapping for this team project to your local computer. You can set a file reference to the assembly within your local file structure. 
	* If you want to control the integration schedule for this dependency, you can create a branch from the shared project into your project and then merge whenever you are ready to pick up changes.

In general, you should avoid dependencies that cross team projects, and instead try to have all the related/dependent solutions/projects under the same team project. This reduces the need for build script customization. If you have a dependency, use project references to define the dependency. You should avoid file references because they are more difficult to manage. 

**Note:** Project-to-project references are supported within a solution. Also note that a project file (csproj, vjsproj, vcproj, vbproj, etc) can be included by multiple solutions (sln files), so a project can be shared by multiple separate solutions.

#### Additional Resources
* For more information about project references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about workspaces, see [http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx)

### What is a workspace?
A _workspace_ is a client-side copy of the files and folders on the TFS version control server. Local pending changes are isolated within your workspace until you check these changes into the server as an atomic unit (referred to as a changeset). A single workspace can contain references to multiple team projects. You can use multiple workspaces to isolate files or versions for your use only. 

**Note:** Workspaces are created per machine, per user account. Therefore, you can have different workspace definitions for each computer you use. Also, you can have multiple workspaces on a single computer by using multiple user accounts to log onto the computer. 

#### Additional Resources
* For more information about workspaces, see [http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx)

### How do I use workspaces to isolate the work of a developer?
As a developer, you can create two workspaces: one containing references to files and folders being worked on by the rest of the team, and another containing files and folders that you want to isolate. You might want to isolate these files in order to evolve specific files in parallel with work that is happening elsewhere. For example, you can use this approach to work on risky pending changes, or to conduct a code review.

#### Additional Resources
* For more information about workspaces, see [http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx)

### What are the proven practices for workspace mapping?
_Workspace mapping_ is the means by which you map files and folders on the server to a location on your local hard drive. 

Consider the following practices for creating workspace mappings:
* **Create mappings at the team project root level.** For new team projects, map your team project root ($/MyTeamProject) to a folder with the same name on your local drive; for example, C:\TeamProjects. Because mappings are recursive, your entire local folder structure is created automatically and will be exactly the same as the structure in source control.
* **Use a unique local folder path on shared computers.** Two users of a single computer cannot share the same workspace mapping. For example, you and a colleague cannot map the same team project ($/MyTeamProject) to the same folder on the local computer. Instead, create mappings beneath My Documents (although this leads to long location paths) or establish a team folder naming convention on the local computer (e.g., C:\TeamProjects\User1, C:\TeampProjects\User2 etc).
* **You may not need the entire tree.** To improve performance and reduce disk size requirements, only map the files you need for your development project. In general, you will only need the files and projects associated with the solution on which you will work.  
* **Avoid using workspace mapping to support cross-project dependencies.** In general, you should avoid dependencies that cross team projects and try to have all the related/dependent solutions/projects under the same team project. This reduces the need for build script customization. If you have a dependency, use project references to define the dependency, or branch the dependency from a shared project into your project. You should avoid file references because they are more difficult to manage. The exception is when the dependent project is developed in parallel and you need to make real-time changes. In this case, you can consider using the workspace mapping. You can still consider branching to create a buffer of isolation if the dependent code is causing too many breaking changes.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx)

### When should I create a new Team Project versus a new Branch?
Create a branch if you want to isolate the code that developers are working on within a project while at the same time sharing all other TFS assets such as work items, process guidance, and reports.

Create a new team project if you want to use different TFS assets such as work items, process guidance, and reports. Also create a new team project if you want to carry forward your code without carrying forward any other TFS assets.

#### Additional Resources
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about adding a new project, see “How to: Add a Project or Solution to Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181373(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181373(VS.80).aspx)

### How should I manage source code that is shared across multiple projects?	
Managing shared source involves two decision points: 
# Where do you want to store the source?
# How do you want your team to access the shared source?

The following options are available for storing the source:
* If the shared source is clearly owned by a particular team, store it in their team project.
* If the shared source has no clear ownership, create a team project specifically for the shared code.

If you want to use the source in another project, choose one of the following two options:
* If you need to stay in sync with shared code at all times, map the source from the shared location into the local workspace on the client machines.
* If you only need to stay in sync periodically, branch from the shared location into the consuming team project. Every time you perform a merge from the shared location to the consuming project, you will pick up latest source.

Whether you use workspace mapping or branching, use naming conventions that make it clear where the shared source location is located in your project; for example:
* **Main** – Container for all assets you need in order to ship the product
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
	* **Docs** – Container for documentation that will ship with the product 
	* **Installer** – Container for installer source code and binaries 
	* **Builds** – Container for team build scripts
	* **Tests** – Container for test team test cases 

#### Additional Resources
* For more information about project references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about workspaces, see [http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx)

### How should I manage binaries that are shared across multiple projects?
Managing shared binaries is similar to managing shared source?you must decide where you want to store the binaries and how you want your team to access the binaries.

The following options are available for storing the binaries:
* If the shared binaries are clearly owned by a particular team, store it in their team project.
* If the shared binaries have no clear ownership, create a team project specifically for the shared binaries.

The following options are available for using the binaries in another project
* Shared binaries are usually updated only periodically. If this is the case for your project, branch from the shared location into the consuming team project. When the binaries change, you can execute a merge to get the latest version.
* If you need to stay in sync with the shared binaries at all times, map the source from the shared location into a local workspace on the client machines.

Whether you use workspace mapping or branching, use naming conventions that make it clear where the shared binary location is in your project; for example:
* **Main** – Container for all assets you need in order to ship the product
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
	* **Docs** – Container for documentation that will ship with the product 
	* **Installer** – Container for installer source code and binaries 
	* **Builds** – Container for team build scripts
	* **Tests** – Container for test team test cases 

#### Additional Resources
* For more information about project references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx)
* For more information about workspaces, see [http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181383(VS.80).aspx)

### How should I organize my source tree?
Your source tree structure consists of a combination of folder structure, file structure, and branch structure. Within your Main branch, the following folder and file structure has been proven to work for teams of various sizes:
* **Main** – Container for all assets you need in order to ship the product
	* **Source** – Container for everything you need in order to build
		* **Code** – Container for source code
		* **Shared Code** – Container for source code that is shared from other projects
		* **Unit Tests** – Container for unit tests
		* **Lib** – Container for binary dependencies
	* **Docs** – Container for documentation that will ship with the product 
	* **Installer** – Container for installer source code and binaries 
	* **Builds** – Container for team build scripts
	* **Tests** – Container for test team test cases 

Any branches that you create off of Main will copy this folder and file structure into the new branch; for example:
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
	* **Docs** – Container for documentation that will ship with the product 
	* **Installer** – Container for installer source code and binaries 
	* **Builds** – Container for team build scripts
	* **Tests** – Container for test team test cases

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)

## Shelving
* **What is shelving?**
* **What is a shelveset?**
* **When would I typically use shelving?**
* **How do I use shelving to back up my work?**
* **Why would I want to unshelve a shelveset?**

### What is shelving?
The process of shelving a change or set of changes (also known as creating a shelveset) allows you to store pending changes under source control without having to check in the changed files. This means that you benefit from having the files on the (backed up) server while ensuring that the potentially incomplete work on those files does not impact and break your regular builds.

#### Additional Resources
* For more information about shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)

### What is a shelveset?
A _shelveset_ is a set of files that are saved but are not yet ready to be committed to source control. Files can be shelved in order to save pending changes to the workspace, or to be shared with other team members for feedback. You can also use shelved files to hand off partially completed work.

#### Additional Resources
* For more information about shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)

### When would I typically use shelving?
There are a number of common scenarios in which you would use shelving:
* You are midway through making changes to a set of source code when new, higher-priority work is allocated (for example, an emergency bug fix is required). At this point you need to go back to a stable version of the code but do not want to lose your changes. You can shelve your code and easily retrieve it later.
* You have not completed work at the end of the day but want to ensure that your current work is backed up on the server. By shelving your current changes, the changes are applied to the Team Foundation Server and can be retrieved by you (or others) on another day. 
* You want to discuss or review your partially completed code with a remote team member. Rather than e-mailing the code, you can shelve it and then have your remote colleague retrieve the files from the shelf.
* You want to pass partially finished work to another developer for completion.

#### Additional Resources
* For more information about shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)

### How do I use shelving to back up my work?
If your work on one or more source files is not complete at the end of the working day, you can shelve your code to ensure that the source is uploaded to the server without checking in partially completed work.

#### Additional Resources
* For more information about shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)

### Why would I want to unshelve a shelveset?
You might unshelve a shelveset to:
* Resume work on a set of files that you backed up previously by using a shelveset.
* Integrate shelved pending changes into your work going forward.
* Review someone else’s code. 
* Pick up another developer’s partially completed work.

#### Additional Resources
* For more information about unshelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)
## Source Control Resources
* For more information about TFS Source Control, see “Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx)