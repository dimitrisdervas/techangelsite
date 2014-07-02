---
layout: blogpost
title: How to build a one page website Jekyll vs Drupal
categories: blog
part: Part 3 - Bean Blocks
---
Let's start creating the block types that we are going to use.
We need a

 - Slideshow 
 - Slideshow text 
 - 3 Room types
 - Map 
 - Contact

##**Bean - Block Types**

###**Slideshow Bean** 
Fields:

+ **Slideshow** - type: Image - number of images we want in the slideshow

and the rest of the bean are self-explanatory
filefield path
images/slideshow

FILE SOURCES


### **SimpleText Bean** - 
Fields:

+ **Header** - type: Text -  the first line in the slideshow - I created this field because I had a problem themming the default title field of the bean
+ **Subheader** - type: Text - the second line in the slideshow
    
<!--more-->

###**Rooms Bean** - fields:
- **Subheader**	- type: Text - the text below the title - **existing**
- **Slideshow** -type: Image/multiple - the rest of the images- **existing**
- **Prices** - type: Table Field - the table with the prices - Select e.x. 3 rows 2 colums rows / columns and table tittle
- **Description** -type:Long Text - the desription for the room
and the rest of the bean are self-explanatory
filefield path
images/rooms
FILE SOURCES

###**Contact_bean** - fields:
+ **Subheader** - type: Text
+ **Email** -type: Email
+ **Phone** -type: Text - so that you will add the +30 in integer it doesnot take it
+ **Facebook** -type: Link
+ **Twitter** -type: Link

###**Map Bean** - fields
- Location - type: geofield - widget: Longitude / Latitude
- Find Longitude - Latitude http://universimmedia.pagesperso-orange.fr/geo/loc.htm


and I also created a webform

###**Reservation Webform** - Form components
+ **Check In** -type: Date
+ **Check Out** -type: Date
+ **Name** -type: Textfield	
+ **email** -type: E-mail	
+ **Persons	Number** -type: Number	
+ **Room type** -type: Select options

Form settings - show as block - enable ajax
You must enable the **Clientside Validation Webform** which is also straight forward

###**Menu**

####How to  create anchor link menus work in drupal

####[Void Menu](https://drupal.org/project/void_menu) to the rescue

It gives you the ablility to add anchor links to drupal menu field link
It is a simple straightforward module. 

Void menun settings page
**/admin/config/user-interface/void_menu**

This is the settings page where you can assign an HTML value for every void (void1:##content1, void2:##content2, etc.), then you go to edit your menu links and add to the menu path the void variable that you want e.x. <void3>

The other important thing is that you have to add to the template the anchor links. More about that later.

Now start creating your content and then we will see

Next in the series: **How to make the theme layout in Omega**
