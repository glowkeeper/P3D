# Lab - Week 1, Session 1 - Installing Unity and Integrating with GitHub

This lab's primary aim is to set up your environment so you can complete the rest of the Programming for 3D (P3D)module.

## GitHub and Version Control

You are required to use [GitHub](https://github.com/) for this module. GitHub is a great place to save and share your work. Besides, version control tools, like GitHub, are a crucial software industry tool, so getting to grips with how it works is a great skill to learn.

[GitHub](https://github.com/) is a cloud-based [version control](https://www.atlassian.com/git/tutorials/what-is-version-control) service with [git](https://git-scm.com/) at its core. Version control systems are how developers store, track changes and manage their code over time. They feature mechanisms such as [branching](https://www.atlassian.com/git/tutorials/using-branches) and [merging](https://www.atlassian.com/git/tutorials/using-branches/git-merge), giving developers even more control over the software they build. Branches are a snapshot of any changes made to a codebase, so when a developer wants to add a new feature or fix a bug, they create a new branch that captures the changes. Merging is the way version control systems reunite two branches.

![git branches](./images/gitBranchingandMerging.png)

If you have not used GitHub before, then there is a [Panopto recording](https://sussex.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=57307baa-f78e-42a8-8e5c-ac40012ddc4a) of a lecture about GitHub that the  [Module Convenor](https://github.com/glowkeeper/Programmingfor3D#maintainer) gave some time back. You can also access the [lecture slides](../githubPresentation.pdf).

_Figure 1: A visualisation of git branching and merging_

This module will not go into the intracacies of branching and merging but you are free to investigate and use such mechanisms, should you so wish.

## Exercise

This session requires you to set up a [GitHub](https://github.com/) account (if you do not have one already) and create a GitHub repository to store the rest of your work on this module. You will also install [Unity](https://unity3d.com/unity/qa/lts-releases) and make the Unity project that you will use for your work on this module. Finally, you will integrata that Unity project with GitHub.

### GitHub

If you still need a [GitHub](https://github.com/) account, create one. It may also be beneficial (although not for this module) to access the [GitHub Student Developer Pack](https://education.github.com/pack), as it gives you free access to lots of resources and tools.

Once you have a GitHub account, create a _private_ repository for your P3D work (you may wish to make it public later so that the repository forms part of your portfolio that you can show to potential employers). You should add the [Module Convenor](https://github.com/glowkeeper/Programmingfor3D#maintainer) as a collaborator to that repository (GitHub username _glowkeeper_) so they can support you throughout the module. Eventually, you'll publish your coursework there so that the Module Convenor can access it when they mark your work.

#### Clone the Repository

Before you _clone_ your GitHub repository locally, you will need to setup your GitHub username and credentials on your local machine.

GitHub has some really good online documentation for [Setting your username in Git](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git) and [Caching your GitHub credentials](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git) - for the latter, you have a couple of options - choose one!

Once you have your credentials set up, you should _clone_ your repository to your local hard drive. Below, you will create a Unity project in that repository and push your work back to GitHub.

### Unity

If you are new to Unity, you should apply for a [Unity Student Plan](https://unity.com/products/unity-student). Then, you should install the Unity Hub. Once you have that, use the Hub to install the latest version of [Unity with long-term support](https://unity3d.com/unity/qa/lts-releases); you will need [Visual Studio](https://visualstudio.microsoft.com/) for the scripting part of the course, so if you do not have that installed, you should add Visual Studio as a module when you install Unity.

#### Integrating a Unity Project with GitHub

Now, you will create a Unity project and save that project on GitHub.

To do so, open Unity Hub, create a new project and choose either the 3D Sample Scene (HDRP) or the 3D Sample Scene (UDRP), which are the High Definition Render Pipeline and the Universal Render Pipeline respectively. Store the project in a directory in your cloned repository - this could be any directory, but a good choice might be _src/yourProjectName_; you can name the project however you choose, but this project will form the basis of the rest of your work on this module, so choose the name wisely!

**Before you push your work back up to GitHub**, you should fetch [P3D's _.gitignore_](https://github.com/glowkeeper/P3D/blob/main/src/unity/.gitignore) and put it in _src/yourProjectName_ - this excludes the many files in the Unity project that will never change between machines, so they do not need to go under version control. You will know if you've done this correctly because you should only have hundreds of files to push up to GitHub (and not thousands); if that's the case (and only if that's the case), you can [add](https://github.com/git-guides/git-add), [commit](https://github.com/git-guides/git-commit) and [push](https://github.com/git-guides/git-push) the changes in your local repository up to GitHub.

Congratulations - you are now all set for the rest of the module!
