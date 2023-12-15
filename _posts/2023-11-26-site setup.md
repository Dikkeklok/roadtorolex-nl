---
layout: post
title:  "Technical: site setup"
date:   2023-11-26 17:28:11 +0200
categories: technical
---
Similar to e-mail, we also need a space to post actual content. Picking a 'place' to post content should align with some of my wishes and future plans. In this blog I'd like to cover some of the options I considered, including my initial setup.

There are many easy and difficult ways to approach this, but I'd explictly mention that _content = key_. What I mean with this is that you can have the prettiest website in the world, but that if the content is trash people won't stick around. In line with content, I guess, actually producing content (either good or bad) is better than not publishing anything at all.

There are many ways to launch your own content online, so what works best might be different for each person or project.

## CMS vs own code, or a nice middle ground
For [https://dikkeklok.nl](https://dikkeklok.nl), the idea is to host a static [blog](https://dikkeklok.nl/blog). Most of the content will consist of text and supportive images. At least in the beginning this will be nothing fancy.

### CMS
A content management system is piece of (cloud) software used to manage the creation and modification of digital content. The most common CMS example for blogs and websites is probably [Wordpress](https://wordpress.com). A CMS such as wordpress makes it easy to structure text, images, and other content. They come with visual text editors and usually allows you to style your website with a variety of themes, which can be used to change the look and feel of the website, or allows plugins to enable additional features. Examples of such features are visitor comments, photo diretories, search fields, or helpful code that optimizes your site for search engine indextation (SEO). 

A CMS can be a good and user friendly way to get started. It has a way lower learning curve compared to creating your own website from scratch. But, you are limited to the options and features that the CMS provides.

### Own code
Having written some basic html, css, and javascript before, writing my own website from scratch is also an option to consider. It allows for maximum flexibility and can be styled in any way, shape, or form. However, setting up (coding) my own framework for easy publishing can be considered a project on its own.

## Middle ground - the Static site generator
_"Static site generators"_ are a nice middle ground between using a CMS and having the ability to write your own code. A static site generator can convert plain text into fully fledged webpages and usually have support for your own code while also allowing themes and plugins.

A tool such as [Jekyll](https://jekyllrb.com/) appears to be a good option. It allows me to focus on the content without having to worry too much about the technical website code while still being able to use themes and plugins.

## Paid vs Free hosting
Hosting companies have to make money somehow. So very often hosting a website comes with a certain cost. This costs is calculated between storage, traffic, and computation power.

A CMS usually requires some computation power, which can become pricey if the site generates more traffic. Since I'd like to keep costs to a minimum, going with a paid hosting environment is not an option. Luckily, storage and bandwidth is relatively cheap these days, and plenty of providers offer 'static file hosting' for free.

A suitable option for this kind of setup, which also allows this project to be as transparent as possible, is Github Pages.

## Setup
Github Pages allows for direct website deployment and hosting through the use of Github itself. Since this project is an organic 'something', it helps to have versioning at the same time. 

The setup is as follows:
* Store files and assets on a github repository
* On update (merge), generate a new version of the website (static assets) with Jekyll
* Deployment and hosting of static assets via Github Pages

### Configuration
As explained in the previous blog, a domain name needs to point towards a server that is able to handle the traffic. In this case we point an A-record to Github, as described [here](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#dns-records-for-your-custom-domain)

Configuring a Github repo to be used for Github Pages is really easy. You can enabled it from the repository settings as follows:

![Github-pages](/images/20231126/github-pages.png)

Now, everytime someone visits [Dikkeklok.nl](https://dikkeklok.nl) they will be pointed towards Github pages.

### Jekyll
As for Jekyll, the setup itself is pretty self explanatory. Jekyll uses three specific files/folders/formats:
* Config files
* Content (posts, assets)
* Layouts

When you're done writing content, the Jekyll generator will produce a static version of the site based on the layouts and set configuration. This can then pushed to Github to be displayed. More about Jekyll itself is explained [here](https://jekyllrb.com/docs/step-by-step/01-setup/)

### The Theme
The blog itself uses a standard theme called [So Simple](https://github.com/mmistakes/so-simple-theme). I did make some minor changes to the theme to support some of my wishes. This will be discussed in one of the following blog.

## Transparancy
One of the better things about using Github for hosting the website is that it comes with complete transparancy. All changes made to the website can be traced and reviewed. For example, if content is edited. Part of the watch industry is based on trust, and I feel like things such as pricing and description of items could use more transparency as well. This was also one of the reasons I went for a more public approach.

## In summary
The site is hosted on Github Pages. Every change of content can be viewed in the repository [https://github.com/Dikkeklok/dikkeklok-nl](https://github.com/Dikkeklok/dikkeklok-nl). If you have any suggestions of would even like to contribute, feel free to make a pull request.

For the next blog, I will try to dive into the changes I've made (such as the inclusion of analytics), and will gather the numbers to publish an update on click and visitors. _More soon..._

> _I've added an ['in progress'-folder on Github](https://github.com/Dikkeklok/roadtorolex-nl), this folder will contain some of the blogs that are in progress or that require some more thoughts_