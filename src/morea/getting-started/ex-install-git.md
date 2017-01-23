---
title: "Install Git"
published: true
morea_id: ex-install-git
morea_type: experience
morea_summary: "How to install git on Windows and configure it for use on a public or private computer."
morea_sort_order: 1
morea_labels:
 - install
 - git
---

# {{ page.title }}
{{ page.morea_summary }}

## Windows Users
There are two choices for installing git on Windows for this course.  You may download and install git through the Visual Studio installer, or you may install git directly from the web.  

{% include alert.html type="danger" content="Be sure to note the information on configuration at the bottom of this page." %}

### Visual Studio Install
If you have MS Visual Studio 2015 installed, go to Settings to modify the installation for Visual Studio.

At the bottom, expand "Common Tools" and check the box for Git for Windows.  
Optionally you may also check the box to install the GitHub extension for Visual Studio.

{% include img-small.html url="/morea/getting-started/images/vs-install-git-options.png"
    alt="Screenshot showing git options in VS Installer."
%}


### Stand-alone Install
You can get it from the [Git-SCM Downloads](https://git-scm.com/download/win).

I recommend that you keep the default install settings suggested by the installer, specifically:
<div class="row">
<div class="col-md-6">
<img class="img-responsive" src="{{ "/morea/getting-started/images/git-install-opt1.png" | prepend:site.baseurl }}" alt="Screenshot of install options">
</div><div class="col-md-6">
<img class="img-responsive" src="{{ "/morea/getting-started/images/git-install-opt2.png" | prepend:site.baseurl }}" alt="Screenshot of install options">
</div>
</div>

<br>
This will install a few different options that allow you to work with Git on a Windows computer.  You may choose any of them you like, but I would recommend GitBash as it will be closest to what you may see from my examples.


## Configure Git
Before you dive in, you'll want to configure git with your user information. In the commands below, fill in your GitHub name and the email used with your GitHub account.  The email address is what will tie your activity to your account.  **Make sure that you are using the same email and check for typos.**

### Config for Public (Shared) Computer
Use this only for a computer which is public or shared.  This configuration is applied __only to the current git repository directory__.  It must be repeated for each repository you clone or create.  
{% highlight bash %}
$ git config user.name "User Name"
$ git config user.email "user@email"
{% endhighlight %}

I also recommend saving this git config customized with your information as a Gist on GitHub so that it is easily available for you to use on any computer.

### Config for Personal (Home) Computer
Use this only for a computer where you are the only GitHub user.  This config is applied *globally* across all git repositories.
{% highlight bash %}
$ git config --global user.name "User Name"
$ git config --global user.email "user@email"
{% endhighlight %}
