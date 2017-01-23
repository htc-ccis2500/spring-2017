---
title: "GitHub Basics"
published: true
morea_id: read-github-basics
morea_summary: "An introduction to file & version management using git on GitHub."
morea_type: reading
morea_sort_order: 2
morea_labels:
 - intro
 - GitHub
 - git
---

## Introduction
Throughout this course, we will be using git and [GitHub](http://github.com/) to manage our projects. Git is an popular open source version control system, originally developed by Linus Torvalds (the creator of the Linux kernel). A large number of software projects, both open source and commercial, rely on Git for version control.

Version control provides many benefits to individuals and teams. In addition to providing a safe backup of the latest version of your files, it also maintains a history of changes so that you can see how the files looked in the past.  If you get something working, save it to your version control system, then later break it, you can return easily to the working version.  In a team project, version control helps avoid confusion that may occur when multiple people are editing the same files.  It provides a central spot for all team members to get and save files, and assists with merging changes from different people.

[GitHub](http://github.com/) allows us to have a centralized location to store and manage the git repositories.  While git can version files locally (on your computer), it is less risky to have copies of those versioned files in another location in case something happens to the files on your computer.  Since the repositories on GitHub are public, it is a great source for developers to show off their portfolio and to share your work with others.  

<div style="padding:20px">
<div class="row">
<div class="col-xs-12 col-md-8 col-md-push-2">
  <iframe src="https://player.vimeo.com/video/89542305" width="560" height="315" frameborder="0" allowfullscreen></iframe>
</div>
</div>
</div>

Understanding how to work with Git (the underlying version control system behind GitHub) and [GitHub](http://github.com/) itself are both very important first steps in this course, but learning to work with source code management tools more generally is a crucially important job skill.


## Get a GitHub Account
Get yourself setup with a GitHub account.  I recommend that you add your name to the account so that others can easily search for and find your account and repositories. If you use your student email, you can later request a free Personal account upgrade through the GitHub [Student Developer Pack](https://education.github.com/pack).  If you don't have access to your student mail right now, you can always come back and add an additional email later.

<div style="padding:20px">
<div class="row">
<div class="col-xs-12 col-md-8 col-md-push-2">
  {%  include youtube-small.html  id="ezxRcdJ8glM" %}
</div>
</div>
</div>

## Workflow
Most assignments will begin with a starter repository that you will *fork*.  This gives you a personal copy of the repository and its files.  This repository will usually contain the general layout for the project and any starter code that you should have to begin.  However this personal copy initially exists only on GitHub.  You'll need to *clone* the repository to your computer, so that you can make changes to the files.

Once you've made your changes and tested them, you need to stage your changes so that git knows the files are ready to be versioned.  It does not just version all of the files in your repository.  It will only track and version files you specifically add to the staged version.  When all your files are staged, then you do a *commit*.  This marks them with a version stamp inside your local repository.  It's a good habit to commit code locally often. I suggest that you make specific notes on what you've done in the commit messages.  This gives you a point to go back to if you need or want to undo something.  

When you're done with a chunk of work, or just need to save it *in the cloud* to go home for the night, you *push* your changes up to GitHub.  If you work on multiple computers, you might be wondering how to get those changes on that other computer.  To do this, you *fetch* or *pull* them.  When you are done with the assignment and are ready to submit it for grading, you create a *pull request*.  This is done on the GitHub website and allows me to give you in-code feedback as I  grade.  
