### Chapter 3 - Structuring Projects and Solutions in Source Control
- _[J.D. Meier](http://blogs.msdn.com/jmeier), [Jason Taylor](http://jtaylorgoodlife.blogspot.com/), Alex Mackman, [Prashant Bansode](http://prashantbansode.blogspot.com/), [Kevin Jones](http://blogs.advantaje.com/blog/kevin/)_

### Objectives
* Structure your Microsoft® Visual Studio® Team System solutions and projects appropriately.
* Know when to use multiple solutions and when to use a single solution.
* Identify appropriate structures for small, medium-size and very large teams.

### Overview
This chapter explains various options for structuring Visual Studio solution and project files in a manner appropriate for team development. Visual Studio uses solution (.sln) files to group together related Visual Studio project (.csproj and .vbproj) files. Deciding how to structure your projects and solutions is an important decision because the pattern you choose has a number of consequences. For example, it impacts how easily members of your development teams can push and pull solutions and projects to and from source control, the mechanism you use to reference dependencies, and also your build processes.

If you are working on a small project you can use a single solution to contain all of your project files. If you are working on a software development project with a large number of project files, you should use multiple solution files to group related projects that correspond to subsets of functionality within your overall team project. Depending on your specific scenario you may also need a single solution file to group together all of your project files.

### How to Use This Chapter
Use this chapter to select an approach for structuring your Visual Studio solutions and projects. To gain the greatest benefits from this chapter, you should:
* **Use the strategies list**.**** Use the initial list of strategies: single solution, partitioned solution, and multiple solutions to quickly evaluate the best approach for your scenario.
* **Read the scenario section that is most relevant to your needs**.**** Read the section describing how to implement the option you have chosen.
* **Read Chapter 4, “Structuring Projects and Solutions in Team Foundation Server Source Control” next**. Chapter 4 introduces you to important considerations to keep in mind when storing your code in Team Foundation Server (TFS) source control. 
* **Read Chapter 6, “Managing Source Control Dependencies in Visual Studio Team System”.** Project structure impacts the strategies available to you when managing dependencies across projects and solutions. For more information about how to manage dependencies, read Chapter 6. 
* **Read the companion How To articles.** Read the following companion How To articles for a step-by-step walkthroughs of various procedures discussed in this chapter. 
	* How To: Structure ASP.NET Applications in Visual Studio Team Foundation Server.
	* How To: Structure Windows Applications in Visual Studio Team Foundation Server.
	* How To: Structure Your Source Control Folders in Visual Studio Team Foundation Server.

### Strategies for Solution and Project Structure
The three most common strategies used to structure solution and project files are:

* **Single solution**. If you work on a small system, create a single solution and place all of your projects within it.  
* **Partitioned solution**. If you work on a large system, use multiple solutions to group related projects together. Create solutions to logically group subsets of projects that a developer would be most likely to modify as a set, and then create one master solution to contain all of your projects. This approach reduces the amount of data that needs to be pulled from source control when you only need to work on specific projects.
* **Multiple solutions**. If you are working on a very large system that requires dozens of projects or more, use multiple solutions to work on sub-systems but for dependency mapping and performance reasons do not create a master solution that contains all projects.

In general you should:
* Use a single solution strategy unless the resulting solution is too large to load into Visual Studio. 
* Use multiple solutions to create specific views on sub-systems of your application.
* Use multiple solutions to reduce the time it takes to load a solution and to reduce build time for developers.

Keep the following considerations in mind when designing a project and solution structure:
* Each project generates an assembly at build time. Start by determining what assemblies you want to create and then use this to decide what projects you need. Use this to determine how to factor your codebase into projects.
* Start with the simplest single solution structure. Only add complexity to your structure when it is really necessary.
* When designing a multi-solution structure:
	* Consider project dependencies. Try to group those projects that have dependencies on one another as part of the same solution. This enables you to use project references within your solution. By using project references instead of file references, you enable Visual Studio to keep build configurations (debug/release) synchronized, and to track versioning to determine when projects need to be rebuilt. Try to minimize the number of cross-solution project references.
	* Consider source sharing. Place projects that share the same source in the same solution.
	* Consider team structure. Structure your solutions to make it easy for teams to work on a set of related projects together.
* Keep a flat project structure so that it is easy for you to group projects into solutions without needing to make file system or source control folder structure changes.

### Single Solution
If you work on a small system, consider using a single Visual Studio solution to contain all of your projects.  This structure simplifies development because all of the code is available when you open the solution. This strategy also makes it easy to set up references, because all references are between projects in your solution. You might still need to use file references to reference third-party assemblies, such as purchased components, that are outside your solution. Figure 3.1 shows the single solution approach.

![](Chapter 3 - Structuring Projects and Solutions in Source Control_Fig3.1.gif) 
**_Figure 3.1** Single Solution Approach_

The main reasons to choose this structure include:
* You can keep build scripts simple.
* You can easily map dependencies across projects within the solution.

You should use this structure if all developers use the same solution and have the same set of projects. This could be a problem for large systems where you want to organize projects by sub-system or feature.

### Partitioned Solution
If you work on a large system, consider using multiple solutions, each representing a sub-system in your application. These solutions can be used by developers in order to work on smaller parts of the system without having to load all code across all projects. Design your solution structure so any projects that have dependencies are grouped together. This enables you to use project references rather than file references. Also consider creating a master solution file that contains all of the projects. You can use this to build your entire application.

**Note:** Unlike previous versions of Visual Studio, Visual Studio 2005 relies upon MSBuild. It is now possible to create solution structures that do not include all referenced projects and still build without errors. As long as the master solution has been built first, generating the binary output from each project, MSBuild is able to follow project references outside the bounds of your solution and build successfully. This only works if you use project references, not file references. You can successfully build solutions created this way from the Visual Studio build command line and from the IDE, but not with Team Build by default. In order to build successfully with Team Build use the master solution that includes all of the projects and dependencies.

Figure 3.2 shows the partitioned solution approach.

![](Chapter 3 - Structuring Projects and Solutions in Source Control_Fig3.2.Gif) 

**_Figure 3.2** Partitioned Solution Approach_

When working with multiple solutions, use a flat file structure for all of your projects. A typical example is an application that has a Microsoft Windows® Forms project, an ASP.NET project, a Windows service, and a set of class library projects shared by some or all of those projects.
 
You can use the following flat structure for all projects:
# /Source
# /WinFormsProject
# /WebProject
# /WindowsServiceProject
# /ClassLibrary1
# /ClassLibrary2
# /ClassLibrary3
# Web.sln
# Service.sln
# All.sln

Keeping the structure flat provides a lot of flexibility and the ability to use solutions for presenting different views on the projects. The physical folder structure around solution files is very hard to change, especially if you realize that you need to reuse a class library from another solution.

Reasons to use this structure include:
* Performance is improved when loading and building application sub-solutions.
* Sub-solutions can be used to create views on sets of projects based on development sub-teams or boundaries of code sharing.
* You can use the master solution to build the entire application.
* You can easily map dependencies across projects in each sub-solution. 
* It reduces overall complexity if the solutions are broken up logically. For example breaking up the solution along technology or feature lines makes it easier for new developers to understand which solution to work on.

The main reason not to use this structure is:
* Increased solution maintenance costs. Adding a new project might require multiple solution file changes.

### Multiple Solutions
If you work on a very large solution requiring many dozens of projects, you may encounter solution scalability limits. In this scenario, break your application into multiple solutions but do not create a master solution for the entire application because all references inside each solution are project references. References to projects outside of each solution (for example to third-party libraries or projects in another sub-solution) are file references. This means that there can be no “master” solution. 

Instead, you must use a script that understands the order in which the solutions need to be built. One of the maintenance tasks associated with a multiple-solution structure is ensuring that developers do not inadvertently create circular references between solutions. This structure requires complex build scripts and explicit mapping of dependency relationships. In this structure it is not possible to build the application in its entirety within Visual Studio. Instead, you can use TFS Team Build or MSBuild directly. 

Figure 3.3 shows the multiple solutions approach.

![](Chapter 3 - Structuring Projects and Solutions in Source Control_Fig3.3.Gif) 

**_Figure 3.3** Multiple Solution Approach_

You should use this structure to work around Visual Studio IDE performance and scalability limits for very large applications.

One reason not to use this structure is that it requires a complex build script to handle dependencies across the sub-solutions by building solutions in the right order.

### Large Project Considerations
Large development teams are likely to distinguish themselves from smaller teams in the following ways:

* They require a more complex branching and merging structure.
* They are more likely to manage dependencies across solutions and team projects.
* They are more likely to maintain multiple builds for components and teams.

A partitioned solution approach works well for most large projects because it provides solution flexibility while maintaining a single solution that you can use to build the application. If your application is large enough that you hit solution scalability limits, use the multiple solutions approach.

### Summary
Use a single solution for small projects in which it is not necessary to partition your source into separate sub-solutions.

Use a partitioned solution for logically grouping subsets of projects that a developer would be most likely to modify as a set, and then create one master solution that contains all of your projects. 

Use multiple solutions to create specific views on subsystems and to reduce the load and build time of your application. 

A partitioned solution works well for most large projects because it provides solution flexibility while maintaining a single solution that can be used to build the application.

### Additional Resources
* For more information about project and solution structure (though not directly applied to Team Foundation Server), see “Team Development with Visual Studio .NET and Visual SourceSafe” at [http://msdn2.microsoft.com/en-us/library/ms998208.aspx](http://msdn2.microsoft.com/en-us/library/ms998208.aspx)