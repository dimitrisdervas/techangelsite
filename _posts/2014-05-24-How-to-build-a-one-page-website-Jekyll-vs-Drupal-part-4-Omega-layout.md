---
title: How to build a one page website Jekyll vs Drupal
date: 2014-05-24 00:00:00 Z
categories:
- blog
layout: blogpost
part: Part 4 - Omega Layout
---

In the Omega Theme we can create new page layouts and it is relatively simple process.
We go here to our them and create a folder layout and then we create a folder with the name of our new page layout e.x.nepage
 Inside that folder we must create two files
 At first we create onepage.layout.inc where we will define the regions our page will have and define where it will find the css for the layo


### onepage.layout.inc
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



Then we must create thε onepage-layout.tpl.php which we will write the Html for our new layout.

###onepage-layout.tpl.php
     

     
####Content Sections

We must a wrapper around it plus a 
<a name="studio"></a>
for the anchor links to work
The problem here is that the anchor links must be predicided. Probably we can build a custom module to control this through the UI.
	
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
    </footer> </div>
 
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
create a new context onepagelayout 
Choose Condition 
Path: <front>
and put each bean-block to the right order


link to onepage template - github
link to sass - github
link to css - github
