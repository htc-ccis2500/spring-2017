---
title: "Application Structure"
published: true
morea_id: read-xamarin-basics
morea_summary: "An introduction to the structure of a Xamarin.Forms cross-platform mobile application."
morea_type: reading
morea_sort_order: 3
morea_labels:
 - Xamarin.Forms
---

## {{ page.title }}
{{ page.morea_summary }}

## Reference Text
Chapters 1-2 of [Creating Mobile Apps with Xamarin.Forms](https://developer.xamarin.com/guides/xamarin-forms/creating-mobile-apps-xamarin-forms/) by Charles Petzold.  

## Inside the App
Let's take a deeper look at the shared code inside a basic Xamarin.Forms portable application project.  

First, notice that the main class `App` (in the App.cs file) inherits from the `Application` class which is part of `Xamarin.Forms`.  The code we will be writing is heavily object oriented.  We will be using and extending many classes provided by the Xamarin framework.

{% highlight csharp %}
public class App : Application
{
    ... code hidden ...
}
{% endhighlight %}


## User Interface
Next let's start looking in more depth at the user interface code.  There are 3 main categories of objects that we can have on the screen:  pages, layouts, and views. If you've worked with user interface code in the past these types of objects should sound familiar.

### Pages
The Xamarin.Forms applications are organized into pages.  As you might expect, a page generally fills the device screen.  We might have a single page application, or we might have one with many pages that flow from one to another.  The sample application that we looked at earlier is a single page application built using a [`ContentPage`](https://developer.xamarin.com/api/type/Xamarin.Forms.ContentPage/).  

The `App` class sets the `MainPage` of the application.  The template starts you out with a simple page built right inside the `App` class constructor itself. It does this by creating a new `ContentPage`.  This is one of several different page types supported by Xamarin.Forms. We will look at other types later, but they include `MasterDetailPage`, `NavigationPage`, `TabbedPage`, `TemplatedPage`, and `CarouselPage`.  (Learn more about the other types in the [Page]() class documentation.)

### Template App
Let's look more closely at how this is done in the template application. The constructor itself uses the object initializer syntax to create a set of nested objects inside of a `ContentPage`. This happens in lines 5-17 of the code snippet below.  Then on line 19, we use that to create a new `NavigationPage` instance which we use to set the `MainPage` property of our `Application` object.  

{% highlight C# linenos %}
    public App()
    {
        // The root page of your application
        var content = new ContentPage
        {
            Title = "HelloXamarin",
            Content = new StackLayout
            {
                VerticalOptions = LayoutOptions.Center,
                Children = {
                    new Label {
                        HorizontalTextAlignment = TextAlignment.Center,
                        Text = "Welcome to Xamarin Forms!"
                    }
                }
            }
        };

        MainPage = new NavigationPage(content);
    }
{% endhighlight %}

Before you worry about all those new object types, make sure you understand how that object initializer syntax is working. We start by creating that new `ContentPage`, but inside of that they are setting two properties.  Notice they are separated by a comma (,).  The first is the `Title`.  It's simple; just a String.  

The second property, `Content`, (line 7) is being set to another object also being created with the object initializer syntax.  It also has two properties: `VerticalOptions` (line 9) and `Children` (line 10).  Notice that again `Children` is a new object created with the object initializer syntax.  It a new `Label` which also has two properties: `HorizontalTextAlignment` and `Text`.

## Custom Page Class
As you might imagine, this is a very simple example, and real application code gets much more complex.  Instead of putting all of the page layout code into the `App.cs` file, it is typical to create a custom page class that extends `ContentPage` in a new file. The standard convention is to name the class using the name of your application + Page.  For example, for an app called "MyApp" the main page class would be called `MyAppPage`.

Shown below, I've taken the template code from the `App` class constructor that creates the *content* of the page and moved it to a new class called `MyAppPage` which extends `ContentPage`.

{% highlight C# linenos %}
class MyAppPage : ContentPage
{
    // The constructor
    public MyAppPage()
    {
        Title = "HelloXamarin";  // Modified to end with ;
        Content = new StackLayout
        {
            VerticalOptions = LayoutOptions.Center,
            Children = {
                new Label {
                    HorizontalTextAlignment = TextAlignment.Center,
                    Text = "Welcome to Xamarin Forms!"
                }
            }
        }; // Modified to end with ;
    }
}
{% endhighlight %}

After creating a custom page class, we must update the `App` constructor code to remove all this sample page junk and just create an instance of our new class.  

{% highlight C# %}
class MyAppPage : ContentPage
{
    public App()
    {
        // The root page of your application
        MainPage = new NavigationPage(new AboutMePage());
    }
}
{% endhighlight %}

Note that the result of running the application is exactly the same, but we've moved the code around so that it is easier to add onto and maintain.  To do this, understanding both the standard C# object syntax and the object initializer syntax used by the examples is key.

Now we can make changes to our new App and begin customizing our own user interface.  Let's start simple and just update the title and the text shown.

{% highlight C# linenos %}
class MyAppPage : ContentPage
{
    // The constructor
    public MyAppPage()
    {
        Title = "Hello .Net Mobile!";  // Modified for new title
        Content = new StackLayout
        {
            VerticalOptions = LayoutOptions.Center,
            Children = {
                new Label {
                    HorizontalTextAlignment = TextAlignment.Center,
                    Text = "Welcome to the .Net Mobile class!"  // Modified for new text
                }
            }
        };
    }
}
{% endhighlight %}

{% include alert.html type="warning" content="If your program is not showing your new page, and instead says \"Welcome to Xamarin Forms!\", then it is likely that you've forgotten to update this code to use your new class."
%}
