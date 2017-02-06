---
title: "Family App - Part 2"
published: true
morea_id: ex-myfamily-app2
morea_type: experience
morea_summary: "Create a simple Xamarin.Forms application to introduce your family."
morea_sort_order: 2
morea_labels:
 - Xamarin.Forms
---

# {{ page.title }}
{{ page.morea_summary }}

## The Family App - Part 2
Add your Xamarin.Forms FamilyApp to GitHub.  You may push the initial work from last week to the master branch to begin with, but remember to setup a development/feature branch for your new work for this week.

## Custom Main Page
You should already have a new `ContentPage` class in your application.  It should already add text to the page that introduces various members of your family.  A sentence or two for each person is fine.  You will have multiple paragraphs, one for each member of the family.

Make sure that you have added at least 5 people.  But feel free to add more if you like.

### Style the Text
No more black and white here.  Add some custom styling to make your family stand out.  For this application you must:

- Use bold text and increase the font size of each family member's name (Done last week!)
- Set a different background color for the page (Done last week!)
- Use a different font color for each family member
- Use a StackLayout with a Label for each member of the family
- Use a ScrollView so that any overflow content is visible by scrolling
- Use a layout option to expand at least one (but not all) family members, so that it will expand to fill any left over space.


## Test
Test your application using the Android & Windows phone emulators (optionally iOS).  Make sure that your font choices are all readable, and that the application meets the requirements shown above.  Make sure you test that the scrolling is functional by adjusting your content quantity, size or emulator device size.

- Ensure that one screenshot illustrates the scrolling functionality was needed and tested successfully.  
- Ensure that another screenshot does not require scrolling and shows the expand behavior.

Take a screenshot of your successful test on each platform to place in the assignment submission box.  

## Submit
Commit your changes to your development/feature branch and push to GitHub. Open a pull-request for the work. __Do NOT commit or merge to master.__

Upload the following screenshots to the Assignment box:

1. Your Family app running on Android
2. Your Family app running on Windows Phone
3. Your Family app running on Windows and/or iOS (optional)
4. One or more additional screenshots to show the scroll & expand behavior
4. A GitHub website screenshot clearly showing your GitHub username, repository and open pull-request

Clearly label all the screenshots and add them individually to the dropbox, or paste them into a single MS Word document to upload.   Please do not zip the screenshots.

## Need more challenge?
If you're ready to try something a little different and with less hand-holding, try branching out on your own.  First, literally, branch out and make a new dev/feature branch for this work. It is important that you __DO NOT__ break the code that you submitted above.

Next, use the information from the [Xamarin.Forms Pages](https://developer.xamarin.com/guides/xamarin-forms/controls/pages/) class documentation to alter your application to use a `MasterDetailPage` or a `CarouselPage` instead of the `NavigationPage`.  

Submit a second pull-request for this work if completed. (Or heck, do it to show me that you tried!)
