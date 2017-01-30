---
title: "Application Structure"
published: true
morea_id: read-xamarin-basics
morea_summary: "An introduction to the structure of a Xamarin.Forms cross-platform mobile application."
morea_type: reading
morea_sort_order: 1
morea_labels:
 - Visual Studio
 - Xamarin.Forms
---

## {{ page.title }}
{{ page.morea_summary }}

## Reference Text
Chapters 1-3 of [Creating Mobile Apps with Xamarin.Forms](https://developer.xamarin.com/guides/xamarin-forms/creating-mobile-apps-xamarin-forms/) by Charles Petzold.  

## The User Interface
Let's take a deeper look at the shared code inside a basic Xamarin.Forms portable application project, beginning with the user interface.  We have 3 main categories of objects on the screen:  pages, layouts, and views. If you've worked with user interface code in the past these should sound familiar.

The Xamarin.Forms applications are organized into pages.  As you might expect, a page generally fills the device screen.  We might have a single page application, or we might have one with many pages that flow from one to another.  The sample application that we looked at earlier is a single page application built using a [`ContentPage`](https://developer.xamarin.com/api/type/Xamarin.Forms.ContentPage/).  

The `App.cs` class sets the `MainPage` of the application.  Instead of putting all of the page layout code into the `App.cs` file, it is typical to create a custom page class that extends `ContentPage` in a new file. The standard convention is to name the class using the name of your application + Page.  For example, for an app called "MyApp" the main page class would be called `MyAppPage`.  

After creating a custom page class, we must update the `App` code to create an instance of that class as the `MainPage`.  

{% include alert.html type="warning" content="If your program is not showing your new page, and instead says \"Welcome to Xamarin Forms!\", then it is likely that you've forgotten to update this code to use your new class."
%}
