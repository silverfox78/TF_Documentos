### How To: Create Custom Check-in Policies in Visual Studio Team Foundation Server 
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Applies To
* Microsoft® Visual Studio® 2005 Team Foundation Server (TFS)
* Microsoft Visual Studio Team System

### Summary
This How To article walks you through the process of creating, registering, and applying a custom check-in policy for TFS. Check-in polices allow you to run rules whenever a developer attempts to check-in a source file, in order to ensure that the source file being checked-in meets a specified set of criteria. As an example, this How To article uses a custom policy to enforce that check-in comments are supplied with all check-ins. To implement a custom check-in policy, you create a class that derives from **PolicyBase** and implements the **IPolicyDefinition** and **IPolicyEvaluation** interfaces. You register the policy assembly in the Microsoft Windows® registry and you apply the policy to your team project.

### Contents
* Objectives
* Overview
* Before You Begin
* Summary of Steps
* Step 1 – Create and Build a Custom Policy Class.
* Step 2 – Register the Custom Policy Class in the Windows Registry
* Step 3 – Apply the Custom Policy.
* Step 4 – Validate the Custom Policy.
* Additional Considerations

### Objectives
* Learn what a custom check-in policy is 
* Learn how to create, register, and apply custom check-in policies.

### Overview
_Check-in policies_ enforce constraints whenever files are checked into source control. Team Foundation Server provides a number of out-of-box check-in policies including policies to check that unit tests have run and been passed, policies to perform static code analysis to ensure that code meets coding standards and .NET guidelines, and policies to check that work items are associated with check ins. The Microsoft Visual Studio 2005 Team Foundation Power Tool also provides a number of additional check-in policies. In this How To article, you will learn how to create, register, and apply a custom policy. The example policy ensures that developers supply check-in comments whenever they check in a file.

### Before You Begin
Note that, to create a check-in policy, you must have the **Manipulate** security settings permission set to **Allow**.

### Summary of Steps
* Step 1 – Create and Build a Custom Policy Class
* Step 2 – Register the Custom Policy in the Windows Registry
* Step 3 – Apply the Custom Policy
* Step 4 – Validate the Custom Policy

### Step 1 – Create and Build a Custom Policy Class
In this initial step, you create a custom policy class by deriving from the **PolicyBase** base class in the **Microsoft.TeamFoundation.VersionControl.Client** namespace. By deriving from this base class, your class implements the **IPolicyDefinition** and **IPolicyEvaluation** interfaces. The example policy code below forces a developer to supply check-in comments whenever he or she checks in a source file.

# Use Visual Studio to create a new Visual C#® class library project.
# Add an assembly reference to **System.Windows.Forms.dll**. You use this assembly to display message boxes.
# Add an assembly reference to **Microsoft.TeamFoundation.VersionControl.Client.dll.** By default, this is installed in the following folder: \Program Files\Visual Studio 2005 Team Foundation Server\Tools
# Replace your skeleton class code implementation with the following source. Note that the class derives from the **PolicyBase** base class and is marked as serializable.


{{ using System;
using System.Windows.Forms;
using Microsoft.TeamFoundation.VersionControl.Client;

[Serializable](Serializable)
public class CheckForCommentsPolicy : PolicyBase
{
    public override string Description
    {
        get { return "Remind users to add meaningful comments to their checkins"; }
    }

    // This is a string that is stored with the policy definition on the source
    // control server. If a user does not have the policy plug-in installed, this string
    // is displayed.  You can use this to explain to the user how they should 
            // install the policy plug-in.
    public override string InstallationInstructions
    {
        get { return "To install this policy, read InstallInstructions.txt."; }
    }

    // This string identifies the type of policy. It is displayed in the 
 // policy list when you add a new policy to a Team Project.
    public override string Type
    {
        get { return "Check for Comments Policy"; }
    }

    // This string is a description of the type of policy. It is displayed 
    // when you select the policy in the Add Check-in Policy dialog box.
    public override string TypeDescription
    {
        get { return "This policy will prompt the user to decide whether or not they should be allowed to check in."; }
    }

    // This method is called by the policy framework when you create 
    // a new check-in policy or edit an existing check-in policy.
    // You can use this to display a UI specific to this policy type 
    // allowing the user to change the parameters of the policy.
    public override bool Edit(IPolicyEditArgs args)
    {
        // Do not need any custom configuration
        return true;
    }

    // This method performs the actual policy evaluation. 
    // It is called by the policy framework at various points in time
    // when policy should be evaluated. In this example, the method 
    // is invoked when various asyc events occur that may have 
    // invalidated the current list of failures.
    public override PolicyFailure[]() Evaluate()
    {
        string proposedComment = PendingCheckin.PendingChanges.Comment;
        if (String.IsNullOrEmpty(proposedComment))
        {
            return new PolicyFailure[]() {
                new PolicyFailure("Please provide some comments about your check-in", this) };
        }
        else
        {
            return new PolicyFailure[0](0);
        }
    }

    // This method is called if the user double-clicks on 
    // a policy failure in the UI. In this case a message telling the user 
    // to supply some comments is displayed.
    public override void Activate(PolicyFailure failure)
    {
        MessageBox.Show("Please provide comments for your check-in.", "How to fix your policy failure");
    }

    // This method is called if the user presses F1 when a policy failure 
    // is active in the UI. In this example, a message box is displayed.
    public override void DisplayHelp(PolicyFailure failure)
    {
        MessageBox.Show("This policy helps you to remember to add comments to your check-ins.", "Prompt Policy Help");
    }
} }}

### Step 2 – Register the Custom Policy in the Windows Registry
In this step, you add an entry to the Windows registry so that your policy appears in the **Add Check-in Policy** dialog box. Note that you must install the policy assembly on any computer that needs to reference the assembly. This includes the computer of the team project’s administrator who needs to associate the policy with the team project and on all of your team members’ computers where the policy is actually evaluated. 

**Important**: The policy is evaluated on the client when a developer checks in a file.

# Start Regedit.exe and locate the following key 
## HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\TeamFoundation\SourceControl\Checkin Policies 
## The registered policies are listed in the right pane. 
# Right-click in the right-hand pane, point to **New,** and then click **String Value**.
# Type the name of your custom policy dynamic link library (DLL), without the DLL extension; **CheckForCommentsPolicy** in the above example.
## **Important**: The new string name must match your DLL filename exactly, without the DLL extension.
# Double-click the new string value and set its value to the fully qualified path and filename to the .dll containing your custom policy.

### Step 3 – Apply the Custom Policy
In this step you add the custom policy to your team project. This ensures that the policy is evaluated each time a developer checks in a file to this team project.

# In **Team Explorer**, right-click your team project, point to **Team Project Settings** and then click **Source Control**.
# Click the **Check-in Policy** tab and then click **Add**.
# Select your custom **Check for Comments Policy** and click **OK** and then **OK** again.

The policy is now applied each time a developer checks a file into this team project.

### Step 4 – Validate the Custom Policy
In this step, you check-in a source file to ensure that the custom policy works correctly.

# Make a change to a source file and then check-in the file without supplying a check-in comment. 
# Verify that the check-in is prevented because the policy rule is not satisfied. 
# Add some comments and complete the check-in. With a supplied comment the check-in should work successfully and you will not see a policy failure notification.

### Additional Resources
* To learn how to customize a check-in policy, see “Walkthrough: Customizing Check-in Policies and Notes” at [http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181281(VS.80).aspx) 
* To see sample code that will disallow selected patterns on check-in, see “Check-in Policy to Disallow Certain Patterns” at [http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/02/523125.aspx)
* To see sample code that will enforce comments on check-in, see “Sample Check-in Policy: Make Sure the Comment Isn't Empty” at [http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx](http://blogs.msdn.com/jmanning/archive/2006/01/21/515858.aspx)
* To learn how to register a new check-in policy, see “I've Made a New Check-In Policy! How Do I Add It?” at [http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx](http://blogs.msdn.com/jmanning/archive/2006/02/07/526778.aspx)