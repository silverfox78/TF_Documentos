### Chapter 9 - Setting Up Scheduled Builds with Team Build
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Understand the purpose of a scheduled build.
* Setup a scheduled build with Microsoft® Visual Studio® Team System Team Build.

### Overview
This chapter explains how you can set up scheduled builds by using Team Build and Microsoft Visual Studio Team Foundation Server (TFS). The purpose of a scheduled build is to automate the process of creating a reliable build on a consistent schedule. This is the type of build most often used by test teams, internal adopters, and external beta users.

Scheduled builds are the simplest form of build automation. You can configure scheduled builds to run hourly, daily, weekly, or at any time interval that works best for your team.  

### How to Use This Chapter
Use this chapter to learn strategies for scheduled builds and to learn how to set up and configure scheduled builds by using Team Build. For a step-by-step walkthrough to help you set up a scheduled build see, “How To: Set Up a Scheduled Build.” 

If you are new to TFS and Team Build, or if you want to learn more about the options available for automating and scheduling builds, read “Chapter 7 - Team Build Explained” before reading this chapter.

If you are concerned about build instability caused by the quality of the code that your development team checks in, you should consider using continuous integration builds. For more information about continuous integration, see “Chapter 8 - Setting Up Continuous Integration with Team Build.”  

### Strategy for Scheduled Build Frequency
The frequency of your builds is one of the most important decisions to make, when creating a scheduled build. You can choose to schedule your builds at an hourly, nightly, or weekly basis.

#### Hourly Builds
If you are working on a project that has enough check-ins to cause significant changes within an hour, and you do not employ continuous integration builds you can choose an hourly build frequency. Hourly builds to provide rapid feedback to developers and can also be made available to testers and other team members to solicit their feedback.

#### Nightly Builds
This is the most common scheduled build frequency because it gives your test and development team a new build every morning incorporating the changes from the previous day, ready to be tested.  

#### Weekly Builds
If you are working on a large, complex project, where the build time can last for days, you should opt for weekly builds. This ensures that your test team has a build at the start of each week incorporating the changes from the previous week, ready to be tested.   

### Scheduled Build in Team Foundation Server
The Team Build feature in TFS does not support scheduled builds from the user interface. Instead, you can use the Microsoft Windows® Task Scheduler to run the TFSBuild command utility to start builds at predetermined time.

Use the following steps to create a scheduled build:
* Create a TFSBuild command line.
{{ TfsBuild start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

* Place the command line in a batch file. Note that you must specify the full path to the TFSBuild.exe file so that it can run from windows command prompt. An example of the command used in the batch file is shown here:

{{ "C:\Program Files\Microsoft Visual Studio 8\Common7\IDE\TFSBuild" start <<TeamFoundationServer>> <<TeamProject>> <<BuildTypeName>> }}

* Create a Windows Scheduled Task that runs the batch file at your desired interval.

For more information see “How To: Set Up a Scheduled Build in Visual Studio Team Foundation Server.”

### Summary
Use a scheduled build to produce consistent builds that you can give to your test team or other build consumers who can provide feedback on the quality of the build. Team Foundation Server does not support scheduled builds from its user interface. Instead you can use the Windows Task Scheduler to run the TFSBuild command utility to start your builds at a predetermined time.

You can configure scheduled builds to run hourly, daily, weekly, or at any time interval that suits the requirements of your project.

### Additional Resources
* For more information about setting up a scheduled build see, “How To – Configure a Scheduled Build (Command Line)” at [http://msdn2.microsoft.com/en-us/library/ms181727(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms181727(VS.80).aspx)