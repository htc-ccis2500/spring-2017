---
title: "Shell Basics"
published: true
morea_id: read-shell-basics
morea_summary: "An introduction to the shell on Windows and Mac."
morea_type: reading
morea_sort_order: 3
morea_labels:
 - intro
 - shell
 - git
---

# Shell Basics
When I include shell commands in the notes, the lines will begin with a $ (dollar sign). That indicates the prompt or the start of the shell command line. The *prompt* will look different based on what type of computer you are using, so we use the $ to indicate the prompt in a generic way.  _When entering commands do not type in the $; only type in the text that follows it._

Having the $ there to indicate the prompt is important as it allows us to differentiate commands that you would type in from the results of entering that command.  Any lines without the $ at the beginning of the line, will show you sample output from entering a command. Note that many commands do not give you output when successful.

For example, the `pwd` command tells you your current working directory. Basically, this tells you where you are located within your computer's file system tree.

<div style="padding:10px">
<div class="row">
<div class="col-xs-12 col-md-6">
  {% highlight bash %}
  $ pwd
  /Users/marymosman/Development/html/students
  {% endhighlight %}
</div>
</div>
</div>


When you try out this command, only type `pwd` into your shell window, do not type the $, then hit enter. It will output your current working directory on the next line, which will be different from the example shown.  It will then give you a prompt again.   

This is what it actually looks like on my computer.  I'm running on a Mac, so this is the Terminal.
<div style="padding:10px">
<div class="row">
<div class="col-xs-12 col-md-6">
   <img class="img-responsive" src="{{ "/morea/getting-started/images/terminal-pwd-cmd.png" | prepend:site.baseurl }}" alt="Terminal showing pwd command">
</div>
</div>
</div>

There are really only two other basic shell commands that you need to know to get through this course - `ls` and `cd`.

The `ls`, or list, command will list all of the files and directories inside the current working directory.

<div style="padding:10px">
<div class="row">
<div class="col-xs-12 col-md-6">
   {% highlight bash %}
   $ ls
   Gemfile        _data          _sass           javascripts
   README.md      _includes      assets          stylesheets
   _config.yml    _layouts       index.html
   {% endhighlight %}
</div>
<div class="col-xs-12 col-md-6">
  <img class="img-responsive" src="{{ "/morea//getting-started/images/terminal-ls-cmd.png" | prepend:site.baseurl }}" alt="Terminal showing ls command">
</div>
</div>
</div>


The `cd`, or change directory, command will change your working directory. When you enter the command, you type the directory to change to after the `cd`.  So if we want to go into the _data directory, we would enter:

<div style="padding:10px">
<div class="row">
<div class="col-xs-12 col-md-6">
  {% highlight bash %}
  $ cd _data
  {% endhighlight %}
</div>
<div class="col-xs-12 col-md-6">
  <img class="img-responsive" src="{{ "/morea//getting-started/images/terminal-cd-cmd.png" | prepend:site.baseurl }}" alt="Terminal showing cd command">
</div>
</div>
</div>

Notice there is no output this time.
The cd command will not give output unless there is an error.  Make sure to watch for those.  

To go up a directory you use two dots/periods.  

<div style="padding:10px">
<div class="row">
<div class="col-xs-12 col-md-6">
  {% highlight bash %}
  $ cd ..
  {% endhighlight %}
</div>
<div class="col-xs-12 col-md-6">
  <img class="img-responsive" src="{{ "/morea//getting-started/images/terminal-cd2-cmd.png" | prepend:site.baseurl }}" alt="Terminal showing cd .. command">
</div>
</div>
</div>

Again there is no output, but you can use the `pwd` command to see that the working directory has changed.



## Git Commands
The GitHub Student Directory assignment walks you through the GitHub process that you'll use for your assignments.  But to give you a summary of all the commands you'll use in the shell on one page, I'll quickly introduce the key git commands here.


### Clone
The `git clone` command will create a local copy of your repository from GitHub. The GitHub repository, what you see when looking at the website, lives on their servers "in the cloud".  That is a remote repository.  To work on your files, you need a local repository; one that is on your computer.

{% highlight bash %}
$ git clone <clone-url>
{% endhighlight %}


### Status
The `git status` command will give you the current status of your local repository. It will show you if you have changes that are untracked (not added), added and ready for commit, and how different your local repository is from the remote repository that you cloned from.

For example:
{% highlight bash %}
$ git status
On branch gh-pages
Your branch is up-to-date with 'origin/gh-pages'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   _data/summer_2016/mbmosman.yml

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	_data/summer_2016/mbmosman2.yml

no changes added to commit (use "git add" and/or "git commit -a")
{% endhighlight %}


### Add
The `git add` command will stage, or mark, your local changes for commit. Changes that have been added are tracked, and changes that have not been added yet are untracked and will not be included in any commits that you make.

To add all changes, you can use this shortcut:
{% highlight bash %}
$ git add .
{% endhighlight %}

To add individual changes, you can use add plus the file name or directory to add:
{% highlight bash %}
$ git add <file-or-directory-name>
{% endhighlight %}


### Commit
The commit command will save and version your changes to your local repository. This saves the time of the commit, all of the changes to the staged (added) files, as well as the message that you enter.  These changes are then available to push to the remote repository.

{% highlight bash %}
$ git commit -m "added new file"
On branch gh-pages
Your branch is ahead of 'origin/gh-pages' by 1 commit.
  (use "git push" to publish your local commits)
 1 file changed, 3 insertions(+)
 create mode 100644 _data/summer_2016/mbmosman2.yml
{% endhighlight %}

Notice that the output will tell you which branch you are on (for this class that will usually be gh-pages), how many commits your local repository is ahead of the remote, and how many files were changed as part of this commit.


### Push
The `git push` command sends your local changes to the remote repository.  

If your local and remote branches match, you can just use the short form of the command:
{% highlight bash %}
$ git push
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 502 bytes | 0 bytes/s, done.
Total 5 (delta 3), reused 0 (delta 0)
To https://github.com/mbMosman/students.git
   182b32c..2823398  gh-pages -> gh-pages
{% endhighlight %}

Notice the output include a status to show it is 100% done and where it pushed the changes to.

If your local and remote branches are different, you can choose which remote branch to push to:
{% highlight bash %}
$ git push origin <remote-branch-name>
{% endhighlight %}


## Other Resources
While this is enough to get by for this course, shell commands are important tools for IT Professionals. This article from LifeHacker offers a quick overview of why you should learn the command lilne, and how to do it:  [Master the Command Line This Weekend](http://lifehacker.com/5990668/master-the-command-line-this-weekend).

Codecademy also has an online course to [Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line).  Unit 1 and Unit 2 provide sufficient knowledge for this course, and the last time I checked you were able to work through those with a free account.  There are also additional units that will teach several other common commands.  
