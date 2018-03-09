### How To: Structure Windows Applications in Visual Studio Team Foundation Server
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® Team Foundation Server (TFS)
* Microsoft Visual Studio Team System (VSTS)
* Microsoft Windows® Form Applications

### Summary
This How To article walks you through the process of organizing and structuring your Windows Form applications for Team Foundation Server. The article explains an appropriate source tree structure to use within TFS source control. 

### Contents
* Objectives
* Overview
* Summary of Steps
* Step 1 – Create Local Folders for Your Windows Forms Project
* Step 2 – Create a Blank Solution
* Step 3 – Add a Windows Forms Project to Your Solution
* Step 4 – Add a Control Library (Optional)
* Step 5 – Add a Class Library (Optional)
* Step 6 – Check Your Solution Structure
* Step 7 – Check Your Local Folder Structure
* Step 8 – Add Your Solution to Source Control
* Shared Code Considerations
* Additional Resources

### Objectives
* Learn how to structure a Windows Forms application in TFS source control.
* Learn about an appropriate tree structure to use within TFS source control.

### Overview
This How To article shows you how to build a source control folder structure that is appropriate for Windows Forms applications. Because Windows Forms projects often include additional class and control libraries, a structure is required to accommodate these as well. Folders in which to maintain your Windows Forms projects are located beneath a **/Main/Source** top-level structure. This enables you to easily use additional **Development** and **Releases** folders if you need to create branches for isolated development and for release maintenance. For more information about creating this top level folder structure, see “How To: Structure Your Source Control Folders in Visual Studio team Foundation Server.”

### Summary of Steps
* Step 1 – Create Local Folders for Your Windows Forms Project
* Step 2 – Create a Blank Solution
* Step 3 – Add a Windows Forms Project to Your Solution
* Step 4 – Add a Control Library (Optional)
* Step 5 – Add a Class Library (Optional)
* Step 6 – Check Your Solution Structure
* Step 7 – Check Your Local Folder Structure
* Step 8 – Add Your Solution to Source Control

### Step 1 – Create Local Folders for Your Windows Forms Project
In this step, you create an appropriate local folder structure for your Windows Forms project on your development computer. To ensure a consistent approach for your team development and to keep team projects well organized on your development computer, you should keep your entire development source from all of the team projects you are working on grouped together beneath a single root folder such as C:\DevProjects.

Create a top-level folder such as C:\DevProjects.

### Step 2 – Create a Blank Solution
To create a Windows Forms application, start by explicitly creating a Visual Studio Solution (.sln) file and then add your Windows Forms project and any supplementary projects you might need, such as class or control libraries. In the following steps, you create your solutions beneath a top-level C:\DevProjects directory.

# On the **File** menu, point to **New** and then click** Project**.
# Expand **Other Project Types** and then select **Visual Studio Solutions**.
# Select **Blank Solution**.
# Name your solution **MyApp**.
# Set the **Location** to C:\DevProjects and then click **OK**.

This creates a C:\DevProjects\MyApp folder. Visual Studio adds the solution (.sln) file and solution user options (.suo) file to this folder. Note that only the .sln file is subsequently added to source control in Step 8.

### Step 3 – Add a Windows Forms Project to Your Solution
In this step, you add a new Windows Forms project to your solution.

# In **Solution Explorer**, right-click **Solution MyApp**, point to **Add,** and then click **New Project…**.
# In the **Add New Project** dialog box, select **Visual C#** as the project type and **Windows Application** as the template.
# Set the **Location** to C:\DevProjects\MyApp\Source directory.
# Name your project as **MyWinFormApp**.
# Click **OK** to close the **Add New Project** dialog box and add your project.

### Step 4 – Add a Control Library (Optional)
If your Windows Forms application requires additional control libraries, add them as follows:

# In **Solution Explorer**, right-click your solution, point to** Add,** and then click **New Project…**.
# In the **Add New Project** dialog box, select **Visual C#** as the project type and **Windows Control Library** as the template.
# Set the **Location** to C:\DevProjects\MyApp\Source directory.
# Name your Windows Control Library as **ControlLibrary**.
# Click **OK** to close the **Add New Project** dialog box.

### Step 5 – Add a Class Library (Optional)
If your Windows Forms application requires additional class library projects, add them as follows:

# In **Solution Explorer**, right-click your solution, point to** Add,** and then click **New Project…**.
# In the **Add New Project** dialog box, select **Visual C#** as the project type and **Class Library** as the template.
# Set the **Location** to C:\DevProjects\MyApp\Source directory.
# Name your Windows Class Library as **ClassLibrary1**
# Click **OK** to close the **Add New Project** dialog box.

### Step 6 – Check Your Solution Structure
Use Solution Explorer to verify your solution structure. It should resemble the following:

![](How To - Structure Windows Applications in Visual Studio Team Foundation Server_windows.gif) 

### Step 7 – Check Your Local Folder Structure 
Use Windows Explorer to verify your local folder structure. It should resemble the following:
![](How To - Structure Windows Applications in Visual Studio Team Foundation Server_windows1.gif)
 
### Step 8 – Add Your Solution to Source Control
In this step, you add your solution containing your Windows Form project, optional class libraries, and control libraries to TFS source control.

# Right-click **MyApp** and then click **Add Solution to Source Control**.
# In the **Add Solution MyApp to Source Control** dialog box, choose your team project.
# In the dialog box, click **Make New Folder** and then name the new folder as **Main.**
# Select the newly created **Main** folder, click **Make New Folder**, and then name the new folder as **Source**. 
# Select the newly created **Source** folder and then click **OK**.
# Check your source control folder structure by double-clicking **Source Control** within the **Team Explorer**. This displays Source Control Explorer. Your structure should resemble the following:

![](How To - Structure Windows Applications in Visual Studio Team Foundation Server_windows2.gif) 

# At this point you can view pending changes and check your source files into the server. To do so, on the **View Menu**, point to **Other Windows** and then click **Pending Changes**. Select your project and the source files to be checked-in, supply a check-in comment, and then click **Check In**.

### Shared Code Considerations
For Windows Forms applications that reference shared source code, you can consider the following two main options:

* **Reference the code from a shared location**
* **Branch the shared code**

#### Reference the Code from a Shared Location
With this approach, you map the source from a shared location such as another team project into the workspace on your development computer. This creates a configuration that unifies the shared source from the shared location with your project code on your development computer. 

The advantage of this approach is that any changes to the shared source are picked up every time you retrieve the latest version of the source into your workspace. For example consider a team project named Common that contains the shared source. To reference the code from this location, you map both team projects to a common path location on your development computer. For example: 
* C:\MyProjects\MyApp\ 
* C:\MyProjects\SharedCommon\  
The following workspace mappings are used: 
||**Source Control Folder**	||**Local Folder** ||
||$/MyTeamProject1/Main/Source/MyApp	||C:\DevProjects\MyApp||
||$/MyTeamProject2/Main/Source/Common	||C:\DevProjects\Common||

For more information, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx) 

#### Branch the Shared Code
With this approach, you branch the shared code from the common team project into your team project. This also creates a configuration that unifies the source from the shared location and your project. 

The difference with this approach is that the shared source changes are picked up as part of a merge process between the branches. This makes the decision to pick up changes in the shared source much more explicit. You decide when to perform a merge to pick up latest changes.

For example consider the team project named **Common** that contains shared source. To branch the code from this location:

# In **Source Control Explorer**, right-click the root folder of the **Common** team project.
# Click **Branch…** 
# In the **Branch** dialog box, set the **Target:** to the root folder of the $/MyTeamProject1/Main/Source/ team project, and then click **OK**.
# After the branch operation has completed, do not forget to check-in the branched source code. 

### Additional Resources
* For more information on creating a workspace, see “How to: Create a Workspace” at [http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181384(VS.80).aspx)
* For more information on referencing assemblies in different team projects, see “Working with multiple team projects in Team Build” at [http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx](http://blogs.msdn.com/manishagarwal/archive/2005/12/22/506635.aspx)