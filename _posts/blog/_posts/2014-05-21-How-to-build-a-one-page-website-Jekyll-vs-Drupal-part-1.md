---
layout: blogpost
title: How to build a one page website Jekyll vs Drupal
categories: blog
part: Part 1
---

I follow Drupal for several years and I must admit that Drupal is becoming a real beast. The possibilities and the contributed modules are endless so to speak.

If you are new to Drupal  you can really get lost.

A friend came to me to build a simple website for his small hotel. The hotel has 6 rooms in total and 3 room types.  We will just have to show the rooms, a map, contact information and a form to ask the hotel owner for availability. 

So I thought it was a suitable project to build a one page website.

And an idea came to me. I will try to build it with Drupal but then I will try to build it again with the latest trend of static websites using Jekyll and see by first hand what is the best tool for the job.

The purpose of this exercise is to learn new things (e.x. Jekyll) and also challenge Drupal. I want to use the simplest way to build it, for me and for someone just starting in Drupal.

 
##**Find a html template**
You can browse:

- [Theme Forest](http://themeforest.net) 
- [Creative Market](https://creativemarket.com/)
- [One Page Love](http://onepagelove.com)

or other sites and find a lot of one page sites for inspiration

I found one to use as inspiration.
So the end result will be like this [HotelDrupal](hoteldrupal.techangel.me)

##Drupal approach: **Panels vs Display Suite-Context**

Then we have to decide the drupal approach to tackle this task. 
Should we use the DS - Context combination or Panels?
I will built it both ways and see what is the simplest way.
I personally like the **Display Suite / Context / Omega 4.x theme** approach, so let's start with this.

I also wanted to try the **[Bean](https://drupal.org/project/bean)** module. It helps you create Block types just as you would Content types. So instead of creating nodes you create blocks so you easily attach them to right region in context.

We will build the following Block types

 - Slideshow Bean Block 
 - Slideshow Text Bean Block 
 - Rooms Bean Block 
 - Map Bean Block 
 - Contact Bean Block


Next in the series all the needed Modules that we must download.

[Next](http://router-lactic.codio.io:4000/blog/2014/05/22/How-to-build-a-one-page-website-Jekyll-vs-Drupal-part-2-Modules/)