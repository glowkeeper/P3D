# Week 1, Session 1 - Installing Unity and Integrating with GitHub

This session aims to set up your environment so you can complete the rest of the Programming for 3D (P3D) module.

## GitHub and Version Control

You are required to use [GitHub](https://github.com/) for this module. GitHub is a great place to save and share your work. Besides, version control tools, like GitHub, are a crucial software industry tool, so getting to grips with how it works is a great skill to learn.

[GitHub](https://github.com/) is a cloud-based [version control](https://www.atlassian.com/git/tutorials/what-is-version-control) service with [git](https://git-scm.com/) at its core. Version control systems are how developers store, track changes and manage their code over time. They feature mechanisms such as [branching](https://www.atlassian.com/git/tutorials/using-branches) and [merging](https://www.atlassian.com/git/tutorials/using-branches/git-merge), giving developers even more control over the software they build. Branches are a snapshot of any changes made to a codebase, so when a developer wants to add a new feature or fix a bug, they create a new branch that captures the changes. Merging is the way version control systems reunite two branches.

![git branches](./images/gitBranchingandMerging.png)

If you have not used GitHub before, then there is a [Panopto recording](https://sussex.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=57307baa-f78e-42a8-8e5c-ac40012ddc4a) of a lecture about GitHub that the  [Module Convenor](https://github.com/glowkeeper/Programmingfor3D#maintainer) gave some time back. You can also access the [lecture slides](../githubPresentation.pdf).

_Figure 1: A visualisation of git branching and merging_

This module will not explore the intricacies of branching and merging, but you can investigate and use such mechanisms.

## Unity Game Engine

The [Unity](https://unity.com/) game engine and editor framework gives you a system for designing and building interactive 2D and 3D applications and games. Unity allows you to create such environments using code and/or visual components you make in the editor, and you can export them to every major platform, including mobile and VR.

During Programming for 3D, you will create a game.

## Exercise

This session requires you to set up a [GitHub](https://github.com/) account (if you do not have one already) and create a GitHub repository to store the rest of your work on this module. You will also install [Unity](https://unity3d.com/unity/qa/lts-releases) and make the Unity project that you will use for your work on this module. Finally, you will integrate that Unity project with GitHub.

### GitHub

If you still need a [GitHub](https://github.com/) account, create one. It may also be beneficial (although not for this module) to access the [GitHub Student Developer Pack](https://education.github.com/pack), as it gives you free access to lots of resources and tools.

Once you have a GitHub account, create a _private_ repository for your P3D work (you may wish to make it public later so that the repository forms part of your portfolio that you can show to potential employers). When creating the repository, you should tick the checkbox that adds a _README_ file (this initialises the repository, so you don't need to do that yourself later) and add a Unity-specific _.gitignore_ - this is very important! The _.gitignore_ file excludes the many files in the Unity project that will never change between machines, so they do not need to go under version control.

You should add the [Module Convenor](https://github.com/glowkeeper/Programmingfor3D#maintainer) as a collaborator to that repository (GitHub username _glowkeeper_) so they can support you throughout the module. Eventually, you'll publish your coursework there so the Module Convenor can access it when they mark your work.

### Install the GitHub Pull Requests and Issues extension in VS Code

To get started with the GitHub in VS Code, you'll need to [install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git), create a GitHub account (see above), and install the [GitHub Pull Requests and Issues extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github). Once all that's done, you can sign into GitHub using the _Accounts_ button in the bottom-left corner of the VS Code Window.

#### Clone the Repository

Before you _clone_ your GitHub repository locally, you must set up your GitHub username and credentials on your local machine.

GitHub has some excellent online documentation for [Setting your username in Git](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git) and [Caching your GitHub credentials](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git) - for the latter, you have a couple of options - choose one!

Once your credentials are set up, you should _clone_ your repository to your local hard drive. Below, you will create a Unity project in that repository and push your work back to GitHub.

### Unity

If you are new to [Unity](https://unity.com/), you should apply for a [Unity Student Plan](https://unity.com/products/unity-student). Then, you should install the Unity Hub. Once you have that, use the Hub to install the latest version of [Unity with long-term support](https://unity3d.com/unity/qa/lts-releases); you will need [Visual Studio](https://visualstudio.microsoft.com/) for the scripting part of the course, so if you do not have that installed, you should add Visual Studio as a module when you install Unity.

#### Integrating a Unity Project with GitHub

Now, you will create a Unity project and save it on GitHub.

To do so, open Unity Hub, create a new project, and choose the 3D Sample Scene (HDRP) or the 3D Sample Scene (UDRP), which are the High Definition Render Pipeline and the Universal Render Pipeline, respectively. Store the project in a directory in your cloned repository - this could be any directory, but a good choice might be _src/yourProjectName_; you can name the project however you choose, but this project will form the basis of the rest of your work on this module, so choose the name wisely!

**Before you push your work back up to GitHub**, you should move the _.gitignore_ file you added to the repository when it was created to _src/yourProjectName_. You will know if you've done this correctly because you should only have hundreds of files to push up to GitHub (and not thousands); if that's the case (**and only if that's the case**), you can [add](https://github.com/git-guides/git-add), [commit](https://github.com/git-guides/git-commit) and [push](https://github.com/git-guides/git-push) the changes in your local repository up to GitHub. Only do this if you do not have many thousands of files to push up to GitHub (because undoing that push is problematic).

Congratulations - you are now all set for the rest of the module!

## Lab Video

[Integrating Unity with GitHub](https://youtu.be/sDMHpWAa4Os)

## Links

- [git](https://git-scm.com/)
- [What is GitHub?](https://kinsta.com/knowledgebase/what-is-github/)
- [What is Version Control?](https://www.atlassian.com/git/tutorials/what-is-version-control)
- [git add](https://github.com/git-guides/git-add)
- [git commit](https://github.com/git-guides/git-commit)
- [git push](https://github.com/git-guides/git-push)
- [Unity](https://unity.com/)
- [Old but still worth a read - Developing Your First Game with Unity](https://learn.microsoft.com/en-us/archive/msdn-magazine/2014/august/unity-developing-your-first-game-with-unity-and-csharp)