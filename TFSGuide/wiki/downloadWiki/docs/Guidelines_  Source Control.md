## Guidelines: Source Control
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

## Index
### Accessing Version Control
* _Consider using command-line tools._
* _Use Microsoft® Visual Studio® 2005 Team Foundation Power Tools (TFPT) to unshelve a change._
* _Use Team Foundation Power Tools to roll back a change._
* _Use Team Foundation Power Tools to work offline._
* _Use Team Foundation Power Tools to get a changeset._
* _Use Team Foundation Power Tools to remove pending edits._

### Administration
* _Turn off inherited permissions on maintenance branches._
* _Deny check-in permissions to developers you do not yet trust to make changes to your source._

### Branch / Label / Merge
* _Use labels to mark builds you might need to return to._
* _Use branches to isolate supported releases._
* _Plan your branching structure along merge paths._
* _Branch at a high level, including configuration and source files._
* _Do not branch too deeply._
* _Do not branch unless you need to._
* _Avoid baseless merges where possible._
* _Prefer full merges to “cherry-pick” merges._
* _Merge frequently._
* _Always create a top-level folder for a new team project to serve as a main branch._
* _Consider using the candidate or preview switch to double-check before merging._
* _When renames are part of the merge, pay close attention to the path that the tool recommends._ 
* _Be careful when resolving merge conflicts._
* _Check in the results of one merge at a time._
* _Build and run tests after the merge and prior to check-in._

### Check-ins and Check-in Policies
* _Only check in your code when you are ready to share it._
* _Use shelvesets to back up or share pending changes._
* _Resolve one work item per check-in._
* _Use check-in policies to enforce coding standards._
* _Use check-in policies to enforce a code quality gate._
* _Detect when a policy has been overridden._
* _Plan to avoid conflicts._

### Checkout, Get, and Lock
* _Get the latest source before making changes._
* _Use the **lock** command with discretion._
* _Communicate with your teammates when locking files._ 

### Dependencies
* _Use project references whenever possible._
* _Use file references only where necessary._
* _Use **copy local = true** for project and file references._
* _Use dynamic URLs when referencing Web services._

### Distributed / Remote Development
* _Make sure that you get an appropriately sized disk drive for your proxy._
* _Create a scheduled task to pull the latest files on a periodic basis._ 
* _Periodically monitor proxy performance counters and the event log._
* _Configure executionTimeout based on file sizes and bandwidth._
* _Disable the proxy if it is going to be down for an extended time period._
* _Consider workspace cloaking to reduce unnecessary file transfers._

### Migration
* _Use the VSS converter to migrate to Team Foundation Server Source Control._
* _Migrate from other source-control systems to Team Foundation Server Source Control._

### Project / Workspace Management
* _Isolate a single developer using workspaces rather than branches._
* _Delete and rename files by using source control, not Microsoft Windows® Explorer._
* _Only delete and rename with your solution open._
* _Create one team project per application if you want to move your assets between application versions._
* _Create one team project per version if you want to start fresh with each application version._
* _Use branching to share code and binaries that require integration testing._
* _Avoid workspace mapping to support cross-project dependencies._
* _Create workspace mappings at the team project root level._
* _Use a unique local folder path on shared computers._
* _Consider mapping only part of the source tree._
* _Structure your source tree to support branching._

### Shelving
* _Use shelving to share pending changes for review or handoff._
* _Use shelving to back up pending changes to the server._
* _Use shelving if interrupted by higher-priority work._

## Accessing Version Control
* **Consider using command-line tools.**
* **Use Team Foundation Power Tools to unshelve a change.**
* **Use Team Foundation Power Tools to roll back a change.**
* **Use Team Foundation Power Tools to work offline.**
* **Use Team Foundation Power Tools to get a changeset.**
* **Use Team Foundation Power Tools to remove pending edits.**

### Consider Using Command-Line Tools
For operations not available from Visual Studio, or if you need to schedule operations, consider using command-line tools such as the Team Foundation Power Tools (Tfpt.exe) that are provided with Team Foundation Server (TFS). The Tfpt.exe tools are available as a separate download. You can use these command-line tools to schedule operations by using the Windows Task Scheduler. 

To ensure that the appropriate path and other environment variables are set up, run Tf.exe from the Visual Studio 2005 Command Prompt window, or run the Vsvars32 batch file, which is normally located in _DriveLetter_:\Program Files\Microsoft Visual Studio 8\Common7\Tools. The Tf.exe tool supports most source control commands including **Checkin**, **Checkout**, **Get**, **History**, **Shelve**, **Branch**, **Merge**, **Label**, **Status**, **Undelete**, and **Undo**. 

The following are common operations you might want to execute from the command line by using Tf.exe:
* Synchronize files from the server to your local machine – **tf get**
* Add a file to the server – **tf add**
* Check out a file for editing – **tf checkout**
* Check in pending changes – **tf checkin**
* Retrieve a particular changeset from the server – **tf get /version**

There are certain operations that you can only be perform from the command line:
* Delete another user’s workspace – **tf workspace /delete**
* Undo another user’s check-in – **tf undo**
* Unlock another user’s lock – **tf lock**
* Define label scope – **tf label**
* Perform a baseless merge – **tf merge**

#### Additional Resources
* For more information, see “Walkthrough: Working with Team Foundation Source Control from Command Line” on the Microsoft MSDN® Web site at [http://msdn2.microsoft.com/en-us/library/zthc5x3f.aspx](http://msdn2.microsoft.com/en-us/library/zthc5x3f.aspx) 
* For more information about commands that are only available from the command line, see “Operations Available Only From the Command-Line (Team Foundation Source Control)” at [http://msdn2.microsoft.com/en-us/library/ms194957(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms194957(VS.80).aspx) 

### Use Team Foundation Power Tools to Unshelve a Change
The Team Foundation Power Tools (TFPT) provides version-control functionality that is not available from Visual Studio. For example, you can use TFPT to help support offline working or to perform rollback operations in order to undo check-ins of a changeset. Consider using TFPT if you need to unshelve a change.

The **unshelve** operation supported by TFS does not allow shelved changes and local changes to be merged together. By using TFPT to unshelve a change from a changeset, if an item in your local workspace has a pending change that is an edit, and the shelved change is also an edit, then TFPT can merge the changes with a three-way merge.

You run this command from the command line by using Tfpt.exe.

#### Additional Resources
* To download Team Foundation Power Tools, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)   
* To view a forum discussing Team Foundation Power Tools, see [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1) 

### Use Team Foundation Power Tools to Roll Back a Change
Consider using TFPT if you need to roll back a change. The ability to undo a check-in of a changeset is not directly supported by TFS. By using the TFPT **rollback** command, you can attempt to undo any changes made in a specified changeset. Not all changes can be rolled back, but the rollback works for most scenarios.

You run this command from the command line by using Tfpt.exe.

#### Additional Resources
* To download Team Foundation Power Tools, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)     
* To view a forum discussing Team Foundation Power Tools, see [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1) 

### Use Team Foundation Power Tools to Work Offline
Offline working is not supported natively by TFS. If you want to work offline, you must adhere to the following strict workflow:
# Manually remove read-only flags.
# Edit files.
# Add or delete files
# Run the TFPT online command.

Each of these steps is described in detail below.

**Important:** You must not rename any files while you are offline.

1. **Manually remove read-only flags.**
By default, all files in the workspace that have not been checked out are marked as read-only. When you work without a server connection, you must manually remove the read-only flags from files before editing or deleting them. To do this, right-click the file in Windows Explorer, click **Properties**, clear the **Read-only** check box, and then click **OK**. Alternatively, you can use the DOS command **attrib -r**. 
2. **Edit files.**
You can now edit any files for which you have removed the read-only flag.
3. **Add or delete files.**
You can add or delete files for which you have removed the read-only flag. Do not rename files, because the TFPT **online** tool cannot distinguish a rename operation from a deletion paired with an add operation. 
**Note:** You must specify an option to the **Tfpt** **online** command to get it to look for deletions, as this is a more time-consuming operation.
4. **Run the TFPT online command.**
When you are back online, run the TFPT online command by typing **TFPT online** at the command line. This command scans your workspace for writable files and determines what changes should be pended on the server. If you have deleted any files, use the /**delete** switch. This tells the tool to scan for deleted files in your local workspace as well. The tool then displays the online window from which you can choose which changes to pend into the workspace.

#### Additional Resources
* To download Team Foundation Power Tools, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en)   
* To view a forum discussing Team Foundation Power Tools, see [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1) 

### Use Team Foundation Power Tools to Get a Changeset
Consider using TFPT if you need to get a changeset. The TFPT **GetCS** command enables you to get all the items listed in a changeset at the time of that changeset version. This is useful if a colleague has checked in a change that you need to have in your workspace, but you cannot update your entire workspace to the latest version.

You run this command from the command line by using Tfpt.exe.

#### Additional Resources
* To download Team Foundation Power Tools, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en) 
* To view a forum discussing Team Foundation Power Tools, see [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1) 

### Use Team Foundation Power Tools to Remove Pending Edits
Consider using TFPT if you need to remove pending edits from files. The TFPT **Undo Unchanged** command removes pending edits from files that have not actually been edited. This is useful in a scenario where you check out a large number of files for editing, but only actually make changes to a small number of the files. You can undo your edits on the unchanged files by running the TFPT UU tool, which compares hashes of the files in the local workspace to hashes on the server in order to determine whether or not the file has actually been edited.

You run this command from the command line by using Tfpt.exe.

#### Additional Resources
* To download Team Foundation Power Tools, go to [http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=7324C3DB-658D-441B-8522-689C557D0A79&displaylang=en) 
* To view a forum discussing Team Foundation Power Tools, see [http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=930&SiteID=1) 

## Administration
* **Turn off inherited permissions on maintenance branches.**
* **Deny check-in permissions to developers you do not yet trust to make changes to your source.**

### Turn Off Inherited Permissions on Maintenance Branches
Once a branch is in maintenance—for example, after you have shipped a version of your software—you can turn off inheriting permissions to lock down the tree. After you have done this, you can grant individual users the PendChange and Checkin permissions as needed for hot fixes.

#### Additional Resources
* For more information about removing permissions, see “How to: Remove Access to Source Control Files” at [http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx) 

### Deny Check-in Permissions to Developers You Do Not Yet Trust to Make Changes to Your Source
You can deny check-in permissions on the source tree for developers you do not trust, such as new hires or interns. Make sure that you set your desired permissions (including permissions for your own account) before turning off inheritance. Rather than check in directly, they can make pending changes and then shelve these changes. A more experienced developer can then unshelve the changes, review them, and check them in.

#### Additional Resources
* For more information about removing permissions, see “How to: Remove Access to Source Control Files” at [http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms400718(VS.80).aspx) 

## Branch / Label / Merge
* **Use labels to mark builds you might need to return to.**
* **Use branches to isolate supported releases.**
* **Plan your branching structure along merge paths.**
* **Branch at a high level, including configuration and source files.**
* **Do not branch too deeply.**
* **Do not branch unless you need to.**
* **Avoid baseless merges where possible.**
* **Prefer full merges to “cherry-pick” merges.**
* **Merge frequently.**
* **Always create a top-level folder for a new team project to serve as a main branch.**
* **Consider using the candidate or preview switch to double-check before merging.**
* **When renames are part of the merge, pay close attention to the path that the tool recommends.** 
* **Be careful when resolving merge conflicts.**
* **Check in the results of one merge at a time.**
* **Build and run tests after the merge and prior to check-in.**

### Use Labels to Mark Builds You Might Need to Return To
Use labels to mark daily builds so that you can easily view and retrieve the set of files used for a particular build. Team Build automatically assigns a label to the set of files associated with each build that it creates. Team Build labels follow the format “ReleaseType_Build#”; for example, “Releasex86_20070226.1”.

Although every team build is labeled, you might want to create your own labels for builds that you are likely to want to return to, such as:
* An internal milestone; e.g., alpha release
* A build created after branch or external dependency integration

You should use a label-naming convention that makes it easy to locate the build later and know what it represents. Use labels that are clear about what they represent. For example, use a convention such as “AlphaBuild_20070112” composed of “LabelName_Date”. 

When you release a build to a customer for whom you will need to provide maintenance, use a branch instead of a label to isolate future maintenance work on the release. You can subsequently merge the branch, with any fixes it might contain, back into to your main source tree.
 
To locate an existing label, on the **File** menu, point to **Source Control**, **Label** and then click **Find Label**. Once you have found the label, you can modify it or delete it from within the **Find Label** dialog box.

#### Additional Resources
* For more information, see “Working with labels” at [http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181439(VS.80).aspx)    
* For more information about labels, see “How to: Apply Labels” at [http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181440(VS.80).aspx)   

### Use Branches to Isolate Supported Releases
Create a branch containing the source code used to generate a supported release build. This allows you to apply fixes and updates to the supported release version of your software without impacting the continued development of your source code base, which continues along the main branch.

You continue to develop the next version of your application along your main branch in parallel with the supported release branch. You can merge any stabilization changes you made to the supported release branch into the main branch prior to releasing the next version of your product.

The following is an example of what your branch structure might look like after you have created a Maintenance branch used to support released versions of your software:
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**
* **Releases** – Container for maintenance branches
	* **Release 1** – Maintenance Branch
		* **Source**

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx) 

### Plan Your Branching Structure Along Merge Paths
You can only merge along existing branch paths by using Source Control Explorer. You can do baseless merges along other paths from the command line, but this type of merge is less intelligent, resulting in more merge conflicts and additional conflicts in future merges.

Keep the following in mind when you perform merges:
* Merging along the hierarchy, from parent to child or from child to parent, results in fewer conflicts than merging across the hierarchy.
* The branch hierarchy is based on the branch parent and branch child, which may be different than the physical structure of the source code on disk.  For example:
* **Physical Structure**:
	* **Development – Development** branch
	* **Main –** Integration branch
	* **Releases** – Container for release branches
		* **Release 1** – Release Branch
* **Logical Structure**:
	* **Main**
		* **Development**
		* **Release 1**

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Branch at a High Level, Including Configuration and Source Files
Branch at a high-enough level that the branch you create is still compilable. For instance, in the following source tree:
* **Main** – container for all assets you need to ship the product
* **Source** – container for everything you need to build
	* **Code** – container for source code
	* **Shared Code** – container for source code that is shared from other projects
	* **Unit Tests** – container for unit tests
	* **Lib** – container for binary dependencies
* **Docs** – container for documentation that will ship with the product 
* **Installer** – container for installer source code and binaries 
* **Tests** – container for test team test cases 

Branch at the level of the Source folder to ensure that the new branch contains all source and configuration files.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Do Not Branch Too Deeply
Do not branch too deeply because this will add to the time required to merge a change from a child branch up to the topmost parent. For example, in the following branching structure:

* **Development** – Container for development branches
	* **Development Branch** 
		* **Sub-Branch** 
			* **Sub-Sub-Branch**
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**

Merges result in fewer conflicts when performed along the branch hierarchy. Therefore, if there is a change in the **Sub-Sub-Branch** that you would like to merge into **Main**, you would first need to merge with the **Sub-Branch** and the **Development Branch** before you can merge into **Main.** Each merge takes time to complete, resolve conflicts, build, and test, which multiplies merge time by the level of branches you have created in your branch structure.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Do Not Branch Unless You Need To
Do not branch unless your development team needs to work on the same set of files concurrently. If you are unsure, you can label a build and create a branch from that build at a later point. Merging branches can be costly, especially if there are significant changes between them.

Merging requires one or more developers to execute the merge and sort out conflicts. The merged source must be thoroughly tested because it is not uncommon to make bad merge decisions that can destabilize the build.

Merging across the branch hierarchy is especially difficult and requires you to manually handle many conflicts that could otherwise be handled automatically.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)   
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx) 

### Avoid Baseless Merges Where Possible
Avoid baseless merges where possible. When performing a baseless merge, TFS has no information describing the relationship of files and folders in the branches being merged. This generally results in more merge conflicts, and can lead to more conflicts in future merges. 

Structure your branch trees so that you only need to merge along the hierarchy (up and down the branch tree) rather than across the hierarchy. Branching across the hierarchy forces you to use a baseless merge.

Keep the following in mind when performing merges:
* Merging along the hierarchy, from parent to child or from child to parent, results in fewer conflicts than merging across the hierarchy.
* The branch hierarchy is based on the branch parent and branch child, which may be different than the physical structure of the source code on disk.  

For example:
* **Physical Structure**:
	* **Development – Development** branch
	* **Main –** Integration branch
	* **Releases** – Container for release branches
		* **Release 1** – Release Branch
* **Logical Structure**:
	* **Main**
		* **Development**
		* **Release 1**

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Prefer Full Merges to “Cherry-Pick” Merges
Rather than picking individual changes to merge between branches (a “cherry-pick” merge), choose to merge the entire branch at once. It can be convenient to select individual changes in a branch to merge with another branch. However, if a cherry-picked changeset falls in the middle of a future merge range, that changeset will be re-merged, potentially resulting in additional merge conflicts.

This is especially true for **/discard** merges run from the command line. The discarded changeset can be picked up if it falls in the middle of a future merge range.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Merge Frequently
Eliminate the latency between branches, especially when teams are working on the same release but in their own isolated branch. This ensures compatibility between changes.

The merge schedule depends on the complexity of your branch structure as well as the individual needs of your development team. As an example, in a moderately complex branch structure such as the one below, the development branches may merge up to the main branch daily and merge changes back from the integration branch every couple of days.

* **Development –** Folder for isolated development branches
	* **External** - External dependency branch
	* **Team 1 -** Team branch
	* **Team 2 -** Team branch
		* **Feature A –** Feature branch
		* **Feature B –** Feature branch
		* **Feature C –** Feature branch
* **Main –** Integration branch
* **Releases -** Folder for release branches
	* **Release 2** – Release Branch
* **Safe Keeping -** Folder for safekeeping branches
	* **Release 1 -** Safekeeping branch

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Always Create a Top-Level Folder for a New Team Project to Serve as a Main Branch
Start any new team project by creating a folder, frequently named **Main**, underneath your team project. Put all source for the **Main** branch in this folder. When you need to create a new branch, branch directly from the Main folder.

The following example shows a typical branch structure:
* **Development** – Folder for isolated development branches, branched from Main
	* **Feature A**
		* **Source**
	* **Feature B**
		* **Source**
* **Main** – Integration Branch
	* **Source**
	* **Other Asset Folders**
* **Releases** – Folder for release branches, branched from Main
	* **Release 1** – Maintenance Branch
		* **Source**

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Consider Using the Candidate or Preview Switch to Double-Check Before Merging
Prior to performing a merge, use the candidate or preview switch to double-check your merge results. Although this option is only available from the command line, it is extremely beneficial to know which files and which versions will be merged when you perform the merge command. For example, this can help to ensure that the scope of your merge is not significantly greater than you were expecting and to make sure that you understand the impact of your merge command. For large merges, the merge report also helps you to divide the work between individuals or teams.

To preview the results of a merge, use the Tf.exe command-line tool with the **merge** command, together with the **preview** or **candidate** switches. For example: 

{{ Tf merge main/source development/feature/source /preview }}

The **preview** switch shows a preview of the merge, while the **candidate** switch prints a list of all changesets in the source that have not yet been merged into the destination. The list includes the changeset ID that has not been merged and other basic information about that changeset.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### When Renames Are Part of the Merge, Pay Close Attention to the Path That the Tool Recommends
When renames are part of the merge, pay close attention to the path that the tool recommends and make changes as appropriate. All renames are marked as conflicts. The merge algorithm used by TFS tries to calculate the best target path when a rename is being merged over. In some cases the default target path is not the desired path, so you should always double-check prior to committing the merged file.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Be Careful When Resolving Merge Conflicts
Be careful when merging because it is easy to make mistakes that may result in build instability. When merging files:
* Double-check the code you are merging before committing the merges.
* Test that you can compile the resulting merged file before checking it back into source control.
* Verify that the associated unit tests run and succeed before checking the merged file back into source control.
* Make sure that you understand the nature of the changes made by another developer. If you are in doubt about merging some lines, talk to the developer who made the other changes so that you are sure of their purpose and to get a second view on the impact of your merge.

After you have finished merging, compile the resulting source and run unit tests to test for major breaks.

#### Additional Resources
* For more information about resolving merge conflicts, see “Resolving Conflicts” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms181432(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181432(VS.80).aspx) 

### Check In the Results of One Merge At a Time
Check in the results of one merge before performing a second merge that involves the same files. After performing the first merge, compile the code and ensure that the unit tests succeed, and then check in your pending changes. Then begin the second merge and repeat the process.

This helps to reduce complexity and, by keeping the merges separate, enables you to undo changes if the need arises. 

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Build and Run Tests After the Merge and Prior to Check-in
Having performed a merge, make sure that you compile the code and run the associated tests before checking in the merged file. Do this to avoid introducing build instability as a result of your merges. 

The results of a merge are initially isolated within your workspace and are not uploaded to the server until you check in the pending changes. 

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information on branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information on merging, see “How to: Merge Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

## Check-in and Check-in Policies
* **Only check in your code when you are ready to share it.**
* **Use shelvesets to back up or share pending changes.**
* **Resolve one work item per check-in.**
* **Use check-in policies to enforce coding standards.**
* **Use check-in policies to enforce a code quality gate.**
* **Detect when a policy has been overridden.**
* **Plan to avoid conflicts.**

### Only Check In Your Code When You Are Ready to Share It
Only check your updated code into source control when it is fully unit-tested and ready to share with the rest of the team. Use shelvesets for intermediate work that is not yet complete. 

When you check in your code, it will be used as part of your next scheduled build. Any incomplete code is likely to cause build instability. Also when you check in your code, any other developer who does a **get latest** operation will pick up your changes. If they are incomplete or inadequately tested, they will cause problems for your colleague.

#### Additional Resources
* For more information about check-ins, see “How to: Check In Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx) 

### Use Shelvesets to Back Up or Share Pending Changes
Use shelvesets to back up files that contain pending changes you are not yet ready to check in. You can also use shelvesets to share code for code review, or if you are passing off a development task to another developer. By using shelvesets, you can upload your pending changes to the server without checking in partially completed work that could potentially lead to build instability.

To shelve a set of pending changes, first view the changes by right-clicking your solution in Solution Explorer and then clicking **View Pending Changes**. Select the files you want to shelve and then click **Shelve**. Type a shelveset name and a comment that identifies the purpose of the shelveset, and then click **Shelve**. 

**To retrieve a shelveset** 
# On the **File** menu, point to **Source Control** and then click **Unshelve**. 
# In the **Owner** **name** text box, type the shelveset creator’s name (for example, Contoso\JimB or simply JimB) and then click **Find**. 
# In the Results pane, select the shelveset you want to unshelve into your workspace, and then click **Details**. 
# If you want to delete the shelveset as you retrieve it from the TFS source control server, clear the **Preserve** **shelveset** **on server** option. Team Foundation Server restores each shelved revision into the destination workspace as a pending change as long as the revision does not conflict with a change that is already pending in your workspace. 
# Optionally, you can clear the **Restore work items and check-in notes** option if you do not want to have the work items and check-in notes associated with the shelveset restored. When the **Details** dialog box appears, select the shelveset or shelveset items you want to unshelve into your workspace, and then click **Unshelve**.

#### Additional Resources
* For more information, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)   

### Resolve One Work Item per Check-in
After resolving a work item, check in your pending changes and update the work item status. This practice serves the following purposes:
* It provides a consistent record in the source control database that can be used to review changes per work item, or to back a work item out if necessary in the future.
* It ensures that you do not wait too long between check-ins. The longer you wait between check-ins, the more likely that you will have a conflict that requires a manual merge and additional testing.

#### Additional Resources
* For more information about check-ins, see “How to: Check In Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181411(VS.80).aspx) 
* For more information about work items and changesets, see “How to: Associate Work Items with Changesets” at [http://msdn2.microsoft.com/en-us/library/ms181410(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181410(VS.80).aspx) 
* For more information about reviewing work item details, see “How to: View Work Item Details from Pending Changes Window” at [http://msdn2.microsoft.com/en-us/library/ms245467(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245467(VS.80).aspx) 

### Use Check-in Policies to Enforce Coding Standards
Use check-in policies to enforce coding standards across your development team. Check-in policies help to ensure that all source code checked into TFS source control meets your defined coding standards. 

The code analysis check-in policies that ship with TFS enables you to ensure that static code analysis has been run on code before it is checked in. You can fine-tune the code analysis policy to check many different rules. For example, you can check rules governing design, interoperability, maintainability, mobility, naming conventions, reliability, and more.

**To enforce a code analysis check-in policy for a team project**
# In Team Explorer, right-click your team project, point to **Team Project Settings**, and then click **Source Control**.
# Click the **Check-in Policy** tab and then click **Add**.
# In the **Add Check-in Policy** dialog box, select **Code Analysis** and then click **OK**.
# In the **Code Analysis Policy Editor**, select either **Enforce C/C++ Code Analysis (/analyze)** or **Enforce Code Analysis** **For Managed Code**. Select both if your project contains a combination of managed and unmanaged code.
# If you select **Enforce Code Analysis** **For Managed Code**, configure your required rule settings for managed code analysis based on your required coding standards. This determines precisely which rules are enforced.

You can also create a custom check-in policy to perform checks that are not available by default. For example, you can disallow code patterns such as banned application programming interface (API) calls, or you can write a policy to enforce your team’s specific coding style guidelines, such as where braces should be positioned within your source code.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To view sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To view sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)

### Use Check-in Policies to Enforce a Code Quality Gate
Use a combination of code analysis and testing policies to enforce a code quality gate. For example, use the supplied testing policy to ensure that specific tests are executed and passed prior to allowing source to be checked into TFS source control. You can also configure a code analysis policy to help ensure that your code meets certain quality standards by ensuring that security, performance, portability, maintainability, and reliability rules are passed.

By enforcing this type of check-in policy in addition to policies that enforce coding standards and guidelines, you ensure your code meets a specific code quality gate.

**To enforce a code analysis check-in policy for a team project**
# In Team Explorer, right-click your team project, point to **Team Project Settings,** and then click **Source Control**. 
# Click the **Check-in Policy** tab, click **Add**, and then select and configure the appropriate policy.

#### Additional Resources
* For more information about creating and using a custom check-in policy, see “How To – Step Through Creating Custom Check-in Policies for TFS” in this guide.
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To see sample code that will disallow selected patterns on check-in, see “Checkin Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Checkin Policy: Make Sure the Comment Isn’t Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I’ve Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)

### Detect When a Policy Has Been Overridden
Team Foundation Version Control does not prevent you from overriding a policy. However, you can use the following steps to detect if a policy has been overridden:
* Use the Team Foundation Eventing Service (from the Team Foundation Core Services API) for hooking into check-in events.
* Write a **Notify** method that parses the details of the changeset and then react to it if an override has occurred.

Alternatively, you can manually scan changeset history to discover policy overrides.

#### Additional Resources
* To learn more about overriding a check-in policy, see “How to: Override a Check-in Policy” at [http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245460(VS.80).aspx) 
* To learn more about the Team Foundation Eventing Service, see “Eventing Service” at [http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/bb130154(vs.80).aspx) 
* To learn how to receive an e-mail message when a policy has been violated, see [http://blogs.infosupport.com/marcelv/archive/2005/10/18/1635.aspx](http://blogs.infosupport.com/marcelv/archive/2005/10/18/1635.aspx)

### Plan to Avoid Conflicts
Plan to avoid having multiple developers working in the same region of the same source file at the same time. Do this to avoid conflicts that are potentially difficult to correctly resolve. While automatic conflict resolution can resolve many conflicts, you should avoid situations where two or more developers are working on the same method, or on the same lines of code. Conflicts on the same lines of code require manual conflict resolution, which complicates the merge operation. Effective team communication is the key.

Before starting work on a file, make sure that you have the latest version from source control and check to see if anyone else has the file checked out before you begin work. If a colleague has the file checked out, ask your colleague what he or she is working on and then decide if you can wait until they complete their changes or if it is safe to continue to work in parallel on the same file because you are working on separate functionality in separate source code regions within the file.

**To check if someone else has a file checked out**
# In the Team Explorer window in Visual Studio, double-click **Source Control**.
# Browse to the folder containing the file you want to check in the source control folder hierarchy. 
Any pending changes are listed together with the username of the user who owns those changes.

To check which files people currently have pending changes for, run the following command from a Visual Studio 2005 command prompt window.

{{ Tf status /format:detailed /user: }}

When you do begin working on a source file that you know others will work on in parallel, let other team members know that you are working on the file and which aspects you will be updating. 

#### Additional Resources
* For more information on viewing pending changes in your workspace, see “How to: View and Manage All Pending Changes in Your Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181400(VS.80).aspx) 
* For more information on viewing pending changes in other workspaces, see “How to: View Pending Changes in Other Workspaces” at [http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181401(VS.80).aspx) 

## Checkout, Get, and Lock
* **Get the latest source before making changes.**
* **Use the lock command with discretion.**
* **Communicate with your teammates when locking files.** 

### Get the Latest Source Before Making Changes
To make sure that you have the latest versions of all the source files for the project you are working on, run a **get latest** command before you check out a file for editing. The danger of not doing so is that locally building your code against non-current source files increases the likelihood of your code causing build problems when you subsequently check it into the server. 

To get the latest copies of the file set associated with a specific team project, right-click the team project in Source Control Explorer and then click **Get Latest Version**. If you currently have writable files with pending edits in your workspace, this command does not overwrite those files. You can run the same command from the command line by running the **Tf get /all** command from a directory mapped to the current workspace. 

#### Additional Resources
* For more information about the **Get** command, see “Get Command” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/fx7sdeyf(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/fx7sdeyf(VS.80).aspx) 

### Use the lock Command with Discretion
Use the **lock** command sparingly because locking a file while you work on it can lead to bottlenecks in the development process by preventing other people from working on the same file at the same time. You should only lock a file while editing it if you are concerned that there will be a conflict resulting in a complicated manual merge operation. Where possible, prefer shared checkouts by selecting the lock type **None** when you check out the file. 

The following are common scenarios where using a lock is appropriate to avoid conflicts:
* You are modifying a binary file format, such as an image or a document that cannot be easily merged.
* You are making such widespread changes to a file that any other developer working on the same file would be very likely to make changes to the same lines as you.

If you want to avoid any possibility of conflicts, use a checkout lock, which prevents other people from checking out and checking in the same file. If you do lock a file, notify your teammates when you lock a file and tell them why you are doing so and how long your work on the file is likely to take. Also let them know when you remove the lock and check your changes back in.

You specify your lock type when you check out a file for editing, or you can explicitly lock a file. 

**To lock a file while checking it out**
# In Source Control Explorer, right-click the file and then click **Check Out for Edit**.
# Specify your lock type: **None**, **Check Out**, or **Check In**. 
# To explicitly lock a file, right-click the file, click **Lock**, and then select the **Check Out** or **Check In** lock type. 

Note that unlike Microsoft Visual Source Safe® (VSS) behavior, checking out a file does not implicitly get the latest version. Prior to locking a file, make sure that you have the latest version in your workspace by clicking **Get Latest Version**. 

#### Additional Resources
* For more information about locks, see “How to: Lock and Unlock Folders or Files” at [http://msdn2.microsoft.com/en-us/library/ms181420(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181420(VS.80).aspx) 
* For more informational about lock types, see [http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx) 

### Communicate with Your Teammates When Locking Files
If you do lock a source file, let your teammates know so that they can plan their work around the unavailability of the file. Explain why you need an exclusive lock on the file and how long you are likely to retain the lock. By locking a file, you potentially introduce a bottleneck into your development cycle, if other developers need to work on the same source file. 

Only lock a file while editing it if you are concerned that there will be a conflict resulting in a complicated manual merge operation. Where possible, prefer shared checkouts by selecting the lock type **None** when you check out the file. 

To lock a file from Source Control Explorer, right-click the file, click **Lock**, and then select the **Check Out** or **Check In** lock type. 

#### Additional Resources
* For more information on lock types, see [http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181419(VS.80).aspx) 

## Dependencies
* **Use project references whenever possible.**
* **Use file references only where necessary.**
* **Use copy local = true for project and file references.**
* **Use dynamic URLs when referencing Web services.**

### Use Project References Whenever Possible
You should use a project reference whenever possible because they provide the following advantages:
* They work on all development workstations where the solution and project set are loaded. This is because a project Globally Unique Identifier (GUID) is placed in the project file, which uniquely identifies the referenced project in the context of the current solution. 
* They enable the Visual Studio build system to track project dependencies and determine the correct project build orders. 
* They help you avoid the possibility of referenced assemblies being missing on a particular computer. 
* They automatically track project configuration changes. For example, when you build using a debug configuration, any project references refer to debug assemblies generated by the referenced projects, while they refer to release assemblies in a release configuration. This means that you can automatically switch from debug to release builds across projects without having to reset references. 
* They enable Visual Studio to detect and prevent circular dependencies.

You can use a project reference if the assembly is already within your solution’s project set. If the assembly is outside of your solution’s project set and you still want to use a project reference, you can branch the dependency from the originating project into your project. When you want to pick up a new version of the dependency, perform a merge from the originating project into your branch.

#### Additional Resources
* For more information about project and file references, see “Project References” at  [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)
* For more information about adding references, see “How to: Add or Remove References in Visual Studio” at [http://msdn2.microsoft.com/en-us/library/wkze6zky(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/wkze6zky(VS.80).aspx)

### Use File References Only Where Necessary
If you cannot use a project reference because you need to reference an assembly outside of your current solution’s project set, and you do not want to create a branch from the originating project into your project, you must set a file reference.

#### Additional Resources
* For more information about project and file references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)

### Use copy local = true for Project and File References
Every reference has an associated **copy local** attribute. Visual Studio determines the initial setting of this attribute (true or false) when the reference is initially added. It is set to false if the referenced assembly is found to be in the Global Assembly Cache (GAC); otherwise, it is set to true. 
You should not change this default setting. 

With **copy local** set to **true**, the Visual Studio build system copies any referenced assembly (and any dependent downstream assemblies) to the client project’s output folder when the reference is set. For example, if your client project references an assembly named Lib1, and Lib1 depends on Lib2 and Lib3, then Lib1, Lib2, and Lib3 are copied to your project’s local output folder automatically by Visual Studio at build time. 

#### Additional Resources
* For more information about project and file references, see “Project References” at [http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ez524kew(VS.80).aspx)

### Use Dynamic URLs When Referencing Web Services
If you want to call a Web service, you must first add a Web reference to your project. This generates a proxy class through which you interact with the Web service. The proxy code initially contains a static Uniform Resource Locator (URL) for the Web service; for example, http://localhost or http://SomeWebServer.

**Important:** For Web services in your current solution that execute on your computer, always use http://localhost rather than http://MyComputerName to ensure that the reference remains valid on all computers.

The static URL that is embedded within the proxy is usually not the URL that you require in either the production or test environment. Typically, the required URL varies as your application moves from development to test to production. You have three options to address this issue: 
* You can programmatically set the Web service URL when you create an instance of the proxy class. 
* A more flexible approach that avoids a hard-coded URL in the proxy is to set the **URL Behavior** property of the Web service reference to **Dynamic**. This is the preferred approach. When you set the property to **Dynamic**, code is added to the proxy class to retrieve the Web service URL from a custom configuration section of the application configuration file—Web.config for a Web application or SomeApp.exe.config for a Windows application. 
* You can also generate the proxy by using the WSDL.exe command-line tool and specifying the **/urlkey** switch. This works in a similar way to setting the **URL Behavior** property in that it adds code to the proxy to retrieve the Web service URL, but in this case the URL is stored in the <applicationSettings> section of the application configuration file.

The dynamic URL approach also lets you provide a user configuration file, which can override the main application configuration file. This allows separate developers (and members of the test team) to temporarily redirect a Web service reference to an alternate location.

#### Additional Resources
* For more information, see “Chapter 6 - Managing Source Control Dependencies in Visual Studio Team System” in this guide.

## Distributed / Remote Development
* **Make sure that you get an appropriately sized disk drive for your proxy.**
* **Create a scheduled task to pull the latest files on a periodic basis.** 
* **Periodically monitor proxy performance counters and the event log.**
* **Configure executionTimeout based on file sizes and bandwidth.**
* **Disable the proxy if it is going to be down for an extended time period.**
* **Consider workspace cloaking to reduce unnecessary file transfers.**

### Make Sure That You Get an Appropriately Sized Disk Drive for Your Proxy
Be sure to follow the hardware recommendations in the TFS installation guide; specifically, make sure that you get a disk drive with sufficient capacity. A maximum limit is set on the amount of storage space the proxy can use for caching files. When this limit is reached, old files in the cache are deleted to free up some storage space so that the space can be used for caching newly requested files. Cleanup removes the files based on when they were last accessed. Those files that have not been served for the longest time are deleted first.

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

### Create a Scheduled Task to Pull the Latest Files on a Periodic Basis 
Run a scheduled task to retrieve the latest files on a periodic basis to the proxy server. This helps to ensure that the latest version of the files are available in the proxy cache and to ensure that subsequent client requests for these files result in a cache hit.

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

### Periodically Monitor Proxy Performance Counters and the Event Log 
Monitor Proxy Performance counters and the Windows event log for errors and warnings on a periodic basis, to get a good picture of how your proxy is functioning. Make sure that proxy caching is enabled and monitor the performance of your cache. 

You should observe the following performance counters:
* Current Cache Size 
* Total Cache Hits - count and percentage 
* Total Download Requests 
* Total Files in Cache 
* Total Cache Miss - count and percentage

These performance counters are registered when you install the proxy. The proxy performance counters are multi-instanced, which means there is a set of counters for each application tier that you have configured in the Proxy.config file. By collecting this data, you get an understanding of the performance when the proxy server is running. 

Note that the TFS proxy saves cache performance statistics to an Extensible Markup Language (XML) file named ProxyStatistics.xml, and you can change the interval for saving these statistics. The ProxyStatistics.xml file is located in the App_Data folder in the proxy installation directory.

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

### Configure executionTimeout Based on File Sizes and Bandwidth
If you know that large files are going to be downloaded over a low-bandwidth (< 3 megabits per second [Mbps](Mbps)) network, set the **executionTimeout** configuration to an appropriate value in Web.config. Do this to reduce the likelihood of timeouts. The default value is one hour as shown here:
{{
<httpRuntime executionTimeout="3600"/>.
}}

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

### Disable the Proxy if It Is Going to Be Down for an Extended Time Period
Disable the proxy on the clients if the proxy is going to be down for an extended time period. Do this to prevent fruitless reconnections. By default, these are attempted every five minutes.

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

### Consider Workspace Cloaking to Reduce Unnecessary File Transfers
Consider using workspace cloaking to hide specific workspaces from being viewed and to prevent unnecessary file transfers. Cloaking not only hides specified workspace folders from view, but also increases performance bandwidth and conserves local disk space by preventing folders and files that you do not currently require from being copied to your local workspace. Although you can cloak an existing folder mapping in your workspace, a better approach is to create a new folder mapping specifically intended to be cloaked.

**To cloak folders in a workspace**
# In Visual Studio, on the **File** menu, point to **Source Control**, and then click **Workspaces**. 
# In the **Manage Workspaces** dialog box, select the workspace to which you want to apply cloaking, and then click **Edit**.
# In the **Edit Workspace** dialog box, in the **Working** **folders** list, either highlight the folder mapping located under **Source Control Folder** and **Local Folder** that you want to cloak, or create a new one. 
# Click in the **Status** column and change the setting from **Active** to **Cloaked**. - Note that you can only cloak folders in an actively mapped TFS source control folder.
# Click **OK** to close Edit Workspaces and click **Close** to close Manage Workspaces.

Note that your files do not disappear locally until you perform another **get** operation for the entire workspace. 

#### Additional Resources
* To learn more about the Team Foundation Server Proxy, see “Team Foundation Server Proxy and Source Control” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms252490(VS.80).aspx) 

## Migration
* **Use the VSS converter to migrate to Team Foundation Server Source Control.**
* **Migrate from other source-control systems to Team Foundation Server Source Control.**

### Use the VSS Converter to Migrate to Team Foundation Server Source Control
Team Foundation Server ships with a VSS converter tool that allows you to migrate files, folders, version history, labels, and user information from a Visual SourceSafe database to Team Foundation Server Version Control.  

The converter does have some limitations that are important to understand, for example:
* Historical information about file sharing is not preserved. Team Foundation Server does not support sharing. The migration of a shared file results in copying the file to the destination folder.
* Historical information about branching is not preserved.
* Team Foundation Server does not support pinning. Pinned files are migrated by creating two labels.
* Timestamps associated with actions are not preserved during migration.

#### Additional Resources
* For more information about migrating files, see “How To – Migrate Source Code to Team Foundation Server from Visual Source Safe” in this guide.

### Migrate from Other Source-Control Systems to Team Foundation Server Source Control
You can manually export files from the version-control system you are migrating from and then import them into Team Foundation Server Version Control. If you need to preserve file history or other attributes from the version-control system you are migrating from, you can use the TFS Migration and Synchronization Toolkit, available at [http://www.codeplex.com/MigrationSyncToolkit](http://www.codeplex.com/MigrationSyncToolkit), to write your own migration tool.

Microsoft is currently working on a ClearCase converter. When this converter is ready, it will be announced on the TFS Migration blog at [http://blogs.msdn.com/tfs_migration](http://blogs.msdn.com/tfs_migration) 

Component Software has created a converter that is compatible with GNU RCS, CS-RCS, GNU CVS, Subversion (SVN), and Visual SourceSafe (VSS).

#### Additional Resources
* For more information about TFS migration, see the “TFS Migration blog” on the MSDN Web site at [http://blogs.msdn.com/tfs_migration](http://blogs.msdn.com/tfs_migration) 
* To download the TFS Migration and Synchronization Toolkit from CodePlex, go to [http://www.codeplex.com/MigrationSyncToolkit](http://www.codeplex.com/MigrationSyncToolkit) 
* For more information about the Component Software converter, see [http://www.componentsoftware.com/%0bProducts/Converter/](http://www.componentsoftware.com/%0bProducts/Converter/)

## Project / Workspace Management
* **Isolate a single developer using workspaces rather than branches.**
* **Delete and rename files by using source control, not Windows Explorer.**
* **Only delete and rename with your solution open.**
* **Create one team project per application if you want to move your assets between application versions.**
* **Create one team project per version if you want to start fresh with each application version.**
* **Use branching to share code and binaries that require integration testing.**
* **Avoid workspace mapping to support cross-project dependencies.**
* **Create workspace mappings at the team project root level.**
* **Use a unique local folder path on shared computers.**
* **Consider mapping only part of the source tree.**
* **Structure your source tree to support branching.**

### Isolate a Single Developer Using Workspaces Rather Than Branches
To isolate your work from the rest of your team, use an additional workspace and do not create a new branch. Use your primary workspace to contain references to the files and folders being worked on by the rest of the team (that is, containing the shared source) and create a second workspace to maintain the files and folders that you want to isolate. You might want to isolate these files in order to evolve specific files in parallel with work that is happening elsewhere. For instance, this can be used to work on risky pending changes, or experimental changes. By using a second workspace, you reduce additional branch and merge complexity.

**To create a secondary workspace**
# In Source Control Explorer, click the **Workspace** drop-down list and then click **Workspaces**.
# In the **Manage Workspaces** dialog box, click **Add**.
# In the **Add** **Workspace** dialog box, enter a new workspace name such as **MyIsolatedWork** and provide a comment to serve as a future reminder about the purpose of the workspace.
# In the **Working** **folders** list, set the workplace status to **Active**, identify the source control folder to be included in the workspace (this can be the team project root folder or any subfolder), and specify a local folder path on your own computer to contain the files from the workspace. 
# Click **OK** and then click **Close** to create the isolated workspace.

**To retrieve the latest set of source to begin work in your isolated workspace**
# In Source Control Explorer, make sure that your isolated workspace name is selected in the **Workspace** drop-down list.
# Select your team project root folder (or a subfolder if you only need part of the source tree), right-click, and then click **Get Latest Version**. 
This copies the folder structure and latest file set from the source control server to the local directory on your computer that you mapped to the new workspace.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx) 
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

### Delete and Rename Files by Using Source Control, Not Windows Explorer
If you need to delete or rename files that have been added to source control, you should delete or rename them by using Source Control Explorer or by using Tf.exe from the command line. Do not delete or rename files by using Windows Explorer because doing so forces your local workspace files to become out of synchronization with the source control files maintained on the server. 

**To delete a file or folder by using Source Control Explorer**
# In Source Control Explorer, select the file or folder.
# Right-click the selected file or folder and then click **Delete**. 
An icon that indicates the item is deleted appears to the left and the status “delete” appears under the **Pending Change** column. The item is deleted the next time you check the file in. 

**Note:** You cannot delete an item for which another pending change exists. For example, a checked out file cannot be deleted.

The **Tf** **move**, **delete**, and **rename** commands are particularly useful if you need to perform the operation on multiple files or folders. With Source Control Explorer, you can only move, rename, or delete a single file or folder at a time.

#### Additional Resources
* For more information about the **Tf delete** command, see “Delete Command” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/k45zb450(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/k45zb450(VS.80).aspx) 
* For more information about the **Tf rename** command, see “Rename Command” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/a79bz90w(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/a79bz90w(VS.80).aspx) 

### Only Delete and Rename with Your Solution Open
Delete and rename files inside Solution Explorer only with your solution open. Do not do this directly on disk. This approach ensures that when you next check in your pending changes, TFS source control is kept in synchronization. 

#### Additional Resources
* For more information about the **Tf delete** command, see “Delete Command” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/k45zb450(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/k45zb450(VS.80).aspx) 
* For more information about the **Tf rename** command, see “Rename Command” on the MSDN Web site at [http://msdn2.microsoft.com/en-us/library/a79bz90w(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/a79bz90w(VS.80).aspx) 

### Create One Team Project per Application if You Want to Move Your Assets Between Application Versions
If you want to carry forward not only source code but also work items and other TFS assets between releases, consider using one team project per application. When you use a single team project for multiple versions of the application, all of the TFS assets are carried forward automatically for you for the next release. When you are ready to release a new version of your application, you can create a branch within the project to represent the release and isolate that code.

If you choose to use one project per application, keep the following vulnerabilities in mind:
* Releases in parallel are forced to share work item schemas, check in policies, and process guidance.  
* Reporting is more difficult. Because reports default to the entire project, you must add filtering by release.
* If you have hundreds of applications, each in its own project, you will run up against TFS performance and scale limits.
* You will accumulate ‘baggage’ over multiple releases. The easiest way to address this issue is to create a new project and then branch code you want to carry forward into that project.

#### Additional Resources
* For more information on using team projects, see “When to use Team Projects” at [http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx](http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx) 

### Create One Team Project per Version if You Want to Start Fresh With Each Application Version
If you want each release to start fresh without carrying forward work items and other TFS assets, consider using one project per release. When you use a new project for each release, you can modify work item schemas, workflow, check-in policies, and other assets without impacting the old release. This can be especially useful if the old release will be maintained by a separate team such as a sustained engineering team who may have a different process and workflow than your main development team.

When using one project per release, keep the following in mind:
* Although it is very easy to move the source code from one project to another, it is difficult to move work items and other TFS assets from one project to another. Work items can only be copied one at a time to another project; if you want to copy sets of work items, you will need to write your own utility.
* If you have hundreds of applications and releases, each in its own project, you will run up against TFS performance and scale limits.
* Choose a structure you can live with in the long term because restructuring existing team projects is difficult.
* Source can be easily shared among team projects:
	* Branch source from one project to another.
	* Map source from another project into your workspace.
* Team Foundation Server can scale to ~500 projects by using the Microsoft Solution Framework (MSF) for Agile Software Development (MSF Agile) process template or to 250 projects by using the MSF CMMI process template. If you create your own process, or customize an existing process, keep in mind that the work item schema has the greatest impact on server scalability. A complex schema will result in a server capable of supporting fewer projects. 

#### Additional Resources
* For more information on using team projects, see “When to use Team Projects” at [http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx](http://blogs.msdn.com/ericlee/archive/2006/08/09/when-to-use-team-projects.aspx) 

### Use Branching to Share Code and Binaries that Require Integration Testing
Managing shared code or binaries involves two steps: 
# Determine a location in which to store the dependency.
# Branch the dependency into your project.

1. **Determine a location in which to store the dependency.**
Options for storing:
* If the shared dependency is clearly owned by a particular team, store it in that team’s team project.
* If the shared dependency has no clear ownership, create a team project specifically for the shared code.

2. **Branch the dependency into your project.**
Once you have stored the dependency, branch the shared source or binaries into your project. Every time you perform a merge from shared to consuming project, you will pick up the latest source. This allows you to pick up changes on a regular schedule and to perform integration testing before impacting your main source tree.

#### Additional Resources
* For an introduction to branching and merging, see “Branching and Merging Primer” at [http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/aa730834(VS.80).aspx)    
* For more information about branching, see “How to: Branch Files and Folders” at [http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181425(VS.80).aspx) 
* For more information about merging, see “How to: Merge Files and Folders” at   [http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181428(VS.80).aspx) 
* For additional descriptions of how to branch and merge in Visual Studio 2005, see “Branching and Merging Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181423(VS.80).aspx)

### Avoid Workspace Mapping to Support Cross-Project Dependencies
In general, you should avoid dependencies that cross team projects and try to have all the related/dependent solutions/projects under the same team project. This reduces the need for build script customization. If you have a dependency, use project references to define it, or branch the dependency from a shared project into your project. You should avoid file references because they are more difficult to manage. The exception is when the dependent project is developed in parallel and you need real-time changes. In this case, you can consider using workspace mapping. However, you can still use branching in this case to create a buffer of isolation, if the dependent code is causing too many breaking changes.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)   
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

### Create Workspace Mappings at the Team Project Root Level
For new team projects, map your team project root ($/MyTeamProject) to a folder with the same name on your local drive; for example, C:\TeamProjects. Because mappings are recursive, your entire local folder structure is created automatically and will be exactly the same as the structure in source control.

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)   
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

### Use a Unique Local Folder Path on Shared Computers
Two users of a single computer cannot share the same workspace mapping. For example, you and a colleague cannot map the same team project ($/MyTeamProject) to the same folder on the local computer. Instead, create mappings beneath My Documents (although this leads to long location paths) or establish a team folder naming convention on the local computer (for example, C:\TeamProjects\User1, C:\TeampProjects\User2 etc).

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)   
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

### Consider Mapping Only Part of the Source Tree
To improve performance and reduce disk-size requirements, only map the files you need for your development project. In general, you will only need the files and projects associated with the solution on which you will be working.  

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)   
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

### Structure Your Source Tree to Support Branching
Your source tree structure consists of a combination of folder structure, file structure, and branch structure. Within your main branch, the following folder and file structure has been proven to work for teams of various sizes:

* **Main** - container for all assets you need in order to ship the product
	* **Source** - container for everything you need to build
		* **Code** - container for source code
		* **Shared Code** – container for source code that is shared from other projects
		* **Unit Tests** - container for unit tests
		* **Lib** - container for binary dependencies
	* **Docs** - container for documentation that will ship with the product 
	* **Installer** - container for installer source code and binaries 
	* **Tests** - container for test team test cases 

Any branches that you create off of **Main** will copy this folder and file structure into the new branch; for example:

* **Development** – Development branch
	* **Source** - container for everything you need to build
		* **Code** - container for source code
		* **Shared Code** – container for source code that is shared from other projects
		* **Unit Tests** - container for unit tests
		* **Lib** - container for binary dependencies
* **Main** – Integration branch
	* **Source** - container for everything you need to build
		* **Code** - container for source code
		* **Shared Code** – container for source code that is shared from other projects
		* **Unit Tests** - container for unit tests
		* **Lib** - container for binary dependencies
	* **Docs** - container for documentation that will ship with the product 
	* **Installer** - container for installer source code and binaries 
	* **Tests** - container for test team test cases

#### Additional Resources
* For more information about creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)   
* For more information about editing a workspace, see “How to: Edit a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms245466(VS.80).aspx) 

## Shelving
* **Use shelving to share pending changes for review or handoff.**
* **Use shelving to back up pending changes to the server.**
* **Use shelving if interrupted by higher-priority work.**

### Use Shelving to Share Pending Changes for Review or Handoff
Use shelving if you want to discuss or review your work-in-progress code with a remote team member. Rather than e-mailing the code to your teammate, you can shelve the code and then have your remote colleague retrieve the files from the shelf.

Similarly, if you want to pass partially finished work to another developer for completion, you can use shelving to hand the code off.

#### Additional Resources
* For more information on shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)  

### Use Shelving to Back Up Pending Changes to the Server
Use shelving if you have not completed work at the end of the day but want to ensure that your current work is backed up on the server. By shelving your current changes, the changes are applied to the TFS server and can be retrieved by you (or others) the next day. 

#### Additional Resources
* For more information on shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)  

### Use Shelving if Interrupted by Higher-Priority Work
Use shelving if you are midway through making changes to a set of source code, when new higher-priority work is allocated (for example, an emergency bug fix is required). At this point, you need to go back to a stable version of the code but you do not want to lose your changes. Before doing so, you can shelve your code and easily retrieve it later.

#### Additional Resources
* For more information on shelving pending changes, see “How to: Shelve and Unshelve Pending Changes” at [http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181404(VS.80).aspx)  

## Source Control Resources
* For more information on Team Foundation Server Source Control, see “Team Foundation Source Control” at [http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181237(VS.80).aspx)