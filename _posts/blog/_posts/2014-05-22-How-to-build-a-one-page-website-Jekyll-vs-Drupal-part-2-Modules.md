---
layout: blogpost
title: How to build a one page website Jekyll vs Drupal
categories: blog
part: Part 2 - Modules
---

###Modules I used:

###Admin Tools and more:
Very useful modules, needed in any drupal project:

 - [Admin Menu](https://drupal.org/project/admin_menu) 
 - [Environment Indicator](https://drupal.org/project/environment_indicator) 
 - [Module Filter](https://drupal.org/project/module_filter) 
 - [Fast Permissions](https://drupal.org/project/fpa)   
 - [Libraries](https://drupal.org/project/libraries)
 - [Image style flush](https://drupal.org/project/imagestyleflush)
 - [Quickupdate](https://drupal.org/project/quickupdate)
 - [Token](https://drupal.org/project/token)

 Optonal - Easier image upload for the end user
 
 - [File field Sources](https://drupal.org/project/filefield_sources)
 - [FileField Sources Plupload](https://drupal.org/project/filefield_sources_plupload)
 - [Plupload integration](https://drupal.org/project/plupload)- multiple image upload
 
#####the code

        cd sites/all/libraries 
        wget https://github.com/moxiecode/plupload/archive/v1.5.8.zip
        drush dl admin_menu,admin_menu_toolbar,admin_views,environment_indicator,module_filter,fpa
        drush en -y admin_menu,admin_menu_toolbar,admin_views,environment_indicator,module_filter,fpa

 	
Settings
Image toolkit 95%

    drush dis overlay,toolbar,color,comment,dashboard,shortcut
    drush dl admin_menu,environment_indicator,module_filter,fpa,libraries
    drush en -y 
		
###**Fields**
-	[Tablefield](https://drupal.org/project/tablefield)
-	[Email](https://drupal.org/project/email)
-	[Link](https://drupal.org/project/link)
-   [Field Slideshow](https://drupal.org/project/field_slideshow) 	
        Documentation https://drupal.org/node/1495622 	
        Dependencies 	
        Library 
        jCycle	
 	     wget  http://malsup.github.com/jquery.cycle.all.js
         If you get this message:
         > JQuery ImagesLoaded pluginNot found For best results, you should download the JQuery ImagesLoaded plugin and move the downloaded js file(s) into the /sites/all/libraries/jquery.imagesloaded folder of your server. 
         Read this: https://drupal.org/node/1897588#comment-7631479


		> drush dl tablefield,link,email
		>drush en -y tablefield,email,link
        
###**Blocks**
+ [Bean](https://drupal.org/project/bean)
+ [Bean entity view](https://drupal.org/project/bean_entity_view)

        > drush dl bean,bean_entity_view
        > drush en -y bean,bean_admin_ui


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
+ [Title](https://drupal.org/project/title)
+ [Context](https://drupal.org/project/context)
+ [Context omega](https://drupal.org/project/context_omega)
+ [Display Suite](https://drupal.org/project/ds)
+ [Flexslider](https://drupal.org/project/flexslider)
To use Thumbnail Captions you must install FlexSlider version 2.2 or higher.
	
+ field_formatter_settings

+[Imagefield Focus)(https://drupal.org/project/imagefield_focus)

    > drush dl context,context_omega,ds,ds_ui,ds_extras, flexslider,field_slideshow
    > drush en -y context_ui,context,context_omega,ds,ds_ui,ds_extras, flexslider,field_slideshow

####**Fonts**
+ [@font-your-face UI](https://drupal.org/project/fontyourface)

        > drush dl fontyourface
        > drush en fontyourface

####**Maps**
+ [geofield](https://drupal.org/project/geofield)
+ [Leaflet](https://drupal.org/project/leaflet)
+ [Leaflet More Maps](https://drupal.org/project/leaflet_more_maps)
+ [Leaflet MapBox](https://drupal.org/project/leaflet_mapbox)

        > drush dl leaflet_more_maps,leaflet_mapbox

####**Optimize**
+ [Advanced CSS/JS Aggregation](https://drupal.org/project/advagg)
        > drush dl advagg

###Theme I used:
+ [Omega v4](https://drupal.org/project/omega)
        > drush dl omega
        > drush omega-wizard

        $ Name of the theme: Hotel One Page Theme
        $ Machine name of the theme: hotel_omega_onepage
        $ Choose (3) - [Omega - A powerful HTML5 base theme framework utilizing tools like     
                 Sass, Compass, Grunt, Bower, Ruby Version Manager, Bundler and more.]
        $ Starterkit: choose (1)
        $ Please choose a destination. This is where your sub-theme will be placed: 
                sites/(your domain)/themes
        $ Choose Yes (y) to the rest of the questions

###Everything - Download All Modules
	> drush dl 
	
Next in the series: How to build the Bean Blocks