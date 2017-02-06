---
title: "Adding a project to GitHub"
published: true
morea_id: ex-vs-github-add
morea_type: experience
morea_summary: "Learn to work with Git and GitHub through Visual Studio by adding a new project to GitHub."
morea_sort_order: 3
morea_labels:
 - Visual Studio
 - git
 - GitHub
---

# {{ page.title }}
{{ page.morea_summary }}

## Install
If you have not already done so, the first steps are to install git and optionally the Visual Studio plugin.  

- [Install Git]({{ site.baseurl }}/morea/getting-started/ex-install-git.html )

This exercise will assume that you have installed the plugin.  If you do not wish to do that, you may still version your projects manually using the GitHub website and the installed gitcmd or gitbash shell from the git Windows install. You will need to use git commands to create your repository, link it to GitHub, then add, commit, and push files as needed.  

Additional Reference:

- [GitHub Extension for Visual Studio](https://visualstudio.github.com/index.html)
- Microsoft Visual Studio: [Learn about version control and Git](https://www.visualstudio.com/en-us/docs/git/tutorial/gitworkflow)


## Connect and Sign-out
In Visual Studio, go to the Team menu and select "Manage Connections".  

{% include img-small.html url="/morea/getting-started/images/vs-team-connections.png" alt="Visual Studio Team menu, Manage Connections option." %}

This will bring up the Team Explorer - Connect panel, generally on the right side of the screen. Notice the option for GitHub.

{% include img-small.html url="/morea/getting-started/images/vs-connect-github.png" alt="Team Explorer, GitHub option." %}

If you do not already have a GitHub account, you can click the link to sign-up.  Otherwise, click the link to connect and log-in.

{% include img-small.html url="/morea/getting-started/images/vs-gh-login-dialog.png" alt="GitHub login dialog box." %}

Once you are signed in, the GitHub view in the Team Explorer updates to allow you to log-out.  Make sure that you do this when working on public or shared computers such as those available on campus.

{% include img-small.html url="/morea/getting-started/images/vs-gh-signout-reminder.png" alt="GitHub sign out option." %}


## Add a new project to GitHub
Open up a project in Visual Studio that you would like to add to GitHub.  

{% include alert.html type="tip" content="Remember, that by default all GitHub projects are public.  You may make work private if you have a paid or upgraded student account, but it is not the default.  Work for this class should be public." %}  

First, we'll add our project to a local git repository, then connect it up to a remote repository created on GitHub.  There are two ways to do this.  

Option 1 - from the File menu, select the Add Solution to Source Control option.  
{% include img-small.html url="/morea/getting-started/images/vs-add-project.png" alt="File Menu, Add option." %}

Option 2 - in the Solution Explorer, right-click on your project and select Add Solution to Source Control
{% include img-small.html url="/morea/getting-started/images/vs-add-project-context.png" alt="Solution Explorer, Add option" %}

A new local git repository is created for you in your project directory.  Notice that it is shown in the Team Explorer.
{% include img-small.html url="/morea/getting-started/images/vs-local-repo.png" alt="Team Explorer repositories." %}

If you open Windows Explorer and look at your project directory, you'll notice a few things have now been added for you.  At least you'll notice these *if* you have Window set to show hidden files.  (If you do not see them, look up how to show hidden files for your version of Windows.)
{% include img-small.html url="/morea/getting-started/images/vs-git-hiddenfiles.png" alt="Hidden files created." %}

If you are not using the Visual Studio plugin, you'll want to manually create a .gitignore file to keep the junk out.  You can use [my gist](https://gist.github.com/mbMosman/0b98a0db0ecda4aa39e5a500b390ff6d) to fill in the contents of the file.  Note that it __MUST__ be named `.gitignore` to work.

{% include alert.html type="tip" content="When working with IDE's such as Visual Studio and source code management, it is a standard practice to ensure that only your source code and required project configuration is versioned - NOT - miscellaneous files created by the IDE.  Those are considered *junk* as there tend to be a lot of them, they are generally specific to a user and computer, and they can easily be recreated so they are a waste of space." %}

## Working Locally
Return to Visual Studio.  Notice that there is also now git information shown in the bottom right of the status bar at the bottom of Visual Studio.
{% include img-small.html url="/morea/getting-started/images/vs-git-statusbar.png" alt="Visual Studio status bar git info." %}

Reviewing the information in the status bar, you might notice that you now have an unpublished commit and several changes.  Let's see what those changes are and commit them.  If you click the pencil icon that indicates the number of changes, the Team Explorer Changes view shows.  Notice that it indicates we have added files.
{% include img-small.html url="/morea/getting-started/images/vs-changes.png" alt="Team Explorer Changes" %}

At the top of the display is an area for us to enter our commit comment.  Remember that these messages are used to help you understand what work is done in a particular commit, and so you should enter messages that describe the specific work that you completed.  Enter a message, then click Commit All.
{% include img-small.html url="/morea/getting-started/images/vs-changes-commit.png" alt="Team Explorer Changes showing commit message." %}

Notice that on a successful commit, an informational message is shown in the Team Explorer, the changes are cleared from the display and the status bar at the bottom shows no changes and an additional unpublished commit.

## Publishing Remotely
When working with git, it is important to remember that there is both a local and remote repository and that different versions of your files may exist in each.  Versions are initially kept locally on the computer you are currently working on.  To share work with others, or to be able to access that work on a different computer, you must explicitly *push* those to the remote repository.  Likewise, if updates are made remotely, you must also explicitly *pull* those changes down to your current computer.

Click the up arrow in the status bar at the bottom right of the screen.  This will open the Team Explorer Synchronization view. Click "Publish to GitHub".
{% include img-small.html url="/morea/getting-started/images/vs-sync.png" alt="Team Explorer Synchronization view." %}

Enter a repository name and optionally a description and click "Publish".
{% include img-small.html url="/morea/getting-started/images/vs-sync-publish.png" alt="Team Explorers, Create remote repository." %}

If this is successful, you should notice that there are now no unpublished commits and no changes in the status bar at the bottom.  You can also visit the GitHub website to see that your files have been published.

{% include img-small.html url="/morea/getting-started/images/vs-github-repository-web.png" alt="Files shown in the repository on the GitHub website." %}

If you are not using the plugin, you'd need to first create a repository on their website, then use the command line to add the connection to the remote repository and push the changes.  Fortunately GitHub offers helpful tips on the commands to use for this after you create the repository on their site.
