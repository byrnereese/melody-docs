# Building Web Sites with Melody

Welcome to "Building Web Sites with Melody," a definitive guide for designers and developers on how to take a blank canvas and create within it a robust, powerful, feature rich community oriented web site. This guide is divided into three major sections, corresponding to and progressing roughly in accordance to the familiarity you will slowly build with the Melody Publishing Platform. They are:

* **Laying the Groundwork** - This section of the guide will help you become familiar with the fundamentals of blogging, the basics of Melody, and its templating language. At the end of this section you will have created a basic web site and a blog, complete with threaded comments, feeds, and navigation. You will also have become familiar with the basics of Melody's templating language.

* **Extending Your Web Site** - With a solid foundation having been established, thanks to "Laying the Groundwork," this section will instruct you on a number of features you can elect to add to your web site. This section includes such topics as adding "Digg This" buttons, comment feeds, advertising, related entries and much more.

* **Advanced Topics** - In the final section, we will explore features that make use of Javascript and some of Melody's more powerful features like multi-blog aggregation.

## Who is this Guide For?

This guide has content valuable to every Melody user. However, this guide was designed for users, freelance designers and consultants looking to familiarize themselves with the Melody platform. This guide begins with the assumption that you know very little about Melody, or its companion product Movable Type, and through a logical sequence of tutorials it aims to expand the reader's ability and confidence in their building web sites, blogs and social networks with Melody.

In order to use this guide properly however, we must make a few basic assumptions:

* You have successfully installed Melody.
* You understand the basics of HTML and CSS.
* You can work with or at least read Javascript.

TODO - FR: Open Source the Professional Web Site as it is the basis for this guide.

## Using this Guide

It is the goal of this guide to not only instruct you on how to build web sites with Melody, but also to produce a well designed web site in the process that you would be proud to use yourself. 

As a result some of the code samples we will discuss contain large amounts of HTML and Movable Type template tags. To make our samples clearer you may sometimes notice discrepancies between the large code samples we provide for you to cut and paste into Melody, and the excerpts from those code samples we use as a basis for dissection and discussion. These differences often come in the form of an abbreviation in some way, such as in lacking the *complete* HTML you may find in the full example. Our hope is that this will make it easier for us to more easily highlight the most important concepts to learn in any given section.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# Laying the Groundwork

## Building Your First Web Site and Blog

### Start from Scratch

Congratulations, you have decided to take the first step in becoming an expert in Movable Type. In what might be considered rites of initiation your first task is to create a blog in Movable Type, and then to **delete all of its templates**, thereby cleansing you of any preconceptions you have about Movable Type and how it works. When this process is complete, your system will consist exclusively of a raw publishing engine. And that's it, nothing more. Your system will then be ready for you to begin layering on one feature after another, and in so doing slowly build a strong foundation of knowledge in the Movable Type Publishing Platform.

Let's begin.

1. The first thing you need to do, after creating a blog, is navigate to its listing of templates: select "Templates" from the Design menu.

    <form mt:asset-id="1814" class="mt-enclosure mt-enclosure-image" style="display: inline;"><img alt="Select Templates from Design Menu" src="http://www.movabletype.org/documentation/2008/11/04/1%20-%20select%20design.jpg" width="471" height="232" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></form>

2. Next, select all of your Index Templates, and click the Delete button.

    <form mt:asset-id="1816" class="mt-enclosure mt-enclosure-image" style="display: inline;"><a href="http://www.movabletype.org/documentation/2008/11/04/2%20-%20select%20index.jpg"><img alt="Select All Index Templates" src="http://www.movabletype.org/documentation/assets_c/2008/11/2 - select index-thumb-500x195.jpg" width="500" height="195" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></a></form>

3. Then, do the same for your Archive Templates and Template modules. When you are complete, you should have no templates in your system, except for a small set of "System Templates."

    <form mt:asset-id="1820" class="mt-enclosure mt-enclosure-image" style="display: inline;"><a href="http://www.movabletype.org/documentation/2008/11/04/3%20-%20clean%20slate.jpg"><img alt="Clean Slate - no templates" src="http://www.movabletype.org/documentation/assets_c/2008/11/3 - clean slate-thumb-500x408.jpg" width="500" height="408" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></a></form>

Like a newly committed monk freed of his earthly possessions you must feel a great release from all your burdens. Or perhaps not, but at least you are now ready to officially begin your training.

#### Create a Homepage

So you want to create a web site? The good news is that you have already contracted a designer to design your web site and create its HTML. Right? Now it is your job to deploy this site and augment it with content.

The most critical component of any web site its its homepage, the page you reach when typing in the web site's URL. To create your homepage, or your "Main Index" as it is commonly called in Movable Type-land, you will need to create an Index template.

**Your Main Index**

An "Index Template" is a template that outputs a single file, with a filename you designate. You can publish HTML, PHP, ASP, JSP or any kind of page, in any kind of language you can imagine or wish for. The contents of the file can contain template tags that will be evaluated at the time the template is published.

In this example, your homepage will just contain static content and will *not* contain any template tags. This should show you how Movable Type can serve as a very light weight web site publishing tool.

Let's begin:

1. Select Templates from the Design Menu.

    <form mt:asset-id="1814" class="mt-enclosure mt-enclosure-image" style="display: inline;"><img alt="Select Templates from Design Menu" src="http://www.movabletype.org/documentation/2008/11/04/1%20-%20select%20design.jpg" width="471" height="232" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></form>

2. Click the "Create index template" link directly below the heading "Index Templates" near the top of the screen.

3. Enter in "Main Index" as the title for the template.

4. Cut and paste the HTML for your homepage into the body of the template.

    * Download Sample HTML (1 - main_index.txt)

5. Under "Template Options" enter in "index.html" (or "index.php" or "index.jsp" etc) as the output file. Select "main_index" as this template's type. Leave all the other options as-is.

6. Click Save, then "Save and Publish."

7. Finally, view your new web site.

A little underwhelming huh? Well, if you ever wondered what the Internet would look like without designers, this is it. 

<screenshot: 4 - plain site>

Now, let's see what we can do to make this a little prettier.

**Your Stylesheet**

To give your site a design you will next need to publish a stylesheet for your web site. A "stylesheet," written in a language called CSS (Cascading Style Sheets), is what gives a web site its unique layout and appearance. Every page on your web site, including the main index you just created, will reference this stylesheet, which browsers will then use to style and give your site some life.

1. Click "Create index template" from the template listing screen.

3. Enter in "Stylesheet" as the title for the template.

4. Cut and paste the CSS for your web site into the body of the template.

    * Download Sample CSS (2 - stylesheet.txt)

    *The sample stylesheet provided has a lot of additional style information defined within it, much of which will not be utilized until later in this guide. For now, let's just settle on understanding that it is from this template that the entire web site we will be building will derive its look and feel.*

5. Under "Template Options" enter in "styles.css" as the output file. Select "styles" as this template's type. Finally, select "Manually" from the Publishing menu -- this will instruct Movable Type to publish your stylesheet only when you specifically ask it to. This is helpful because your stylesheet is something whose content is not dynamic in any way, and setting its publishing setting to anything else will result in it being published and republished needlessly.

6. Click Save, then "Save and Publish."

Now that your stylesheet has been created you will need to associate it with your homepage. Let's do that now.

1. Go back to your template listing screen by clicking "Templates" in your Design menu.

2. Click "Main Index" under "Index Templates" to edit your homepage.

3. Near the top of your Main Index template, just after the `<head>` tag, add the following:

        <link rel="stylesheet" type="text/css" 
          href="<mt:Link template="styles">" />

    The `<mt:Link>` tag is a Movable Type template tag. It provides the very simple capability of generating a fully qualified URL to another template within the system. It is convenient because it keeps you from having to remember the template's output file. Just enter in the template's type into the `template` argument and Movable Type will do the rest.

4. Click "Save and Publish" and view your site.

Presto, your web site is no longer an eye sore.

**Adding Some Template Tags**

Right now your web site is completely static and will output the exact same text no matter how you configure Movable Type. This is less than ideal, so let's add some additional template tags that will allow you to:

* output the name and description of your blog
* output a more complete link back to your homepage

Our first task will be output your web sites name into the `<title>` tag and in the main banner for your site.

1. Edit your Main Index template.

2. Locate the text bounded by `<title>` and `</title>`, and replace it so that is appears as so:

        <title><mt:BlogName></title>

3. Locate the following text:

        <h1 id="header-name"><a href="index.html" accesskey="1">Your Web Site Name</a></h1>

    And replace "Your Web Site Name" so it appears as so:

        <h1 id="header-name"><a href="index.html" accesskey="1"><mt:BlogName></a></h1>

4. Now, let's replace "index.html" with a more adaptable equivalent by using a `<mt:Link>` tag like so:

        <h1 id="header-name"><a href="<mt:Link template="main_index">" accesskey="1"><mt:BlogName></a></h1>

5. Finally, let's output your web site's description in a similar manner. Look for the text:

        <h2 id="header-description">A description for your web site.</h2>

    And replace it with the following:

        <h2 id="header-description"><mt:BlogDescription></h2>

**Summary**

Congratulations, you have successfully created your web site. It is simple right now, just a homepage and a basic style, but you are well on your way. Now it is time to expand your web site with additional content and see how Melody can serve as an excellent web site content management tool.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# Extending Your Web Site

By now, you should be familiar with the very basics of Melody's templating, theme and design system. Plus, if you have been following along then you also have in place a very simple web site you have built using Melody. Although to say this web site is "simple" is an understatement because in truth all you have done is published a single page: the homepage. 

To some this may actually be more than sufficient, but in all likelihood this barely scratches the surface of what you have envisioned for your web site. 

In this section, we will begin to slow expand upon what you have already created through a series of simple to follow recipes. Each recipe will not only show you how to add a feature or two to your web site, they will also introduce you to an important concept that will aid you in some way for virtually any web site you may want to build.

Let's begin.

## Add an About Page to your Web Site

Suppose you need to add a page to your web site. This section will illustrate a number of different ways to do that using Melody. 

Topics taught in this section:

* The difference between an index template and a page.
* An introduction to archive mappings, specifically page archive mappings.
* How to modularize your web site to share common elements easily between multiple templates and pages.

### Index Templates and Page Templates

For those familiar with creating as index template to publish your web site's homepage, it will would be a relatively straight forward process to use an index template to also publish an about page for you web site. The process would go something like this:

1. Navigate to Templates from the Design Menu.
2. Click Create Index Template.
3. Enter in the name of and the HTML for your page in the spaces provided. 
4. Click Save and Publish.

There, you have a page. In fact, the steps above was at one point the most commonly used approach to pages for most Movable Type users. 

In Melody however, as in more recent versions of Movable Type, there is a far quicker and more flexible way to achieve the same result: Page Templates. 

A page template provides the designer and users with the following advantages:

* Designers can define the default look and feel, or "chrome" for every page on the web site. 

* Melody users do not have to be encumbered with having to know HTML, CSS or the Melody Templating Language. All they have to do is *enter the content for the page.*

To put it another way, **pages produced by page templates are nice because they are simple**. A user need only select the "Page" menu item from the Create menu and they can be publishing a new page for their web site in seconds. However, in their simplicity, they do lack certain capabilities index templates have. To help you better understand these differences and make a more informed decision with regards to what will be right for you, read the following differences carefully:

* The content entered for a page cannot contain any Melody template code and are thus relatively static. 

* Users are free to use a rich text, or WYSIWYG editor when creating pages. They cannot use such an editor when editing index templates.

* More?

Let's assume though that you have weighed your options and have decided that using a page template is best for you at this point. Let's learn how to add a page template to your web site now.

**Setting Up a Page Template**

Before you can create pages, your theme must first define a page template and an archive mapping for that template. Here is how you would do that:

1. Navigate to Templates from the Design Menu.
2. Under the Archive Templates table, click Create Archive Template: Page. 
3. Enter the information and HTML about your page template in the space provided. Click Save.
4. Once the page has been saved, expand the Template Options area just above the save buttons
5. Click "Create Archive Mapping" and select `folder-path/page-basename.html` from the Path pull-down menu.

With the page template and archive mapping in place, you can now publish pages to your web site with ease. 

### Diversion: An Introduction to Template Modules

Now that we have created at least two templates in your system, an index and archive template, you have almost certainly have duplicate blocks of HTML in your templates. The most common elements to be replicated across templates are the header and footer of your web site.

Technically there is nothing wrong with having template code replicated across multiple templates, but generally is considered non-ideal because it makes templates harder to manage and update.

Consider for example that you want to update your site's header in some way, perhaps by changing your site's logo or masthead. If the HTML for your header is replicated across multiple templates then you will have to make the necessary changes to your header as many times as there are templates for your web site. This can be time consuming, and potentially error prone. 

A better approach would be to share the HTML that is common between your templates in some way, which is why we have template modules. Template modules are nothing more than fragments of HTML and MTML that can be included or referenced by name from other templates. When used effectively, that means that if you needed to update your header, you would only need to edit the one relevant template module and you would be done.

Let's look at a simple example. Here is the MTML for a simple header of a web site. It is placed in a hypothetical template module called "Site Header":

    <div id="header">
      <h1><$mt:BlogName$></h1>
      <h2><$mt:BlogDescription$></h2>
    </div>

The header fragment can then be placed in each of your site's templates via the `<mt:include>` tag:

    <html>
      <head>
        <title><$mt:BlogName$></title>
      </head>
      <body>
        <$mt:include module="Site Header"$>
        <div id="content">
        </div>
      </body>
    </html>

Template modules also offer another key, but often under appreciated advantage: they make your templates much easier to read. When you use template modules you can effectively collapse large blocks of MTML into a single line. Consider for example the following Main Index template that is common for many blogs:

    <html>
      <head>
        <title><$mt:BlogName$></title>
        <$mt:include module="HTML Head"$>
      </head>
      <body>
        <$mt:include module="Banner Header"$>
        <div id="content">
          <mt:Entries lastn="auto">
            <$mt:include module="Entry Summary"$>
          </mt:Entries>
        </div>
        <$mt:include module="Banner Footer"$>
      </body>
    </html>

In this example you should hopefully see how template modules can dramatically improve the readability of your templates by dramatically reducing their complexity.

## Building Navigation for Your Web Site

With the introduction of pages to your web site, a new need emerges: giving your users the ability to easily find their way around the site. Perhaps the most common way web sites help users is this respect is with some form of global navigation that reflects the major destinations or content areas within a site. 

In the following example we will create the most basic form of web site navigation: a simple horizontal "nav bar" that lists all of the pages within your web site. To begin lets create a new template module called "Navigation." In the template body, enter the following:

    <ul id="nav">
      <li><a href="<$mt:BlogURL$>">Home</a></li>
      <mt:Pages>
      <li>
        <a href="<$mt:PagePermalink$>">
          <$mt:PageTitle$>
        </a>
      </li>
      </mt:Pages>
    </ul>

Then in your banner or site header module (assuming you have created one), include the new navigational system.

    <div id="header">
      <h1><$mt:BlogName$></h1>
      <h2><$mt:BlogDescription$></h2>
      <$mt:include module="Navigation"$>
    </div>

Once the navigation is in place, then it is just a matter of styling the markup to produce the desired visual. For a horizontal nav bar,  this is what that CSS might look like:

    ul#nav {
      clear: both;
    }
    ul#nav li {
      float: left;
    }

Ok, the CSS above is perhaps too simple, but the gist should be clear: stack each of your navigational elements in a list, then float them using CSS.

**Picking which Pages to Appear in the Site's Navigation**

The sample code above is perfect for a small web site with only a handful of pages. What happens though when you have possibly tens or even hundreds of pages? You can't possibly list them all in a single nav bar. That would be overwhelming to a site's visitors, but more importantly it would most likely be ugly. And we can't have *that*!

So when a web site has more pages than can be fit in a single nav bar, it becomes important for site owners to be able to specify which pages they want promoted there. To give administrators the control they are looking for we make use of  one of Melody's most useful features: the hidden tag. Before however we talk about hidden tags, let's make sure we know what a basic, run-of-the-mill tag is. 

Tags in many respects are nothing more than keywords that one can assign to a piece of content. Except tags, unlike keywords, are usually published and made visible to readers. Tags are also often hyperlinked allowing readers to click on the keyword or tag to find other content that has also been tagged with the same word or phrase. 

Hidden tags therefore are a special kind of tag that can only be seen and edited from within the Melody administrative interface. They are never made visible to the public. They therefore provide designers with a convenient mechanism by which to filter content in the site by some arbitrary token.

In Melody a hidden tag is denoted by prepending the "@" sign to the tag in question.

Let's apply this concept to a site's navigation to illustrate. Suppose your website has over a hundred pages, but your site's horizontal nav bar only has room for five of those pages (give or take). To quickly give your users the ability to select which five pages they want to appear across the top of their site's banner, we use the hidden tag `@topnav` to filter our list of pages:

    <ul id="nav">
      <li><a href="<$mt:BlogURL$>">Home</a></li>
      <mt:Pages tag="@topnav">
      <li>
        <a href="<$mt:PagePermalink$>">
          <$mt:PageTitle$>
        </a>
      </li>
      </mt:Pages>
    </ul> 

Once in place, you can instruct users to select which pages they want to appear in the navigation by editing each of the pages in question and adding the `@topnav` tag to the list of tags associated with the page. Then republish your site and presto, your new nav will appear.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
UNFINISHED BELOW THIS POINT


### Adding a Blog to your Site

* Blog Index template
* Entry Template
* Entry Listing Template
* Adding Javascript

### Adding a Feed to your Blog

* RSS vs Atom
* Atom Template
* Adding a <link rel="alternate"> tag

### Adding Widgets to Your Blog

* WidgetManager
* Widget Templates
* <mt:WidgetSet>

### Adding Search to Your Site

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Extending Your Web Site

### Adding a Comment Feed to your Blog

* About comment feeds
  * Atom
  * <in-reply-to>
  * <link rel="replies">
* Site-wide comment feed
* Per-Entry comment feed

### Adding Advertising to your Site

* AdSense and Others
* Creating ad widgets
* Show ads only to people coming from search

### Adding a Print Stylesheet for your Site
### Adding Digg Buttons and ShareThis
### Adding Related Entries 
### Displaying a List of Nested Categories
### Inserting a Javascript Gallery of Photos
### Switch to Nested Comments to Your Blog
### Adding Action Streams to Your Blog
### Sticky Posts
### Creating Featured Posts
### Adding Google Analytics to Your Site
### Adding Feedburner to Your Site
### Creating a Slideshow of Featured Content
### Featuring Comments
### Allowing Readers to Subscribe to New Comments
### Building Drop Down Menus from Categories
### Aggregating Content from Other Blogs
### Adding Author Archives
### Displaying a List of Authors for Your Site

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Advanced Topics
### IncludeBlock
### Adding a Map to Your Blog
### Collating Actions and Posts
### Adding a Podcast to your Site
### Pagination?
### Inserting YouTube Videos on your Blog
### AJAX Commenting
### Setting up Multible Blogs

#### Aggregating Content Between Blogs

* blog_ids

#### Keeping Content Fresh 

* MultiBlog
* MultiBlog 2.1 beta

#### Global Template Modules
#### Creating a Product Catalog
#### Building a Portfolio Web Site
#### Adding Press Releases to your Web Site

