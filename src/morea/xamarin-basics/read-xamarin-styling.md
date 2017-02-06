---
title: "Text Formatting"
published: true
morea_id: read-xamarin-styling
morea_summary: "Basic information on styling text in a Xamarin.Forms application."
morea_type: reading
morea_sort_order: 4
morea_labels:
 - Xamarin.Forms
---

## {{ page.title }}
{{ page.morea_summary }}

## Reference Text
Chapters 3 & 5 of [Creating Mobile Apps with Xamarin.Forms](https://developer.xamarin.com/guides/xamarin-forms/creating-mobile-apps-xamarin-forms/) by Charles Petzold.  

## Text Formatting
Text is often a large part of what applications (particularly business applications) show.  Boring as it is, we should spend some time looking at how to structure it and alter its presentation and layout.

A `Label` can hold long strings of text, which can look like a paragraph.  If we add newline characters `\n` to the string, it can become more than one paragraph.  Of course it would be better to use the `Environment.NewLine` property to avoid any platform specific differences in the newline character.  

{% highlight csharp %}
  new Label {
      Text = "Welcome to the .Net Mobile class!" +
          Environment.NewLine + Environment.NewLine +
          "More text on a newline!!!"
  }
{% endhighlight %}

We can also set properties to alter the positioning of our text.  We saw the `HorizontalTextAlignment` set on the `Label` in the template code. There is also `VerticalTextAlignment`.  The possible values for these are: `TextAlignment.Start`,  `TextAlignment.Center` and `TextAlignment.End`.  Experiment with these to see how the display is changed.

Notice that the template code also set the `VerticalOptions` on the `Layout` class. There are also `HorizontalOptions` and they have similar possible values as the `TextAlignment` above: `LayoutOptions.Start`, `LayoutOptions.Center`, and `LayoutOptions.End`. Again experiment with these, setting them and removing them, to see how the display is altered. Note that once you have set the `VerticalOptions`, setting the `VerticalTextAlignment` option has no affect.  

## Colors
There are also display properties for setting colors, both on the text and the background on a `Label`. To set the text color, use the `TextColor` property.  To set the background color, set the `BackgroundColor`. The text color can only be set on a `Label`, but the `BackgroundColor` can be applied to `Label`, `Layout`, and `Page` objects.  

By default these color properties are set to `Color.Default` which represents a color appropriate for your platform.  This means that it will be different on iOS, Android, and Windows Phone.  You've probably already noticed that your application displays differently in each of the emulators.  These *default* colors can be modified for your application on Android and Windows phone.  (See Changing the application color scheme, in the reference text.)

There are 17 public static read-only color options, but custom colors can also be created.  The color can be set in three different ways, as shown by the constructors and static creation methods on the `Color` class: using RGB, using RGBA, and using HSLA.  See the documentation for details: [Color class](https://developer.xamarin.com/api/type/Xamarin.Forms.Color/).

{% include alert.html type="danger" content="The static methods divide your input by 255, which will likely not give you what you want.  Pass in decimal values to these methods instead." %}

## Font Size and Style
There are also `Label` properties that can be used for changing the display of the text.  You can change the font used with the `FontFamily` property. You can set this to a font name, but the font must be supported by your platform.  To use this appropriately, you'll likely use it with `Device.OnPlatform` and you'll need to know the supported fonts for the targeted system.  

The size can be set using `FontSize`, which can think of as using generic *units*. (A *lot* more information on sizing is provide in Chapter 5 of the reference text.)  For now, there are some `NamedSizes` that you can use easily: `Default`, `Micro`, `Small`, `Medium`, and `Large`.

{% highlight csharp %}
  new Label {
      Text = "Welcome to the .Net Mobile class!",
      FontSize = Device.GetNamedSize(NamedSize.Medium, typeof(Label))
  }
{% endhighlight %}

There are also `FontAttributes` to set the font to `Bold` or `Italic`.

{% highlight csharp %}
  new Label {
      Text = "Welcome to the .Net Mobile class!",
      FontAttributes = FontAttributes.Bold
  }
{% endhighlight %}

## Mixing and Matching
So far we've been setting properties on the text for the entire `Label`, but we can use `FormattedText` property and the `FormattedString` class to mix the styling on text within a `Label`.  The `FormattedString` class structures the text into a series of `Span` objects which may each have different properties applied.  See (FormattedText section in the reference text for more information and an example.)
