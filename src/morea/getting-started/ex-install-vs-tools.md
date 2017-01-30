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

## Requirements
The mobile tools are new with Visual Studio 2015, but are a part of all editions, including the free Community Edition.

The mobile development tools include emulators for Windows and Android that require either:
  - Windows 8.1 (x64) Professional edition or higher
  - Windows 10 Education, Pro or Enterprise (x64) edition (__NOT__ Home edition)
In addition, you need a processor that supports Client Hyper-V and Second Level Address Translation (SLAT).

{% include alert.html type="tip"
    content="As a student, you can get the Education Edition of Windows 10 free through your student Imagine account."
%}

You'll also need a good chunk of disk space.  Depending on options installed, Visual Studio can require 30GB or more of disk space.

## Customize the Install
Whether you have an existing install or are installing for the first time, the steps to add the mobile tools are similar:

- For a new install, you will want to customize the install when prompted.  
- For an existing install, go to Settings to modify the installation.

## Mobile Tool Options
Look for the option "Cross Platform Mobile Development" and check the box to install all of the mobile development tools.  

{% include img-small.html url="/morea/getting-started/images/vs-install-mobile-options.png"
    alt="Screenshot showing mobile options in VS Installer."
%}

The main tool we will use is the first option for C#/.Net (Xamarin) and the testing tools found under Common Tools and SDKs.  However as time and ability permits we may explore the other development options as well.

If you are limited on space, you may leave the middle two boxes unchecked:

 - HTML/JavaScript (Apache Cordova)
 - Visual C++ Mobile Development

They can always be added later if needed.

## Emulators

### Android
If you have trouble with the packaged Android emulators, there is an additional installer for a Microsoft Android emulator you can get separately.  The [Visual Studio Emulator for Android](https://www.visualstudio.com/vs/msft-android-emulator/) is said to boot and run faster, is tailored for Visual Studio, and allows saving of various device profiles.

### Windows Phone
The Windows Phone emulators require an additional install and there are both Windows 8 and Windows 10 universal emulators.  Both of these may be selected from the Visual Studio install customization screen.  
