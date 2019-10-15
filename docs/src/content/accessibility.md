---
title: "Accessibility"
date: "2017-10-03"
draft: false
path: "/docs/accessibility"
---
<div class="section-wrap">

<div class="section top">

## Access For All

What if your site worked in all of the United States but not the state of New York? There are more persons with disabilities in the country that the population of New York. If your website is not built for people with debilities in mind, you are missing a large minority of your customer base. Also, according to U.S. law these days, not building for disabled persons can be punished in the courts by fines if a person decides to sue your company.

Thankfully, the architecture of the web and web site standards are built with accessibility in mind. As long as web pages stick to being mostly a structured content document, there’s very little that needs to be done to accommodate for persons with disabilities. But when complex functionality such as navigation menus, interactive media or other non-content is included, more has to be done to ensure that persons with disabilities can access the data.

The responsibility of keeping content well-structured and accessible extends not just to our development team but to the content managers of the site. While we work to make the site as accessible as possible at launch and have the administration tools reinforce best practices, content administrators can make the site less accessible through changes to the content’s HTML code.

## What We Do

The overwhelming majority of our sites include a custom design and some custom functionality not included with the platform. When designing your look and customizing your platform to meet your needs, we keep accessibility in the forefront of the following areas.

### Design

Contrast is important for readability and even more important for those who cannot see that well. We do check during the process of selecting the colors and layout that text and elements have sufficient contrast to be noticed by all sighted users. One tool we use is a [Sketch Contrast Plugin](https://github.com/getflourish/Sketch-Color-Contrast-Analyser).

In a similar way, our designs should be perceptive for users with colorblindness. Color should not be the only way to convey information and major design elements should be checked for compatibility for colorblindness. A tool for this is [Color Oracle](http://colororacle.org/), which filter's your OS's colors to simulate what colorblind users see.

Text size is important. The majority of the text should be an equivalent of 16 point, although it depends on the visitor's display settings a lot. Also, font sizes should be resizable in browsers by the user as needed.

With the advent of touch-based devices, it is more and more important that click/touch areas are big enough to be activated easily. Buttons and links should be pretty big. For teaser articles, maybe make the whole teaser click-able.

Collapsible menus can be complicated as the heading may link to a page as well as vistors want to see the sub-items. We make sure the action of each is clear or force one action for the main item and add another way to access the other.

For visitors using screen readers and browsing the page's links, links such as "Click Here" or "Read More" provide very little information of what the link goes to. Instead, we recommend that the title of the item be click-able and/or ARIA markup included to give hints.

Finally, forms can be a big concern for accessibility. As it is an important part of your site that collects visitor information and the visitors have to be able to input data, it must be usable by all visitors. We work to make sure that common patterns for navigating forms are followed and forms are labeled correctly and accept expected values. For more information, see [our blog post on accessible forms](https://www.augustash.com/our-blog/best-practices-designing-web-forms).

### Content Management/Code Output

For blind users and search engines, it is helpful to make sure that images are described so they can get an idea of the visual information given. To that end, for every image uploaded, we expect all images uploaded to include a description and, in most cases, that description will be printed as the image's "ALT" text. In some cases, the image may be used as just an abstract background, in which case an ALT tag may not be needed as the image really just sets a color or palette and not actually conveys information.

To promote clear content and allow for easy browsing of content, pages should have a hierarchical groups of headings with lists, paragraphs, quotes, etc. In the content editing interface, we provide administrators tools to set these and discourage them from using non-standard fonts and colors by not giving them tools for adding other non-standard markup.

Although JavaScript is a great tool to make websites interactive and more user-friendly, some users may want to navigate the site with JavaScript disabled. If for some reason JavaScript is required, a friendly message should be shown when JavaScript disabled.

Blind users or users without a mouse often use their keyboard to navigate through the page hierarchy and/or the links on the page. To facilitate that, our themes often include a "Skip to Main Content" link at the top that skips to the start of the main content and skips the header and navigation. When selecting next/previous items via the keyboard, the focus should be visible for sighted users and there must be something for screen readers to output. Also, navigating via the keyboard should not get "hung up" in a situation where it cannot go further forward or backward.

Before launching the site, we will run a number of common pages through the [WebAIM WAVE tool](http://wave.webaim.org/) to try to identify outstanding accessibility issues. However, tests like this do not catch all issues a visitor may have and does not guarantee accessibility.

## What Drupal Gives Us

### Content Management/Code Output

Drupal's administration interface uses proper ARIA properties for complex UI navigation and is tested for accessibility before most changes are made. Drupal's many framework APIs also are accessibility-friendly and, if implemented correctly, should make our custom code accessible as well. Starting October 2017, Drupal 8.4.0+ includes an "Inline Form Errors" module that displays errors on a form right next to the field instead of printing all the errors in the message area at the top of the page, which can be helpful for users of all types to easily identify and resolve form errors.


## Resources for Developers

*   [Accessibility (A11y) Style Guide](http://a11y-style-guide.com/style-guide/)
*   [Tota11y Plugin](http://engineering.khanacademy.org/posts/tota11y.htm)
*   [Wave web tester and plugin](http://wave.webaim.org/)
*   [Devel A11y Drupal module](https://www.drupal.org/project/devel_a11y)
