---
title: "Git and Branches"
published: true
morea_id: ex-vs-github-branches
morea_type: experience
morea_summary: "Learn to work with Git and branches using Visual Studio."
morea_sort_order: 4
morea_labels:
 - Visual Studio
 - git
 - GitHub
---

# {{ page.title }}
{{ page.morea_summary }}

## Prerequisites
If you have not already done so, the first steps are to install git and add a project to source control.  

- [Install Git]({{ site.baseurl }}/morea/getting-started/ex-install-git.html )
- [Adding a Project to GitHub]({{ site.baseurl }}/morea/xamarin-basics/ex-vs-github-add)

This exercise will assume that you have installed the Visual Studio plugin for GitHub.  If you do not wish to do that, you will need to use git commands to create and manage your branches and version your work.  

Additional Reference:

- [GitHub Extension for Visual Studio](https://visualstudio.github.com/index.html)
- Microsoft Visual Studio: [Learn about version control and Git](https://www.visualstudio.com/en-us/docs/git/tutorial/gitworkflow)


## Intro to Branches
One of the main benefits of using a version control tool like git is that it allows you to keep a history of changes to your project.  That allows you some measure of safety, so that if you need to go back to see what your project looked like in the past, you can easily do that. This also allow you to access the code from that point in time as well, which is helpful if you need to say fix a bug in an older release.  

Another benefit is that you can share your code to allow multiple people to work on things at the same time. This is particularly helpful on large projects where one person cannot handle on the work on the time schedule needed.  It can also allow one person to begin work on the next release while another is maintaining the old and fixing bugs.

With only one active line of changes though, this could become confusing and difficult to manage very quickly.  To facilitate this type of work, it's important to be able to maintain many active lines of work within a single project. This keeps one developers work isolated from the work of others until the changes are complete, tested and ready to be shared. This also allows us to fix bugs for the released code without contaminating it with any new, unreleased features. These lines of work are called __branches__, and learning to work with them is important to understand how git is used on the job.

### Master
The master branch is the default main branch in a git repository.  Generally this branch is reserved for the released version of a project - code that has been integrated, well tested and is publicly consumed.  Developers do not commit changes to this on a day to day basis, as we are known to break things.  Changes to this branch often involve a good deal of coordination and specialized testing first.

You'll notice that when we initially added our project to GitHub in the last exercise, that it was added to the master branch.  The branch is shown in the status bar at the bottom-right of Visual Studio.

For the purposes of this course, the code on your master branch will be the work that has been reviewed (graded) and had any necessary changes or corrections made to it.  

### Dev/Feature Branches
It is common to need to isolate maintenance work or new feature development from both the released code on the master branch and the work being done for other reasons.  Sometimes this is work that you are doing yourself and need to keep separate, but other times it will be work that is done by others.  It isn't important *who* is doing the work, only that the work should be kept separate.

Even on a new development project that does not *have* released code, work is never started on the main branch as you never know what code it might be that is initially released.  Perhaps that high-priority feature, becomes a low priority the next week and it needs to be shelved for a time.  By having that work on a dev/feature branch, that becomes a trivial task.

For the purposes of this course, you should create a new branch for each individual assignment's work so that we isolate our new and unstable code from our completed, tested, and already-graded code. When first starting a new project, it is important to create a branch first as it facilitates the pull-request process that will be used for grading feedback.  


## Create a Dev/Feature Branch
Open up the project you added to GitHub in the previous exercise in Visual Studio.  

The current branch is shown at the bottom-right in the status bar.  This should currently say "master".  Click on this to bring up the pop-up menu and select "New Branch..." option.  This opens the Branches view in Team Explorer.  

Enter the branch name, something to indicate the assignment name perhaps, and select master as the starting point.  Make sure that the box is checked to "Checkout branch" and then click "Create Branch".
{% include img-small.html url="/morea/getting-started/images/vs-new-branch.png" alt="Visual Studio Team Explorer, creating a new branch." %}

You should see that you now have two branches shown in the Branches view and that the name of the branch shown in the status bar has changed from master to your new branch.
{% include img-small.html url="/morea/getting-started/images/vs-branches.png" alt="Team Explorer, branches view with new branch." %}

You're now ready to make changes to your project code and add, commit and push those changes on your development branch.

## Working with the branch
To illustrate the process of making changes, let's add a Readme file to your project repository.

In Visual Studio, Add a new text file using the File menu.  Then use File, Save As to save that file as "Readme.md" in your solution directory.  Make sure the file is saved with a .md extension. This is a [Markdown](https://daringfireball.net/projects/markdown/syntax) file.
{% include img-small.html url="/morea/getting-started/images/vs-save-readme.png" alt="Saving the readme.md file to the solution directory." %}

{% include alert.html type="note" content="It is important that you are creating solution directories for the projects you create for this course." %}

Add some text to the file. This file is shown on GitHub to those browsing through your repositories.  It's helpful to include the name of your project and a short description. A heading begins with `# ` but basic text can just be typed in.  
{% include img-small.html url="/morea/getting-started/images/vs-edit-readme.png" alt="Sample readme file text." %}

Make sure you have saved the file, then notice that you have a change showing in the git status information in the status bar in the bottom-right of Visual Studio.  Make sure the correct branch is showing - your new development branch NOT master.  Then, click the pencil icon to stage and commit that change.  

{% include alert.html type="danger" content="It is important to verify your branch before committing the change. While it is not impossible to move changes put on the wrong branch, this would be a bad faux pax on the job." %}

{% include img-small.html url="/morea/getting-started/images/vs-commit-readme.png" alt="Team Explorer - Changes view showing add of readme file." %}  

Next we want to push that work out to our remote GitHub repository.  Notice there is an unpublished commit showing in the status bar.  Click the up-arrow icon to bring up the Team Explorer Synchronization view.

When the branch is new, you'll notice a message that indicates there is no remote branch being tracked.  That's fine, because we're about to create it.  Click "Publish".
{% include img-small.html url="/morea/getting-started/images/vs-publish-devbranch.png" alt="Team Explorer - Publish the development branch." %}

Now let's take a look at the GitHub website and see what happened.  Notice that the master branch is unchanged, but a new branch was recently updated.
{% include img-medium.html url="/morea/getting-started/images/vs-github-updated-web.png" alt="GitHub website showing new branch recently pushed." %}

Notice that there is a Branch dropdown just above where it shows your file list.  This tells you what branch is being displayed.  Click the dropdown and select your new development branch.
{% include img-medium.html url="/morea/getting-started/images/vs-github-updated-branch-web.png" alt="GitHub website showing changes on new develpment branch." %}

## Pull-request
When your work on a branch is ready to be combined with other work (or in the case of this class is ready for grading), you'll create a pull-request.  This shows the changes between the branches and allows for review and feedback on the work before the changes are merged to another branch.

Let's create a pull-request to add the readme.md file to the master branch.  While looking at the files on the new development branch on the GitHub website, click the New Pull-request button.
{% include img-medium.html url="/morea/getting-started/images/vs-github-new-pullrequest-web.png" alt="GitHub website showing new pull-request button." %}

The next page will show a dialog at the top that titles the pull-request (by default it uses your last commit comment) and below will show all the files/changes that will be part of this request.  It is important that you scroll-down and review the files/changes to make sure you are creating the pull-request correctly.  You should see the files that you recently worked on.  Also notice at the top that base should say "master" and compare should show your dev/feature branch name.
{% include img-medium.html url="/morea/getting-started/images/vs-github-open-pullrequest-web.png" alt="GitHub website review before opening pull-request." %}

Once you have confirmed that the base is your master branch and you have reviewed the changes to be included below, click the green "Create pull request" button.  You'll now see that the pull-request is open.  
{% include img-medium.html url="/morea/getting-started/images/vs-github-opened-pullrequest-web.png" alt="GitHub website review showing open pull-request." %}

A screenshot of the open pull request, as shown above MUST be placed in the assignment dropbox for grading.  This tells me several important things that I would not otherwise know:

1. Your GitHub user name.
2. What repository your work is in.
3. What branch and pull-request I should be looking at for this assignment.

{% include alert.html type="danger" content="No screenshot will mean no grade for the work." %}

## Review Feedback
Once I have reviewed your work, you'll probably see comments in your email.  Depending on the comments, those are generally easier to review and understand if you are looking at the pull-request on GitHub.  If you switch to the Files Changed tab view, you can see a listing of all the files included, the contents of those files, and any comments made in the context of the file and code that the comment pertains to.
{% include img-medium.html url="/morea/getting-started/images/vs-github-pullrequest-feedback-web.png" alt="GitHub website review showing open pull-request feedback." %}

Once you have gotten my feedback on your work, you may want to make updates to your code to make any fixes or  suggestions indicated in that feedback.  You should make those changes and push them to GitHub before going on to merge the code as shown below.  In an on the job situation, those changes would likely require another review before merging, but we'll skip that for this class.

## Merge Changes
The last step is to move your changes from your development branch to the master branch.  Remember that this is done after the work is graded.

Go back to your pull-request on the GitHub website.  There should be a lovely green-button to "Merge pull request".  For *other* assignments, __DO NOT DO THIS UNTIL THE WORK HAS BEEN GRADED.__  (It's ok to do it now while doing this assignment.)
{% include img-medium.html url="/morea/getting-started/images/vs-github-merge-pullrequest-web.png" alt="GitHub website showing merge pull-request button." %}

{% include alert.html type="note" content="If you do not see this green button, you've got changes mixed on both branches and will need to do a manual merge.  I recommend that you contact me for help with this unless you have done it before or feel *very* confident in your git skills. This should not happen if you are careful about where you commit your changes." %}

You'll notice all that green becomes purple and the pull-request is not merged.  
{% include img-medium.html url="/morea/getting-started/images/vs-github-merged-pullrequest-web.png" alt="GitHub website showing merged pull-request." %}

Click the Code tab view to see the list of all your repository files on the selected branch and you'll now see that the master branch includes the Readme.md file.  The comment should also show that the last commit was from the merge of your pull-request.
{% include img-medium.html url="/morea/getting-started/images/vs-github-after-merge.png" alt="GitHub website showing code after merge." %}

__Take a screenshot of that page on GitHub to put in the assignment box to show you have completed this work.__ Note that this screenshot should show your repository not mine.

In a situation where the changes would really be merged to the release branch, you would most likely not be doing this merge automatically through GitHub.  The changes would first be merged into a staging branch where they could be thoroughly QA tested and validated before becoming the official released code.  

## Pulling Remote Changes
One last thing you should know about working with git.  We've now made updates to our master branch outside of Visual Studio.  This was done when we merged the changes from the dev/feature branch to master on the website.  However, you might also get into this situation with other branches if you are pushing work to GitHub from more than one computer.

To get remote changes back into our local repository, we need to pull them in.  

In Visual Studio, go to the Team Explorer and open the Synchronization view.  Check that the dev/feature branch is still active as shown in the status bar at the bottom of Visual Studio, and switch if needed.  In the Sync view you'll notice a section that says incomming commits.  __Click Fetch__  and you'll notice there are still "no incomming commits."
{% include img-small.html url="/morea/getting-started/images/vs-sync-in-devbranch.png" alt="Visual Studio Team Explorer Sync view incoming commits on dev/feature branch." %}

However if you switch the branch to master in the status bar, that will change.  Now you should see that there are incomming commits from your merge.  __Click Pull__  to integrate those changes into your local repository.
{% include img-small.html url="/morea/getting-started/images/vs-sync-in-master.png" alt="Visual Studio Team Explorer Sync view incoming commits on master branch." %}
