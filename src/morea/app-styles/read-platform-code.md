---
title: "Platform Code"
published: true
morea_id: read-platform-code
morea_summary: "Using platform specific code and features in a Xamarin.Forms application."
morea_type: reading
morea_sort_order: 1
morea_labels:
 - Xamarin.Forms
---

## {{ page.title }}
{{ page.morea_summary }}


## Platform Specific API Calls
Read Chapter 9 of [Creating Mobile Apps with Xamarin.Forms](https://developer.xamarin.com/guides/xamarin-forms/creating-mobile-apps-xamarin-forms/) by Charles Petzold. This chapter introduces using platform specific API code within your mobile application. While the example in this chapter focuses on sound, keep in mind that sound is just used as an example of something that must be done in a platform-specific way. The same technique can be used to include other platform-specific features as well.

{% include alert.html type="info" content="Note that we have been building Portable Class Library (PCL) applications which are covered separately following the section on Shared Asset Project (SAP) applications. You can skim over or skip the information on SAP apps." %}

### Platform-specific Sound
The example discussed in this chapter adds sound, and the discussion begins with general information on sound for mobile apps. While compressed sound is great for commercial music files, compressed formats are less ideal when programs need to programmatically generate sounds. PCM (pulse code modulation) is the cross platform technique used in this chapter.

If you are interested in apps that make use of sounds, you might pay more attention to the details presented in this chapter. If your interests are more with business applications, you might skim over this, pulling just enough information to add some basic sound to an app.
