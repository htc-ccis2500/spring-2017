---
title: "Scrolling Pages"
published: true
morea_id: read-xamarin-scrolling
morea_summary: "Adding scrolling to a page in a Xamarin.Forms application."
morea_type: reading
morea_sort_order: 5
morea_labels:
 - Xamarin.Forms
---

## {{ page.title }}
{{ page.morea_summary }}

## Reference Text
Chapter 4 of [Creating Mobile Apps with Xamarin.Forms](https://developer.xamarin.com/guides/xamarin-forms/creating-mobile-apps-xamarin-forms/) by Charles Petzold.  

## StackLayout
You might have noticed that the template application used a `StackLayout`.  Let's look into that in a bit more detail to understand better what it is and how it can be used in our application pages.  

The `StackLayout` allows you to *stack* a collection of child elements one on top of the other to fill a page.  It has a `Spacing` property (type double) that you can use to control how much space is between each child. The default is 6.0, and this is in those generic *units* again.  You can alter the spacing to be bigger or smaller (even negative) to alter your display.

{% highlight csharp %}
  Content = new StackLayout
  {
      Spacing = 3.0,
      Children =
      {
          new Label { Text = "Child 1" },
          new Label { Text = "Child 2" },
          new Label { Text = "Child 3" }
      }
  }
{% endhighlight %}

The problem with this is that if there are too many, or they are too large, they overflow the screen.  That hides some of the data in a rather frustrating (for the end user) sort of way.  You know its there, but how do you get to it?!


## Scrolling to the rescue
The `ScrollView` helps avoid frustration from content that is too large for the device screen size by allowing the content to scroll. The default is for the scroll view to vertically scroll, but there is an `Orientation` property that can be set to alter that to horizontal.

{% highlight csharp %}
  Content = new StackLayout
  {
      Orientation = StackOrientation.Horizontal,
      Children =
      {
          new Label { Text = "Child 1" },
          new Label { Text = "Child 2" },
          new Label { Text = "Child 3" }
      }
  }
{% endhighlight %}


## Fill & Expand
The `ScrollView` has several layout options that are worth noting and understanding.  We have seen `LayoutOptions.Start`, `LayoutOptions.Center`, and `LayoutOptions.End` already.  There is also a `LayoutOptions.Fill` which causes the content to expand to fill its container.  There are also 4 additional properties which have expand capabilities only recognized by the `StackLayout`: `LayoutOptions.StartAndExpand`, `LayoutOptions.CenterAndExpand`, `LayoutOptions.EndAndExpand`, and `LayoutOptions.FillAndExpand`.  

These *expands* properties come into play when the stack would not fill the full vertical space.  When at least one child has a `VerticalOptions` setting which expands, the *extra* vertical space is allocated to all those children which expand, causing them to grow larger so the available space is used.  This can be confusing if you are not seeing an example of how it works.  Look at the example from the reference text and experiment with these layout values in your own application.

## Embedded Resources
There is a bit of a hidden gem in Chapter 4 of our reference text, embedding data inside of the application class library DLL.  This is at the end of the chapter and is shown inside the discussion "A ScrollView in a StackLayout".  Until we learn to work with other datasources, this might provide an interesting way to store program data.  The downside is of course that you would have to have everyone update their version of the app to get new data.
