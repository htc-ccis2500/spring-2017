---
title: "Install Visual Studio Mobile Tools"
published: true
morea_id: ex-install-vs-tools
morea_type: experience
morea_summary: "How to customize your Visual Studio installation to include the mobile development tools."
morea_sort_order: 2
morea_labels:
 - install
 - Visual Studio
---

# {{ page.title }}
{{ page.morea_summary }}

### Customize the Install
Whether you have an existing install or are installing for the first time, the steps to add the mobile tools are similar:

- For a new install, you will want to customize the install when prompted.  
- For an existing install, go to Settings to modify the installation.

### Mobile Tool Options
Look for the option "Cross Platform Mobile Development" and check the box to install all of the mobile development tools.  

{% include img-small.html url="/morea/getting-started/images/vs-install-mobile-options.png"
    alt="Screenshot showing mobile options in VS Installer."
%}

The main tool we will use is the first option for C#/.Net (Xamarin) and the testing tools found under Common Tools and SDKs.  However as time and ability permits we may explore the other development options as well.

If you are limited on space, you may leave the middle two boxes unchecked:

 - HTML/JavaScript (Apache Cordova)
 - Visual C++ Mobile Development

They can always be added later if needed.
