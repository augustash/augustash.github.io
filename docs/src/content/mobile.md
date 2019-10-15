---
title: "Mobile"
date: "2014-05-23"
draft: false
path: "/docs/mobile"
---

## Mobile First Approach

Mobile device usage is growing by the day. This means that every site needs to adapt to different screen sizes to offer the best possible experience for the end user. In order to do this we need to think mobile first. By building from the inside out, it allows us to create a linear workflow. As devices get bigger, our styles need to adapt.

At AAI, all upcoming projects should have mobile first in mind. Because we should (and will) put so much emphasis on mobile devices at the beginning of projects we need to change how are process is handled.

## Design & Build Process

After we have our initial meeting(s) with our new client we're ready to start digging into the design and build of the project. In order to get the creativity juices flowing early we engage with the client first with the [style tile](http://styletil.es/). A style tile is a stripped down palette of colors, fonts and imagery that support the end goal of the finished project. What's really great about style tiles is that they're simple enough that one could quickly iterate new styles based on client feedback without having to change a number of full concept work. This approach allows the designer to gain better perspective on the overall look and feel that the client prefers.

Prototyping follows soon after. Honestly, it is not directly tied to the result of a style tile so it can start once there is time in the schedule. Prototyping has really taken the place of static wireframes. It does a much better job of showing the user flow and allows for actual interaction with the site. Prototypes are also scalable. Clients can test on their phones, tablets and desktop computers. This approach also allows for us to get the site in front of clients quicker. If they have changes, we can make them in the prototype and deliver the feature in the next iteration.

After the client has agreed upon a style tile version we're ready to implement these elements into a design concept. We typically create a homepage, standard content page and any other feature rich pages. This all depends on the size and complexity of the project. For instance, if we were building a staffing site we might create a (homepage, standard page, staff listing and detail page).


Once the design concepts are approved we can start to implement the look and feel on top of the built prototype. Remember, with the mobile first approach we're building from the inside out. Start with the mobile size devices and build up to the desktop.

## The Framework

In order to get the most out of modern day browsers, we have choosen to build with the [Foundation 5](http://foundation.zurb.com/) framework for all projects. It gives us tremendous flexibility in responsive prototyping, customization and scalability. The community of developers behind Foundation is continually growing and improving upon the framework. Unlike other popular frameworks, Foundation keeps it's code base clean and lean. They purposely left their styles spares so themers didn't have to strip away or override baked in code. Rather, they built Foundation to be a starting point.

### IE8 Needs Some Help

The last of the legacy browsers. Foundation 5 doesn't play nice with IE8, and honestly [why should it](http://thebeatofsports.com/wp-content/uploads/2012/11/turrible.jpg)? With that said, we have to remedy this with some JavaScript polyfills. Simply include the following libraries in the footer of the page and IE8 will start displaying content properly.

    <!--[if lt IE 9]>
      <script type="text/javascript" src="//s3.amazonaws.com/nwapi/nwmatcher/nwmatcher-1.2.5-min.js"></script>
    <![endif]-->

    <!--[if lt IE 9]>
      <script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/selectivizr/1.0.2/selectivizr-min.js"></script>
    <![endif]-->

    <!--[if lt IE 9]>
      <script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/respond.js/1.1.0/respond.min.js"></script>
    <![endif]-->

    <!--[if lt IE 9]>
      <script type="text/javascript" src="/local/path/rem.min.js"></script>
    <![endif]-->

Soon [IE8 will be extinct](http://www.microsoft.com/en-us/windows/enterprise/end-of-support.aspx). When that day comes we can stop implementing the above code to each site.

## Getting Sassy

[Sass is a preprocessor](http://sass-lang.com/) that allows themers to quickly and effectively create complex css styles. It adds features such as variables, nested selectors, browser prefixes and loops. By taking a lot of the heavy lifting off of the themer, it allows for faster prototypes and overall quicker builds. Because Foundation is built using Sass, this gives us the ability to easily customize the framework without having to override styles.

Sass also works great within our mobile first workflow. Here's an example.

    // Change the background color as the device gets bigger

    .foo {
      background-color: red;

      @media #{$medium-up} {
        background-color: blue;
      }

      @media #{$large-up} {
        background: green;
      }
    }

Because Sass gives us the power to nest selector and media queries, we can easily update styles as devices get bigger. Foundation provides some handy variables as well. Including `$medium-up` only triggers when the device breakpoint exceeds the medium min width. `$small-only` triggers only for devices within the small width range.

Because there are so many advanced features that Sass offer us, people have started to create libraries to use as a starting framework. Two very popular libraries are Compass and Bourbon.

Compass is really the original mixin library. It's been around nearly as long as Sass itself. It's a powerful tool and provides a couple of very useful features. First off, it has a ton of mixins to speed up your theming. Over the past few years they have been growing this list as new requests come in. The other feature Compass has to offer is compiling Sass. By creating a local config.rb file and running `compass watch`, Compass takes a lot of the heavy lifting off of your hands.

### <span class="cross">[Compass Mixin Library](http://compass-style.org/)</span> <span class="sub">(for now)</span>

Though Compass is powerful, here at AAI we do plan to move away from it. The biggest reason is that the mixin libraries are getting bloated and a lot of styles aren't needed in our workflow. Also, the compiler is slow in comparison to the lean libsass approach.

### [Bourbon Mixin Library](http://bourbon.io/)

Bourbon is a lightweight mixin library created by Thoughtbot. Like Compass, they have taken the time to create extremely helpful snippets to help speed up theming. Bourbon also does a better job at depreciating old mixins as browser standards change.

### [libsass Compiler](http://libsass.org/)

Libsass is a C/C++ port of the Sass engine. The point is to be simple, fast, and easy to integrate. Because it's so fast, we use it to compile our Sass files. [Foundation docs](http://foundation.zurb.com/docs/sass.html) has some simple step by step instructions to help install Foundation with libsass.

_(Scalable & Modular Architecture for CSS)_ is more style guide than rigid framework. There is no library within here for you to download or install. SMACSS is a way to examine your design process and as a way to fit those rigid frameworks into a flexible thought process. It is an attempt to document a consistent approach to site development when using CSS (or in our case, Sass).

By creating organization through separation, we can create easier to manage stylesheets. Because SMACSS is framework-agnostic, we can utilize this structure in Drupal, Magento, Wordpress or any other custom framework.

Our structure consists of three categories:

### libraries

This contains all variables, mixing and placeholders. It can also be used to store vendor styles.

### components

This contains elements within the site. Sidebar blocks, header, footer, callouts, etc.

### sections

This category is for bigger chunks. If you were building an e-commerce site you might have sections like product list, product detail, checkout, etc.

## CMS Themes

The goal is to use Foundation across all projects. This will help in situations where one developer works on a project initially and then hands it off to another. That developer should then be able to quickly get up to speed knowing that the project was built using Foundation.

The problem that we have is we aren't a one CMS shop. We built sites in Drupal, Magento, Ruby and occasionally Wordpress. We need themes that are all built on top of Foundation.

### [Fett <span class="sub">Drupal</span>](https://github.com/JaceRider/Fett)

Fett is a base theme for Drupal built and heavily integrated with Foundation. All Drupal 7 projects are required to use this theme. The following sub-modules are dependencies for Fett.

*   [Sonar](https://github.com/JaceRider/Sonar) _Sass compiler_
*   [Fawesome](https://github.com/JaceRider/Fawesome) _Font icons_
*   [jQuery Update](https://drupal.org/project/jquery_update) _7.x-2.x-dev_

### [Yeti <span class="sub">Magento CE</span>](https://github.com/augustash/yeti)

Yeti is a Magento Community theme built on Foundation. It includes overriding templates, styles and menu configuration to better integrate with the framework. It also is setup to use [Bower](http://bower.io/) for easy component upgrading. Installation and setup instructions are included in the Github Readme. The following extensions are dependencies for Yeti.

*   [Ash Core](https://github.com/augustash/ash_core)
*   [Ash jQuery](https://github.com/augustash/ash_jquery)
*   [Ash Font Awesome](https://github.com/augustash/ash_fontawesome)
*   JakeSharp Menu _(included in theme)_

Being this theme is still in "WIP" form, it's not required for all Magento Community projects. The goal is to get this ready as soon as possible so that it can in the near future.

### [Foundationpress <span class="sub">WP</span>](https://github.com/olefredrik/foundationpress)

Because we don't develop in Wordpress regularly, we can look to the WP community for a starting base theme. Foundationpress is a simple, stripped down theme built on Foundation.

## Browser Support

To ensure our client's sites are accessibly to their audience, we need to identify which browsers to target. Browser statistics can vary from project to project, but we still need a base set of browsers to check regardless. Based on [StatCounter.com](http://gs.statcounter.com/#browser-US-monthly-201303-201403) these are the most popular browsers used in the United States to date.

### Firefox

As an open source project, Firefox's mission is to promote openness, innovation & opportunity on the web. Because of this, it's one of the preferred browsers on the web today. It's heavily used on Mac and Windows, so we need to ensure our sites work on both operating systems.

### Google Chrome

Chrome is quickly becoming one of the most popular browsers out there. Similar to Firefox, developers over at Google are pushing the envelope in innovation on the web. Rapid development and releases keep this browser up to date with the latest technology. It's heavily used on Mac and Windows. We need to ensure our sites work on both operating systems.

### Safari <span class="sub">6+</span>

Safari is the default browser installed on all Macs. Though it can be installed on Windows, it's most popular among Mac users. Based on W3 Schools statistics, versions 6 and up are most commonly used now a days. These are the versions that we need to support and test in.

### Internet Explorer <span class="sub">8+</span>

Internet Explorer is the default browser installed on Windows machines. Because of this and the fact that companies often lockdown browser usage to only IE makes this a browser we can't ignore.

## Device Support

Along with browser support we need to be sure we test in today's most popular devices. This includes Apple's iOS, Android and in some situations Windows Mobile.

### iOS <span class="sub">5+</span>

iOS usages is growing everyday, and we need to ensure that our sites can keep up. With mobile first approach in mind, we need to start testing in iOS early in the development process. Ideally we'd want to test on actual devices, but since that can't be the case for everything we can use Apple's [Xcode iOS Simulator](https://developer.apple.com/devcenter/ios/index.action).

### Android <span class="sub">2.3+</span>

Android is another very popular OS and is growing rapidly in the US. Just like iOS, we'll want to test Android devices early and often in development. BrowserStack offers a ton of Android versions to test in.


### Windows Mobile <span class="sub">7+</span>

The only reason that Windows Mobile is on this list is that we have run into situations in the past where the client uses it as their primary work and personal phone. To test Windows Mobile you can install the "PC only" [SDK emulator](http://dev.windowsphone.com/en-us/downloadsdk).

## Browser Testing

Browser testing is a vital step in producing a site that can be accessible to a wide range of audience. We need to ensure that we test in all of the browsers and devices mentioned above. Here are a couple of tools that can help with this.

<div class="asset">![BrowserStack](images/browserstack.png)</div>

[BrowserStack](http://browserstack.com/) is the most efficient way to test cross-browser. Real virtual machines that you can run and test right in your browser, including localhost. Each browser come pre-loaded with all the development tools you would need. For instance, open up IE 8 and you'll get Firebug Lite, the IE developer tools, and Companion.js.

<div class="asset">![Modern.IE](images/modern-ie.png)</div>

[modern.IE](http://www.modern.ie/) offers a ton of useful resources for testing sites. From browser snapshots, compatibility reports and virtual machine testing. Similar to BrowserStack, modern.ie gives you access to test on an actual copy of IE8\. Either in XP or Windows 7\. There are several ways to install the virtual machines, but the preferred method is to use [VirtualBox](https://www.virtualbox.org/). After you have this installed you can simply grab the IE.x curl command found on the modern.ie site and run it in your terminal window. This will download all of the box files you'll need. From here you can follow the "Getting started with VMs: Instructions" and you're ready to go!
