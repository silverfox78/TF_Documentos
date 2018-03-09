### Chapter 8 - Setting Up Continuous Integration with Team Build
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Understand the purpose of a continuous integration build.
* Set up continuous integration by using Microsoft® Visual Studio® Team System Team Build.
* Optimize your continuous integration build to reduce bottlenecks.

### Overview
This chapter explains how you can set up continuous integration builds with Team Build and Microsoft Visual Studio Team Foundation Server (TFS). You use continuous integration builds to gain rapid feedback on build quality as soon after a check-in as possible. During team development, it is important to get rapid feedback on the quality of check-ins, especially if they combine with other developer’s changes and break the build. A continuous integration build gives you the chance to fix code quickly in order to unblock other team members, thereby improving the consistency and quality of your build. 

Team Foundation Server does not support continuous integration builds by default. It is possible, with the help of a Microsoft-supplied extension, to extend the build engine to support continuous integration.

### How to Use This Chapter
Use this chapter to learn strategies for continuous integration and to learn how to set up and configure continuous integration builds with Team Build. For a step-by-step walkthrough to help you set up continuous integration build see “How To: Set Up a Continuous Integration Build.” 

If you are new to TFS and Team Build, or if you want to learn more about the options available for automating and scheduling builds, read “Chapter 7 - Team Build Explained” before reading this chapter.

### Strategies for Continuous Integration Builds 
_Continuous integration_ (CI) is the process of creating builds whenever a developer checks code into source control. The following list identifies various strategies used for continuous integration builds:
* Build on each check-in.
* Rolling build after a specific number of check-ins.
* Rolling build after a specific time interval.
* Rolling build after a specific number of check-ins or time interval.

#### Build on Each Check-In
Building immediately after every check-in is the simplest continuous integration strategy and generally gives you the most rapid feedback. However, if check-ins occurs rapidly enough to overwhelm the build server, you should use a rolling build approach where you build after a specified number of check-ins or after a specified time period.  To decide if you need to use a rolling build, determine the following:
* Length of your team build in minutes.
* Average frequency of check-ins in minutes.
* Time window during which frequent check-ins occur.

If the length of the build is longer than the average frequency of check-ins, your builds start to queue up because first build does not complete before the next check-in occurs which initiates another build. If the build queue grows long enough, this can impact the performance of the build server and blocks other builds from being started, such as scheduled builds. Review the time window during which frequent check-ins occur and determine if the queue has time to clear itself after the busiest check-in period is over.

For more information, see “How To: Set Up a Continuous Integration Build in Visual Studio Team Foundation Server.”

#### Rolling Build After a Specific Number of Check-ins
If your build server is overloaded as a result of creating builds after each check-in, you can choose to only build after a specified number of check-ins have completed. While this is the simplest rolling build solution it has a significant drawback. Because the build server must see a specific number of check-ins before a build is started, the last check-in of the day is virtually guaranteed not to get a build and therefore build feedback is delayed.

#### Rolling Build After a Specific Time Interval
Producing a build only after a specific time interval elapses after each check-in is an improvement over building after a specific number of check-ins. This approach is guaranteed to produce a build within a specific timeframe around each check-in that is made. Keep in mind that each build may have a varying number of associated check-ins – some builds may only have one check-in, while others may have more. The more check-ins in each build, the more difficult it is to determine which check-in created the breaking change.

#### Rolling Build After a Specific Number of Check-Ins or Time Interval
Producing a build after a specific time interval or number of check-ins (whichever occurs first) results in the most consistency in your rolling builds while still reducing build server load. Use a rolling build if your continuous integration build creates a very long build queue and results in builds that occur a significant time after the check-in. Use a check-in interval to specify the number of check-ins between each build. Use the time-out period to ensure a build occurs even if there is no additional check-ins. 

#### Determining Your Rolling Build Interval
To determine the ideal rolling build interval, divide the average frequency of check-ins by the length of your build.  For example, if you have a build that takes 10 minutes and you average a check-in every 5 minutes you could set a check-in interval of two check-ins and a time-out period of 10 minutes. This helps ensure that the build is complete before the next build is initiated. If you notice excessive load on your build server, you can increase these values.  

### Continuous Integration Build in Team Foundation Server
Team Foundation Server 2005 does not provide a continuous integration solution out of box, but it does provide the framework for you to implement your own continuous integration build solution.

For more information about setting up a continuous integration build with TFS, see “How To: Setup a Continuous Integration Build in Visual Studio Team Foundation Server.” This How To article uses the solution provided by the Visual Studio Team System development team. The solution installs a Web service that runs under an account which has access to the TFS server. Team Foundation Server is able to send an e-mail message or call a Web service when specific events occur. This event mechanism is used by the continuous integration solution to register a Web service with the **CheckinEvent,** so that whenever a check in occurs, the Web service initiates a Team Build.

### Summary
Use continuous integration builds to kick off a build whenever a developer checks code into source control. Although Team Build does not provide a continuous integration solution out of the box, you can customize the build and implement your own continuous integration build solution. 

Depending on your specific project requirements, you can set continuous integration builds as follows:
* Continuous Integration build on each check-in. 
* Rolling build after a specific number of check-ins or specific time interval (whichever occurs earlier) in order to reduce build server load.

### Additional Resources
* For more information about how to use the Visual Studio Team System continuous integration solution, see “Continuous Integration Using Team Foundation Build” at [http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx](http://msdn2.microsoft.com/en-us/library/ms364045(VS.80).aspx)
* To download the Visual Studio Team System continuous integration solution MSI, go to [http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi](http://download.microsoft.com/download/6/5/e/65e300ce-22fc-4988-97de-0e81d3de2482/ci.msi)
* For more information about agile development and continuous integration in Team Foundation Server, see “Extend Team Foundation Server To Enable Continuous Integration” at  [http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx](http://msdn.microsoft.com/msdnmag/issues/06/03/TeamSystem/default.aspx)