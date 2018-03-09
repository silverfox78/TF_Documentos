### How To: Structure Your Source Control Folders in Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)

### Summary
This How To article walks you through the process of structuring your folders in TFS. The recommendations in this article were created using lessons learned in practice by Microsoft teams as well as Microsoft customers in the field. The folder structure presented here is a starting point; more important than the structure is the rationale behind it. Use the rationale to help evaluate an appropriate folder structure and folder-naming convention for your own scenario.

### Contents
* Objectives
* Overview
* Summary of Steps
* Step 1 – Create a Workspace Mapping
* Step 2 – Create Your Main Folder
* Step 3 – Create Folders for Your Project Artifacts
* Step 4 – Add Your Solution to Your Source Tree
* Step 5 – Create a Branched Development Folder for Isolation (Optional)
* Step 6 – Create a Releases Folder for Release Builds Isolation (Optional)
* Additional Resources

### Objectives
* Learn how to create a workspace mapping.
* Learn how to structure and name your source control folders.
* Learn how branching effects your source structure.

### Overview
This How To article shows you how to build an appropriate source control folder structure that you can use with most common project types. The folder structure presented in this article uses three top level folders:

* **Main**. This is the main root folder that acts as a container folder for your main source tree, together with accompanying project artifacts such as design documentation, scripts, and test cases. The **Main** folder also contains your Visual Studio Solution (.sln) files.
* **Development**. This is an optional root-level folder that you can use if you need to create isolation for features or teams development. This folder is created by branching from **Main**.
* **Releases**. This is an optional root-level folder for released builds that you need to isolate; for example for ongoing maintenance of a particular release. 

The folder structure presented in this article is summarized here:
{{
**/Main** 					? Can contain solution (.sln) files
							     for solutions that span projects	
/Source
		/MyApp1				? Contains MyApp1.sln file 
			/Source			? Contain folder for all source
				/ClassLibrary1	? Contains ClassLibrary1.csproj 
				/MyApp1Web 	? Contains Default.aspx
/Build						? Contains build output (binaries)
	/Docs					? Contains product docs etc
	/Tests					? Container for tests

**/Development**
	/FeatureBranch1
		/Source
			/MyApp1
				/Source
					/MyApp1Web
					/ClassLibrary1
	/FeatureBranch2

/**Releases**
/Release1
	/Source
			/MyApp1
				/Source
					/MyApp1Web
					/ClassLibrary1
/Release 1.1
/Release 1.2
}}
Remember that this folder structure is only a starting point with a suggested set of folder names. More important than the structure and naming convention is the rationale behind them and the purposes of the different folders. For more information about the rationale behind this structure, see “Chapter 5 – Defining Your Branching and Merging Strategy.”

### Summary of Steps
* Step 1 – Create a Workspace Mapping
* Step 2 – Create Your **Main** Folder
* Step 3 – Create Folders for Your Project Artifacts
* Step 4 – Add Your Solution to Your Source Tree
* Step 5 – Create a Branched **Development** Folder for Isolation (Optional)
* Step 6 – Create a **Releases** Folder for Release Builds Isolation (Optional)

### Step 1 – Create a Workspace Mapping
In this initial step you create a workspace mapping to define the mapping between the folder structure on the TFS server and client. You need to do this so that you can create a source tree structure. You first create the source tree structure in your workspace and then perform a check-in to your TFS server.

You can create a workspace mapping in one of two ways:

* **Set the workspace mapping explicitly** 
* **Perform a Get operation on your team project.**

**To set a workspace mapping explicitly**
# In Visual Studio, on the **File** menu, point to **Source Control** and then click **Workspaces**.
# In the **Manage Workspaces** dialog box, select your computer name and then click **Edit**.
# In the **Edit Workspace** dialog box, in the **Working folders** list, click **Click here to enter a new working folder**. 
# Click the ellipsis (**…**) button, select your team project (for example **MyTeamProject1**), and then click **OK**.
# Click the local folder cell to display another ellipsis button.
# Click the ellipsis button beneath **Local Folder** and then browse to and select the local folder on your development computer where you want to locate your team project; for example, C:\DevProjects\MyTeamProject1. 
# Click **OK** twice to close the **Edit Workspace** dialog box**.** 
# Click **OK** in response to the Microsoft Visual Studio message box that informs you than one or more working folders have changed.
# Click **Close** to close the **Manage** **Workspaces** dialog box.
  
**To perform a Get operation on your team project**
# In **Team Explorer**, expand your team project node; for example, **MyTeamProject1**.
# Double-click **Source Control** beneath your team project.
# In **Source Control Explorer**, right-click the root folder **MyTeamProject1** and then click **Get Latest Version**.  
# In the **Browse For Folder** dialog box, select your local path (for example, C:\DevProjects\MyTeamProject1) and then click **OK**. This maps the team project root folder within TFS to a local path on your computer.

### Step 2 – Create Your Main Folder
In this step, you create a new root folder named **Main** in your Team Project source control. You use the **Main** folder as a root-level container folder for your source and other project artifacts. You can also use the **Main** folder to store any Visual Studio solution (.sln) files that span multiple projects. Solution files are also maintained in their own application folders lower in the tree structure.

**To create a Main folder:**
# In Team Explorer, expand your team project and then double-click **Source Control**.
# In Source Control Explorer, select your Team Project root folder.
# Right-click in the right-hand pane and then click **New Folder**.
# Type **Main** and then press ENTER.

### Step 3 – Create Folders for Your Project Artifacts
In this step, you create folders beneath **Main** to hold your main source code tree and accompanying artifacts such as builds, documentation, script files and tests as shown below:
{{
**/Main**
	/Build
	/Docs
	/Source
	/Tests }}}

**To create folders for your project assets:**
# Expand your team project and then in the left pane of Source Control Explorer, select the **Main** folder.
# Right-click in the right pane, click **New Folder**, type **Build** and then press ENTER.
# Repeat step 2 to create the remaining folders beneath **Main**.

### Step 4 – Add Your Solution to Your Source Tree
In this step, you add your Visual Studio solution (.sln), project (.vsproj, .vbproj) and source files to your source tree in TFS source control. 

Because you have mapped your root node to C:\DevProjects\MyTeamProject1 in Step 1, make sure the client folder structure and project structure are synchronized. Your solution (.sln) file should be at the following location:
C:\DevProjects\MyTeamProject1\Main\Source\MyApp1

The actual project-related files for MyApp1Web and ClassLibrary1 components should be at the following location:
C:\DevProjects\MyTeamProject1\Main\Source\MyApp1\Source

**To add the solution to your source tree:**
# Open your solution in Visual Studio.
# In Solution Explorer, right-click your solution and then click **Add Solution to Source Control**. Because you have already established a workspace mapping in Step 1, the solution is added at this point. 
# Make sure that the correct **Local Workspace** is selected. This should be the same workspace that you used while creating your folder structure in TFS source control. 
# Click **OK** to add your solution to source control.

You source control folder structure should resemble the following:
{{
**/Main**
	/Source
		/MyApp1
			/Source
				/MyApp1Web
				/ClassLibrary1
/Build
	/Docs
	/Tests
}}

For more information about how to setup an appropriate client-side folder structure, see:
* How To – Structure Windows Applications in Visual Studio Team Foundation Server.
* How To – Structure ASP.NET Applications in Visual Studio Team Foundation Server.

#### Creating a Folder Structure When a Project Has Unit Tests
If your project also includes unit tests, consider creating the following folder structure to store your unit tests separate from your main source folder:
{{
**/Main**
	/Source
		/MyApp1
			/Source
				/MyApp1Web
				/ClassLibrary1
	**		/UnitTests**
/Build
	/Docs
	/Tests }}

### Step 5 – Create a Branched Development Folder for Isolation (Optional)
If you need to isolate for features or teams, consider creating a **Development** folder by branching from the **Main** folder. Note that if you do so, you must check any pending changes before you can branch.

To create a branched **Development** folder:

# Create a root level **Development** folder (as a sibling of **Main**).
# Create a sub folder named **FeatureBranch1**.
# Select the $/TeamProject/Main/Source folder, right-click the folder, and then click **Branch**. **Note**: If **Branch** is grayed out, make sure you have checked in any pending changes.
# In the **Branch** dialog box, click **Browse,** select MyTeamProject/Development/FeatureBranch1, and then click **OK**.
# Click **OK** to create the branch.
# Check-in your pending changes to push them to the server.

Your new folder structure in source control should resemble the following example: 
{{
**/Development**
	**/FeatureBranch1**
		**/Source**
			/MyApp1
				/Source
					/MyApp1Web
					/ClassLibrary1
	**/FeatureBranch2**

**/Main**
	**/Source**
		/MyApp1
			/Source
				/MyApp1Web
				/ClassLibrary1
	/Build
	/Docs
	/Source
	/Tests
}}

### Step 6 – Create a Releases Folder for Release Builds Isolation (Optional)
If you need to perform maintenance on a previously released build, while continuing development, consider isolating the maintenance work by creating a **Releases** folder. Beneath this folder you can create multiple sub folders, one per release.

**To create a branched Releases folder:**
# Create a root-level **Releases** folder (as a sibling of **Main** and **Development**).
# Create a sub folder named **Release1**.
# Select the $/TeamProject/Development/Source folder, right-click the folder and then click **Branch**. **Note**: If **Branch** is grayed out, make sure you have checked in any pending changes.
# In the **Branch** dialog box, click **Browse** select $/TeamProject/Maintenance/Release1, and then click **OK**.
# In the **Branch from version** section, in the **By** list box, click **Label** and enter a label name in the **Label** text box.**** To find a label, click the browse button with the ellipses (**…**) next to the **Label** text box.
# Click **OK** to create the branch.

Your new folder structure in source control should resemble the following example one shown here.
{{
**/Main**
	**/Source**
		/MyApp1
			/Source
				/MyApp1Web
				/ClassLibrary1
	/Build
	/Docs
	/Source
	/Tests

**/Releases**
	/Release1
		/Source
			/MyApp1
				/Source
					/MyApp1Web
					/ClassLibrary1
	/Release 1.1
	/Release 1.2

}}

### Additional Considerations
Keep in mind the following key considerations when structuring your source control folders in TFS:
* Do not branch unless you need to. You can label releases and branch at a later time if you need isolation.
* The above folder structure is ideally suited to scenarios where your project consists of one Visual Studio solution (.sln) file containing all of your project files. In this scenario, the **Main** folder contains the .sln file and you have one subfolder for each project file (.vsproj, .vbproj). In the above example project folders are represented by MyApp1, MyApp2 etc. You can also use the above approach for a single project file; for example, if you use a single project, with no solution file.
* For multiple-solution scenarios, you can locate multiple .sln files in the **Main** folder.

### Additional Resources
* For more information on creating a workspace, see “How To: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)