# Building Web Sites with Movable Type

Welcome to "Building Web Sites with Movable Type," a definitive guide for designers and developers on how to take a blank canvas and create within it a robust, powerful, feature rich community oriented web site. This guide is divided into four major sections, corresponding to and progressing roughly in accordance to the familiarity you will slowly build with the Movable Type Publishing Platform. They are:

* **Laying the Groundwork** - This section of the guide will help you become familiar with the fundamentals of blogging, the basics of Movable Type, and its templating language. At the end of this section you will have created a basic web site and a blog, complete with threaded comments, feeds, and navigation.

* **Extending Your Web Site** - With a solid foundation having been established, thanks to "Laying the Groundwork," this section will instruct you on a number of features you can elect to add to your web site. This section includes such topics as adding "Digg This" buttons, comment feeds, advertising, related entries and much more.

* **Adding Community Features** - In this section we will dive deeper into Movable Type Pro, and the features that can really help you to differentiate your site from all the others. We will discuss adding profiles to your site, customizing login screens, accepting user generated content and more.

* **Advanced Topics** - In the final section, we will explore features that make use of Javascript and some of Movable Type's more powerful features like multi-blog aggregation.

## Who is this Guide For?

This guide has content valuable to every Movable Type user. However, this guide was designed for users, freelance designers and consultants looking to familiarize themselves with the Movable Type Publishing Platform. This guide begins with the assumption that you know very little about Movable Type and through a logical sequence of tutorials it aims to expand the reader's ability and confidence in their building web sites, blogs and social networks with Movable Type.

In order to use this guide properly however, we must make a few basic assumptions:

* You have successfully installed Movable Type.
* You understand the basics of HTML and CSS.
* You can work with or at least read Javascript.

TODO - FR: Open Source the Professional Web Site as it is the basis for this guide.

## Using this Guide

It is the goal of this guide to not only instruct you on how to build web sites with Movable Type, but also to produce a well designed web site in the process that you would be proud to use yourself. 

As a result some of the code samples we will discuss contain large amounts of HTML and Movable Type template tags. To make our samples clearer you may sometimes notice discrepancies between the large code samples we provide for you to cut and paste into Movable Type, and the excerpts from those code samples we use as a basis for dissection and discussion. These differences often come in the form of an abbreviation in some way, such as in lacking the *complete* HTML you may find in the full example. Our hope is that this will make it easier for us to more easily highlight the most important concepts to learn in any given section.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Laying the Groundwork: Building Your First Web Site and Blog

## Step 1. Start from Scratch

Congratulations, you have decided to take the first step in becoming an expert in Movable Type. In what might be considered rites of initiation your first task is to create a blog in Movable Type, and then to **delete all of its templates**, thereby cleansing you of any preconceptions you have about Movable Type and how it works. When this process is complete, your system will consist exclusively of a raw publishing engine. And that's it, nothing more. Your system will then be ready for you to begin layering on one feature after another, and in so doing slowly build a strong foundation of knowledge in the Movable Type Publishing Platform.

Let's begin.

1. The first thing you need to do, after creating a blog, is navigate to its listing of templates: select "Templates" from the Design menu.

    <form mt:asset-id="1814" class="mt-enclosure mt-enclosure-image" style="display: inline;"><img alt="Select Templates from Design Menu" src="http://www.movabletype.org/documentation/2008/11/04/1%20-%20select%20design.jpg" width="471" height="232" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></form>

2. Next, select all of your Index Templates, and click the Delete button.

    <form mt:asset-id="1816" class="mt-enclosure mt-enclosure-image" style="display: inline;"><a href="http://www.movabletype.org/documentation/2008/11/04/2%20-%20select%20index.jpg"><img alt="Select All Index Templates" src="http://www.movabletype.org/documentation/assets_c/2008/11/2 - select index-thumb-500x195.jpg" width="500" height="195" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></a></form>

3. Then, do the same for your Archive Templates and Template modules. When you are complete, you should have no templates in your system, except for a small set of "System Templates."

    <form mt:asset-id="1820" class="mt-enclosure mt-enclosure-image" style="display: inline;"><a href="http://www.movabletype.org/documentation/2008/11/04/3%20-%20clean%20slate.jpg"><img alt="Clean Slate - no templates" src="http://www.movabletype.org/documentation/assets_c/2008/11/3 - clean slate-thumb-500x408.jpg" width="500" height="408" class="mt-image-center" style="text-align: center; display: block; margin: 0 auto 20px;" /></a></form>

Like a newly committed monk freed of his earthly possessions you must feel a great release from all your burdens. Or perhaps not, but at least you are now ready to officially begin your training.

### Create a Homepage

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

*TODO - log FR: enable Save and Publish on initial template creation*

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

Congratulations, you have successfully created your web site. It is simple right now, just a homepage and a basic style, but you are well on your way. Now it is time to expand your web site with additional content and see how Movable Type can serve as an excellent web site content management tool.

### Template Tag Primer

Let's take a break from web site building for a second and lay some important groundwork. 

A key component to the Movable Type publishing platform is its templating language.

**Basic Syntax**

**Arguments**

**Modifiers**

#### Function Tags

#### Container Tags And Loops

**Common Arguments**

**Meta Loop Variables**

#### Variables

**Setting Variables**

**Reading Variables**

**Variable Interpolation**

#### Conditional Tags

**if/else**

**if/else if/else**

**unless**

### Create an About Page

* You could: create another index template
* Page Templates
* Page Archive Mapping
* Header/Footer Module
  * <mt:include>
  * <mt:includeblock>

### Building Navigation for Your Site

* Navigation Module
* Horizontal Navigation
* <mt:Pages>
* Using tags to control menu, e.g. @nav

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

### Adding Userpics to Your Comments

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

## Adding Community Features
### Creating User Profiles
### Defining Custom User Profile Fields
### Customizing the Edit Profile Form
### Accepting User Generating Content
### Adding a List of Recent Members
### Adding a Sign-in/Sign-out Link
### User Blogs

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Advanced Topics
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

