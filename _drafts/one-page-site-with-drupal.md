---
layout: blog
title: One page site with Drupal
categories: blog

---

Drupal is becoming a real beast. The possibilities and the contributed modules are endless so to speak.

If you are not a programmer or a newby in drupal  you can really get lost.

I know my way in Drupal so I wanted to build a one page site as everybody does nowadays. It was for a small hotel - 6 rooms total, 3 room types.  We will just have to show the rooms and a form to ask the hotel owner for availability. 

So it was suitable project. 

##Find a html template
You can browse:
+ [Theme Forest](http://themeforest.net) 
+ [Creative Market](https://creativemarket.com/)
or other sites and find a lot of one page sites for inspiration

I found one to use it as inspiration.

Then we have to decide the drupal approach to tackle this task. I personally like the **Display Suite / Context / Omega 4.x theme** approach, so let's get started.

I also wanted to try the **Bean** module. It helps you create Block types just as you would Content types. So instead of creating nodes you create blocks so you easily attach them to right region in context.

###Modules I used:
###**Fields**

 - [Field Slideshow](https://drupal.org/project/field_slideshow) 	
 - Documentation https://drupal.org/node/1495622 	
 - Dependencies 	
 	- Library 	
 	-  jCycle
 	> wget  http://malsup.github.com/jquery.cycle.all.js)

If you get this message:
	> JQuery ImagesLoaded pluginNot found For best results, you should download the JQuery ImagesLoaded plugin and move the downloaded js file(s) into the /sites/all/libraries/jquery.imagesloaded folder of your server. 
Read this: https://drupal.org/node/1897588#comment-7631479

+	[Tablefield](https://drupal.org/project/tablefield)
+	[Email](https://drupal.org/project/email)
+	[Link](https://drupal.org/project/link)
		> drush dl tablefield
		>drush en -y tablefield,email,link
###**Blocks**
+ [Bean](https://drupal.org/project/bean)
+ [Bean entity view](https://drupal.org/project/bean_entity_view)
> drush dl bean,bean_entity_view
> drush en -y bean,bean_admin_ui,
###**Menus**
+ [Void menu](https://drupal.org/project/void_menu)
> drush dl void_menu
> drush en -y void_menu
###**Contact Form**
+ [Webform](https://drupal.org/project/webform)
+ [Webform AJAX](https://drupal.org/project/webform_ajax)
+ [Clientside Validation Webform](https://drupal.org/project/clientside_validation)
> drush dl webform,clientside_validation,webform_ajax
> drush en -y webform,clientside_validation,webform_ajax
###**Theme**
+ [Context](https://drupal.org/project/context)
+ [Context omega](https://drupal.org/project/context_omega)
+ [Display Suite](https://drupal.org/project/ds)
+ [Entity view mode](https://drupal.org/project/entity_view_mode)
+ Flexslider
To use Thumbnail Captions you must install FlexSlider version 2.2 or higher.
+[Title](https://drupal.org/project/title)
+ field_formatter_settings
+[ FontyourFace](https://drupal.org/project/fontyourface)
+[Imagefield Focus)(https://drupal.org/project/imagefield_focus)

> drush dl context,context_omega,ds,ds_ui,ds_extras, flexslider,field_slideshow
> drush en -y context_ui,context,context_omega,ds,ds_ui,ds_extras, flexslider,field_slideshow
####**Fonts**
+ [@font-your-face UI](https://drupal.org/project/fontyourface)
> drush dl fontyourface
####**Maps**
+ [Leaflet](https://drupal.org/project/leaflet)
+ [IP Geolocation Views & Maps](https://drupal.org/project/ip_geoloc)
    optional 
    + [Leaflet More Maps](https://drupal.org/project/leaflet_more_maps)
    + [Leaflet MapBox](https://drupal.org/project/leaflet_mapbox)
> drush dl ip_geoloc,leaflet_more_maps,leaflet_mapbox
####**Optimize**
+ [Advanced CSS/JS Aggregation](https://drupal.org/project/advagg)
> drush dl advagg

###Theme I used:
+ [Omega v4](https://drupal.org/project/omega)
> drush dl omega
> drush omega-wizard
			+ Name of the theme
			+ Machine name of the theme
			+ 	Choose (3) - Omega - A powerful HTML5 base theme framework utilizing tools like     
         Sass, Compass, Grunt, Bower, Ruby Version Manager, Bundler and more.
         + Starterkit: choose (1)
         +  Please choose a destination. This is where your sub-theme will be placed: 
        sites/your domain/themes
 +	Choose Yes (y) to the rest of the questions
 +	
###Admin Tools and more:

	- [Admin Menu](https://drupal.org/project/admin_menu)
	- [Environment Indicator](https://drupal.org/project/environment_indicator)
	- [Module Filter](https://drupal.org/project/module_filter)
	- [Fast Permissions](https://drupal.org/project/fpa)
	- [Libraries](https://drupal.org/project/libraries)
	- [Views]

	Better manage where the images will be stored
	
	- [File field Sources](https://drupal.org/project/filefield_sources)
	- [FileField Sources Plupload](https://drupal.org/project/filefield_sources_plupload)
	- [File Field Paths](https://drupal.org/project/filefield_paths) - images/rooms
	- [Token]
	- [Path]
	- [Plupload integration](https://drupal.org/project/plupload)
	- [Image style flush](https://drupal.org/project/imagestyleflush)
		> drush dis overlay,toolbar,color,comment,dashboard,shortcut
		> drush dl admin_menu,environment_indicator,module_filter,fpa,libraries
		> drush en -y admin_menu,admin_menu_toolbar,admin_views,environment_indicator,module_filter,fpa
Image toolkit 95%

###Everything - Download All Modules
	> drush dl 

##**Bean - Block Types**
###**For Slideshow + Text on top**

#### **SimpleText Bean** - fields:
+ **Title bean** - type: Text -  the first line in the slideshow - I created this field because I had a problem themming the default title field of the bean
+ **Subheader** - type: Text - the second line in the slideshow
    
###**Slideshow Bean** - fields:
+ **Slideshow** - type: Image - number of images we want in the slideshow

and the rest of the bean are self-explanatory

###**Rooms Bean** - fields:
- **Subheader**	- type: Text - the text below the title - **existing**
- **Slideshow** -type: Image/multiple - the rest of the images**existing**
- **Prices** - type: Table Field - the table with the prices - Select rows / columns and table tittle
- **Description** -type:Long Text - the desription for the room

###**Contact_bean** - fields
+ **Subheader** - type: Text
+ **Email** -type: Email
+ **Phone** -type: Text - so that you will add the +30 in integer it doesnot take it
+ **Facebook** -type: Link
+ **Twitter** -type: Link

###**Map Bean** - fields
- Location - type: geofield - widget: Longitude / Latitude
- Find Longitude - Latitude http://universimmedia.pagesperso-orange.fr/geo/loc.htm


and I created a webform
###**Webform** - Form components
+ **Check In** -type: Date
+ **Check Out** -type: Date
+ **Name** -type: Textfield	
+ **email** -type: E-mail	
+ **Persons	Number** -type: Number	
+ **Room type** -type: Select options
+ 
##How to create the webform validation and stay in the same page
You must enable the **Clientside Validation Webform** which is also straight forward






###**Menu**
####how to  create anchor link menus work in drupal
####How to make anchor link menus work in the same page
####[Void Menu](https://drupal.org/project/void_menu) to the rescue

It gives you the ablility to add anchor links to drupal menu field link
It is a simple straightforward module. 

Void menun settings page
**/admin/config/user-interface/void_menu**

This is the settings page where you can assign an HTML value for every void (void1:#onebedroom, void2:#studio, etc.), then you go to edit your menu links and add to the menu path the void variable that you want e.x. <void3>

The other important thing is that you have to add to the template the anchor links. More about that later.

##**Layout**
Create new page template - simpler 
## Page layout
### hotelonepage.layout.inc
>name = OnePage
description = A simple OnePage layout.
preview = preview.png
template = onepage-layout
>;Regions
regions[header]         = Header
regions[navigation]     = Navigation bar
regions[slideshow]    	= Slideshow
regions[help]           = Help
regions[content]        = Content
regions[content1]        = Content1
regions[content2]        = Content2
regions[content3]        = Content3
regions[content4]        = Content4
regions[content5]        = Content5
regions[content6]        = Content6
regions[sidebar_first]  = First sidebar
regions[sidebar_second] = Second sidebar
regions[footer]         = Footer
>; Stylesheets
stylesheets[all][] = css/layouts/onepage/onepage.layout.css

###hotelonepage-layout.tpl.php

    	####Slideshow
    	
    	'' '
    	 <div class="l-slideshow">
  <?php if ($logo): ?>
          <a href="<?php print $front_page; ?>" title="<?php print t('Home'); ?>" rel="home" class="site-logo">			  <img src="<?php print $logo; ?>" alt="<?php print t('Home'); ?>" /></a>
       <?php endif; ?>
' ''
####Content Sections
We must a wrapper around it plus a 
<a name="studio"></a>
for the anchor links to work
The problem here is that the anchor links mudt be predicided. Probably we can build a custom module to control this thgough the UI

####Section 1 -Content
	 <div class="content-wrapper">
      <?php print render($page['content']); ?>
      </div>
####Section 2 -Content 1
      <div class="content1-wrapper">
      <a name="studio"></a>
      <?php print render($page['content1']); ?>
      </div>
####Section 3 -Content 2
      <div class="content2-wrapper">
      <a name="onebedroom"></a>
      <?php print render($page['content2']); ?>
      </div>
####Section 4 -Content 3
      <div class="content3-wrapper">
      <a name="twobedroom"></a>
      <?php print render($page['content3']); ?>
      </div>
####Section 5 -Content 4
      <div class="content4-wrapper">
      <a name="reservation"></a>
      <?php print render($page['content4']); ?>
      </div>
####Section 5 -Content 5
      <div class="content5-wrapper">
      <?php print render($page['content5']); ?>
      </div>
####Section 4 -Content 6
      <div  class="content6-wrapper">
      <a name="contact"></a>
      <?php print render($page['content6']); ?>
      </div>    


###Footer
<div class="l-footer-wrapper" >
  <footer class="l-footer" role="contentinfo">
    <div class="l-footer1"> <?php print render($page['footer1']); ?> </div>
    </footer>
 </div>
  
link to onepage template - github
link to sass - github
link to css - github

###Add to the theme the new regions
####info file
>regions
name = hotel_omega
description = Hotel Onepage Theme
base theme = omega
screenshot = screenshot.png
engine = phptemplate
core = 7.x
stylesheets[all][] = css/reset.css
stylesheets[all][] = css/hacks.css
stylesheets[all][] = css/styles.css
regions[header] = Header
regions[navigation] = Navigation
regions[slideshow] = Slideshow
regions[help] = Help
regions[content] = Content
regions[content1] = Content1
regions[content2] = Content2
regions[content3] = Content3
regions[content4] = Content4
regions[content5] = Content5
regions[content6] = Content6
regions[sidebar_first] = First Sidebar
regions[sidebar_second] = Second Sidebar
regions[footer] = Footer

scripts[] = js/jquery.formalize.js
scripts[] = js/jquery.easescroll.js

Enable layout module in omega theme
###one page layout
create onepage layout and put it here
you can download it from here
>git clone ...
SaaS  folder create layouts folder nad put in there a folder name onepage nad the file inside 
onepage.layout.scss
Essentialy it will built the css file in the structure that we defined
> css/layouts/onepage/onepage.layout.css
in .inc in the onepage layout folder we create

###Context 
create a new context onepagelayout and attach each bean-block to right order
Choose Condition path <front>

##Now lets start theming- styling
RVM - https://drupal.org/node/1936970
RVM - ubuntu - https://drupal.org/node/2052955
##**Styles**
###Image styles
overide the flexslider_full style to Scale and crop 1600x500
###Display suite
Hide all labels
Enable extras
Enable field templates
Add custom classes 
table: prices
description: expert p
subheader: expert h2 .subheader
slideshow rooms: rooms
Main slideshow text:  expert h1.slideshow-title
									slideshow-subheader

####Slideshow
The field image slideshow you can select the **flexslider style** and the **flexslider_full**
<none> to all bean blocks
####Rooms DS layout
Create new view mode - Onepage
Create a new ds layout
>cd sites/[%your site%]/themes/ansiv2
> mkdir ds_layouts
> cd ds_layouts
>drush ds-build "Rooms layout" --regions="header,column1,column2,footer" --image

Edit the files and add them to the sass files and add additional class names

>ds layout
####Maps 
+ Choose Format:Leaflet
+ Popup settings
+ Zoom - initial zoom
Choose Display Onepage

We will use the power of the new omega theme with  the layouts
We will create a new layout
we can create a list and then add the parallax effect
or create module to add anchor link to bean template - not all bean ex. mpa webform
must go to the template from a module show regions and add to them anchor link

####Webform