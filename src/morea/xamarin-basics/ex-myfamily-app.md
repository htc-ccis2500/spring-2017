---
title: "Family App"
published: true
morea_id: ex-myfamily-app
morea_type: experience
morea_summary: "Create a simple Xamarin.Forms application to introduce your family."
morea_sort_order: 1
morea_labels:
 - Xamarin.Forms
---

# {{ page.title }}
{{ page.morea_summary }}

## The Family App
Create a new Xamarin.Forms application called FamilyApp, and add it to GitHub.  You may push the initial template to the master branch, but remember to setup a development/feature branch for your work.

## Custom Main Page
Add a new `ContentPage` class called `FamilyAppPage` to the application.  Add text to the page that introduces various members of your family.  A sentence or two for each person is fine.  You should add at least 5 people, but can add more if you like. Add multiple paragraphs, one for each member of the family.

### Style the Text
No more black and white here.  Add some custom styling to make your family stand out.  For this application you must:

- Use bold text and increase the font size of each family member's name
- Set a different background color for the page
- Use a different font color for each family member
- Use a StackLayout with a Label for each member of the family


## Test
Test your application using the Android & Windows phone emulators (optionally iOS).  Make sure that your font choices are all readable, and that the application meets the requirements shown above.  Take a screenshot of your successful test on each platform to place in the assignment submission box.  


## Submit
Commit your changes to your development/feature branch and push to GitHub. Open a pull-request for the work. __Do NOT commit or merge to master.__

Upload the following screenshots to the Assignment box:

1. Your Family app running on Android
2. Your Family app running on Windows Phone
3. Your Family app running on Windows and/or iOS (optional)
4. A GitHub website screenshot clearly showing your GitHub username, repository and open pull-request

Clearly label all the screenshots and add them individually to the dropbox, or paste them into a single MS Word document to upload.   Please do not zip the screenshots.

## Need more challenge?
If you're ready to try something a little different and with less hand-holding, try branching out on your own.  First, literally, branch out and make a new dev/feature branch for this work. It is important that you __DO NOT__ break the code that you submitted above.

Next, use the information from the [Xamarin.Forms Pages](https://developer.xamarin.com/guides/xamarin-forms/controls/pages/) class documentation to alter your application to use a `MasterDetailPage` or a `CarouselPage` instead of the `NavigationPage`.  

Submit a second pull-request for this work if completed. (Or heck, do it to show me that you tried!)
