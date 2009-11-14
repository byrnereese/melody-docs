# Creating a Theme in Melody

This reference manual is intended for designers who are already familiar with the basics of the Melody Templating language, and with how to go about building and assembling a web site using Melody. This manual's intent is to serve as a reference guide to all of the various options available to design within a theme's configuration file, a.k.a. config.yaml.

## What is a Theme?

A theme in Melody, historically known as a "template set," is a collection of templates that when used together define the look and feel, as well as the behavior of a web site. 

## Packaging a Theme

In Melody a theme is a type of plugin that defines one or more sets of templates that a user can later apply to their blog or web site quickly and easily. As with plugins, the heart of every theme in Melody is a configuration file, named `config.yaml`, which defines all of a theme's various characteristics, including a list of all the templates the theme contains and utilizes. In addition, this configuration file is responsible for defining:

* Any configuration options associated with a theme.
* Any blog settings and/or preferences that a theme relies upon to operate properly. 

In addition to this configuration file, and the templates a theme utilizes, a theme must also contain all of the javascript, CSS, images and other static files needed by your web site. 

With this in mind, you can therefore think of a theme being broken into two groups of files: program files (which includes your config file, your templates, and any other library or "code" your theme relies on) and static files. For organizational purposes and a variety of esoteric technical reasons these files are keep separate from one another; program files are placed in the `plugins` directory and static files placed in the `mt-static` directory. Let's take a look at a hypothetical theme exactly as it would appear following your downloading and unzipping it onto your desktop:


    MyTheme-1.0/
        mt-static/
            plugins/
                MyTheme/
                    files...
        plugins/
            MyTheme/
                config.yaml
                templates/
                    theme1/
                        files...
                    theme2/
                        files...

The structure mentioned above should be immediately apparent. At the top of the directory tree in the example above is a folder called `MyTheme-1.0`, which typically bears the theme's name and its version number. This is the one folder that is created after unzipping your newly downloaded theme and it contains **all of the files** needed by the theme. Now, within this folder are two other sets of folders. They are:

* `plugins/MyTheme/`
* `mt-static/plugins/MyTheme/`

You can see that both your theme's program files and static files are grouped together into a folder bearing the same name, which in this case is "MyTheme." This convention is used in order to prevent the files from one theme from overwriting or colliding with files from another theme or plugin once it is installed. 

### Creating a Theme from Scratch

To illustrate how one would begin with the process of creating a theme, let's walk through a sequence of commands that will stub out the basic structure of a plugin. 

1. Let's set the current working directory to our home directory:

        prompt> cd ~

2. Now, create the base directory for your theme and then make it your current working directory.

        prompt> mkdir MySuperTheme
        prompt> cd MySuperTheme

3. Create the paths you will need for theme's program files and templates.

        prompt> mkdir plugins
        prompt> mkdir plugins/MySuperTheme
        prompt> mkdir plugins/MySuperTheme/templates

    **Tip: As a short-hand one can use the `mkdir -p` command to recursively create a set of directories if they don't exist.**

4. Create the paths you will need for the theme's static files:

        prompt> mkdir -p mt-static/plugins/MySuperTheme/

5. Create some of the key files your theme will almost certainly rely upon:

        prompt> touch mt-static/plugins/MySuperTheme/styles.css
        prompt> touch plugins/MySuperTheme/config.yaml
        prompt> touch plugins/MySuperTheme/templates/main_index.mtml

    **Tip: The `touch` command in Unix systems simply creates an empty file using the designated file name.**

6. Give your main index template some content to display. Let us also reference within it the CSS stylesheet you created so that you can properly style your theme's homepage. Edit `main_index.mtml` in your templates directory and enter this content:

        <html>
        <head>
          <title><$mt:BlogName$> - Hello World</title>
          <link rel="stylesheet" type="text/css" 
             href="<$mt:StaticWebPath$>plugins/MySuperTheme/styles.css" />
        </head>
        <body>
          <p>Hello World.</p>
        </body>
        </html>

7. Next, let's create the plugin's configuration file which effectively registers the theme we are creating with Melody, and populate it with the very minimal amount of information. Edit your `config.yaml` and then cut and paste this into it:

        id: MySuperTheme
        name: "My Super Theme"
        description: "A demo theme from the documentation."
        author_name: Byrne Reese
        author_link: http://www.majordojo.com/
        version: 1.0

    The above defines the very basics for your plugin. 

8. Finally, let's register and associate the main index template you created above within your theme's configuration file. This final step is what will give users the ability to select and apply your theme to their web site or blog. Edit your `config.yaml` file again, and cut and paste the following at the end of that file:

        template_sets:
          my_super_theme:
            label: "Blog Theme (My Super Theme)"
            base_path: templates
            templates:
              index:
                main_index:
                  label: "Main Index"

The code above registers a theme with Melody called "Blog Theme (My Super Theme)" with an theme ID of `my_super_theme`. This theme ID must be unique within a user's installation. No other theme can bear the same ID. 

The code above also points Melody to the path on the file system where it can find all of the templates associated with this theme. The path specified is relative to the directory containing the `config.yaml` file. 

Finally, the code above associates a single template with the theme called "Main Index." The template is an "index" template and has an ID of `main_index`. The template's ID also happens to correspond to the file name of the template where Melody will find the template code for this template. Alternatively the file name can be stated explicitly like so:

    templates:
      index:
        main_index:
          label: "Main Index"
          filename: "homepage.mtml"

Therefore the path to a template can be determined one of two ways:

* Derived: `<base_path>`/`<template id>`.mtml
* Explicit: `<base_path>`/`<filename>`

And there you have it - your very first theme. Now all you have to do is check it into source control (*ahem*, github, *cough*), and install it into your Melody install.

Once it is installed, then you can apply your theme/template set to any new or existing blog. In that process Melody will read your configuration file, install all relevant templates, setup your theme options and more. 

## Where You Go From Here

Now that we know how to create a basic theme in Melody, the rest of this manual will make a whole lot more sense. What we will discuss below are all of the various options available to you in your theme's configuration file.  

# Reference

## Using this Guide

Each section below details an aspect of a theme's configuration file. For each element documented, the parent element is identified along with all of the element's properties. Properties, or child elements, that are not a simple name/value pair (e.g. "label: My Theme") are denoted by the text *"complex type"*. All complex types are documented in more detail elsewhere in this document. 

## Basic Theme Metadata

* Element name: *theme ID*
* Parent Element: `template_sets`
* Properties:
  * `base_path` - The path, relative to the directory where the theme's `config.yaml` file is located, where this themes templates can be found.
  * `label` - The name of the theme as it will appear to the user inside the Melody CMS.
  * `options` - A collection of all the options related to this theme. *complex type*
  * `order` - The sort order of the theme relative to other themes in the install. It is recommended to leave this blank.
  * `templates` - A listing of all the templates belonging to this theme. *complex type*

**Example**

    template_sets:
      theme_id:
        label: 'My Theme'
        base_path: templates/theme_id
        order: 101

## Templates

Contained by the `templates` key in a theme's configuration file are all of the various templates associated with the current theme. Each template defined here registers its name, archive mappings (if they apply) and publishing options.

* Element name: `templates`
* Parent Element: *theme ID*
* Properties:
  * `index` - A list of all of the index templates in this theme. *complex type*
  * `individual` - A list of all of the individual archive templates and their mappings in this theme. *complex type*
  * `module` - A list of all of the template modules associated with this theme. *complex type*
  * `system` - A list of all of the system templates associated with this theme. *complex type*
  * `widget` - A list of all of the widgets associated with this theme. *complex type*
  * `widgetset` - A list of all of the widget sets associated with this theme. *complex type*

**Example**

    templates:
      templates:
        index:
          main_index:
            label: "Main Index"
        module:
          header:
            label: "Blog Header"
          footer:
            label: "Blog Footer"


### Index Templates

Index templates within Melody correspond to those templates that output a single file. Examples of index templates are:

* Your site's homepage
* An RSS or Atom feed
* A Google Sitemap
* An archive listing
* and more of course. 

An index template has the following properties:

* Element name: *template ID*
* Parent Element: `index`
* Properties:
  * `label` - The display name of the template.
  * `outfile` - The filename to which this template will output its contents. The filename can also include path information relative to the current blog's site path. 
  * `rebuild_me` - A boolean value (1 or 0) indicating whether a template should be rebuilt when a new comment or entry is created. *Obsolete: please use `build_type` instead.*
  * `build_type` - An integer identifying when and how a template should be published. See "Build Types" below.

**Build Types**

A build type designates how and under what conditions a template will be published. The value assigned to the `build_type` property is a simple integer. Below is a list of allowable values and their associated meaning.

* **0** - Disabled. Do not publish this template ever.
* **1** - On demand. Publish this template whenever a new entry or comment is created.
* **2** - Manually (default). Publish this template only when an admin requests it to be republished from within the Melody CMS.
* **3** - Dynamically. Publish this template in real time whenever it is requested by a reader. 
* **4** - Via Publish Queue. Publish this template whenever a new entry or comment is created, but publish it via the "publish queue," a background process to which publishing can be strategically off-loaded.

**Example**

    templates:
      index:
        sitemap:
          label: 'Google Sitemap'
          outfile: 'sitemap.xml'
          build_type: 2

## Archives Templates

Archives provide your visitors with a number of ways to exploring, browsing and discovering new content. Archives are used to group content you have created by a variety of criteria, such as the category they were published in, or the date they were authored, or even a mix of the two (e.g. "show me all of the entries in the 'News' category written in November 2008"). 

Archives are also used to publish the dedicated page for each entry or page, also known as the permalink page, where comments are published and readers are invited to submit their own. 

Once you have created your template, the key factor in determining the kind of archive you are creating is in the archive mapping. An archive mapping is responsible for defining two key elements for an archive template:

* The type of archive the template will produce (category vs. author vs monthly for example). 
* The pattern that will be used in deriving a URL for any given page produced by the archive.

Before we dive into the specific archive types, lets get a grapple on archive mappings, because we will be using them with each of the archive types we can publish.

### Archive Mappings

While index templates output only one file per template, a single archive template can be responsible for publishing hundreds and thousands of files. Furthermore, a single archive template can be used to publish different types of archives. For example, it is completely reasonable for a designer to use the exact same template logic for presenting a list of entries within a specific category as they would to present a list of entries published in a given month. 

Archive mappings give designers the power and flexibility to use and re-use templates to produce a great variety of pages on a web site.  

Let's look at a quick example, and the delve into a mapping's properties in more detail. Here is an example individual archive template declaration:

      individual:
        a_template_id:
          label: "My Entry Feed"
          mappings:
            my_map_id:
              archive_type: Individual
              file_template: %y/%m/%-f.xml

The above sample declares an individual archive template with an id of `a_template_id` and a name of "My Entry Feed." It publishes this template once for every entry in the system using a file naming scheme like this:

    Year + '/' + Month + '/' + Entry Basename + '.xml'

Here is a complete list of properties supported by each archive mapping.

* Element name: *map id*
* Parent Element: `mappings`
* Properties:
  * `archive_type` - One of several allowable strings that identifys the kind and frequency of the archive this mapping refers to. See "Archive Types." 
  * `build_type` - An integer identifying when and how a template under this mapping should be published. See "Build Types" above.
  * `file_template` - A string identifying the output file and folder naming convention that will be used when publishing files under this mapping. e.g. `/2009/12/15/basename.html` or `/category-name/basename/index.html`. 
  * `preferred` - Determines if the mapping under this template is the "preferred" archive to link to when constructing links via the Melody Templating Language. For example, if a theme publishes two entry archives per post, one in HTML and the other in RSS, then what URL should Melody use when processing the tag `<$mt:EntryPermalink$>`? The answer of course is which ever mapping has been flagged as "preferred."

**Tip: you will notice that every mapping is given a unique "map id" the value of which must be unique among the other mappings bound to the same template. Other than that, the map id is effectively ignored by Melody.** 

### Individual Archives 

An individual archive template is responsible for publishing a file for each page and/or entry contained within a site powered by Melody. A site can publish multiple individual archives for a given entry, the primary use case being publishing an entry's permalink page in HTML, in addition to an RSS feed for the entry's comments that readers can subscribe to. 

With a solid understanding of archive mappings, the definition of an archive template is relatively simple:

* Element name: *template ID*
* Parent Element: `templates`
* Properties:
  * `label` - The display name of the template.
  * `mappings` - A list of all of the archive mappings associated with this template. *complex type*

**Supported Archive Mapping Types**

When declaring the archive type in a mapping bound to an individual archive template, only the following archive types are supported:

* Individual - for use with entries.
* Page - for use with pages.

**Example**
 
Here is an example of a config.yaml that declares two different individual archive templates, one for entries and the other for pages.

    templates:
      index:
        main_index:
          label: Main Index
      individual:
        permalink:
          label: Entry
          mappings:
            individual:
              archive_type: Individual
              file_template: %y/%m/%-f
              preferred: 1
        page_content:
          label: Page
          mappings:
            page:
              archive_type: Page
              file_template: %-c/%-f
              preferred: 1

The example above declares two templates, one for entries and the other for pages. The one used for entries has an id of "permalink" and therefore its contents can be found in the template file called "permalink.mtml" in the template set's base path. The template is named "Entry" and will publish each entry to a page accessible via a URL such as the following:

* http://somesite.com/2009/10/a_post.html
* http://somesite.com/2009/11/some_other_post.html
* http://somesite.com/2010/03/my_best_post.html

### Date-based, Category and Author Archive Templates

Generic archive template definitions are virtually identical to individual archive template definitions. Here are their properties:

* Element name: *template ID*
* Parent Element: `templates`
* Properties:
  * `label` - The display name of the template.
  * `mappings` - A list of all of the archive mappings associated with this template. *complex type*

The only real difference lies in what archive types are permissible within the archive mapping declaration. Here is a list of allowable archive mapping types:

**Allowable Archive Mapping Types**

* Daily
* Weekly
* Monthly
* Yearly
* Author
* Author Daily
* Author Weekly
* Author Monthly
* Author Yearly
* Category
* Category Daily
* Category Weekly
* Category Monthly
* Category Yearly

**Example**

Here is an example of a single archive template called "Entry Listing" which is being used to produced to different types of archives, one for categories and one for every month:

    archive:
      entry_listing:
        label: 'Entry Listing'
        mappings:
          by-category:
            archive_type: Category
          by-month:
            archive_type: Monthly

## Modules and Widgets

Template modules and widgets are virtually indistinguishable from one another. In fact the most common observation and question made by designers is, "I honestly can't tell the difference between the two. Why differentiate?"

The answer lies in a desire to keep the widget management function of Melody free and clear of widgets/modules that are not designed to be widgets, or stand alone page elements. For example, consider how confusing it might be to a user if Melody's drag-and-drop widget management interface gave users the option to place the following template modules into the sidebar of a blog:

* Entry Summary
* Blog Header
* HTML Head

Hence, we disambiguate between widgets and modules even though technically they are virtually identical to one another.

### Template Modules

Template modules serve as template fragments that can be shared between templates. They are an excellent way for example of sharing the exact same code to produce the header of your web site across all of your templates. This means that in the event that you need to update your logo then all you have to do is edit a single module and you are done. 

* Element name: *template ID*
* Parent Element: `module`
* Properties:
  * `label` - The display name of the template module.
  * `cache` - The caching preferences for this module. See "Module and Widget Caching Options". *complex type*
  * `include_with_ssi` - The option presumes that Server Side Includes have been enabled for the blog in question. 

**Example**

      module:
        sitemap_mod:
          label: 'Sitemap Include'
          include_with_ssi: 1
          cache:
            expire_type: 1
            expire_interval: 60

### Widgets

Widgets are a type of template module indented for use within the sidebar of a web site. Widgets are made available to users of Melody within its widget management interface in which users can drag and drop widgets to and from sidebars on the web site. They share many, if not all, of the characteristics of a template module. Their properties are:

* Element name: *template ID*
* Parent Element: `widget`
* Properties:
  * `label` - The display name of the template module.
  * `cache` - The caching preferences for this module. See "Module and Widget Caching Options". *complex type*
  * `include_with_ssi` - The option presumes that Server Side Includes have been enabled for the blog in question. 

      widget:
        w_learn_more:
          label: 'Learn More'
        w_photo_of_the_day:
          label: 'Photo of the Day'

### Module and Widget Caching Options

Module and Widget caching is one of Melody's most powerful features in that when properly utilized it can have the most profound impact upon publishing performance. 

Learn more: LINK:The Ultimate Guide to Template Module Caching

*Tip: Keep in mind that setting any of these options presumes that module caching has been enabled on the blog in question. Rest assured however that even if module caching is disabled for the current blog at the time the theme was applied, the preferences you declare within your themes configuration file will be respected once module caching is enabled.*

* Element name: `cache`
* Parent Element: *template id*
* Properties:
  * `expire_type` - An integer signifying what will trigger the cache to be flushed, e.g. a time-based cache or event based cache. See "Expiration Types and Intervals" below.
  * `expire_interval` - The time to live for the cache, as expressed in minutes. Only applicable when `expire_type` is set to 1.
  * `expire_event` - A comma delimited list of the events that will trigger this module's cache to be flushed. See "Expiration Event Types" below.

**Expiration Types and Intervals**

* **1** - Expire the cache after a period of time.
* **2** - Expire the cache upon a specific event. 

**Expiration Event Types**

Users can select from among the following to determine when a module's cache will be flushed. Each of the options below refers to an object type (Author, Entry, TrackBack, etc) that when created, updated or deleted will trigger the cache to be flushed.

* **asset**
* **author**
* **category**
* **comment**
* **entry** 
* **folder** 
* **page** 
* **tbping** 

## System Templates

System templates within Melody are templates designated for specific purposes. They are templates that are always rendered dynamically by the system by virtue of the fact that their contents depend upon user input, e.g. search results, comment previews, etc. 

      system:
        new_password_reset_form:
          label: 'New Password Reset Form'

### Reserved System Template IDs

There are a number of template IDs reserved for system templates that have a predetermined meaning within the context of a web site. By utilizing one of these template IDs for one of your system templates you will be able to customize the presentation of a number of important screens within your website. These IDs are:

*Tip: If a template with one of these IDs cannot be found within a theme, then a default template will be used.*

* `comment_listing` - A template with this ID is used for generating a list of comments in a JSON (Javascript Object Notation) format. The template is used by Melody's entry pagination feature that allows readers to fetch a range of comments associated with an entry.

* `comment_preview` - A template with this ID is used to render the screen that results from a user clicking on the preview button from the commenting form associated with an entry.

* `comment_response` - A template with this ID is used to display a message to a user subsequently to submitting a comment on a web site. This template and the message it contains will only be used if the "Use Comment Confirmation Page" option has been selected under your web site's preferences.

* `dynamic_error` - A template with this ID will be used to present errors to the user. Without this template users will be greeted with a default system error message styled with the Melody logo.

* `login_form` - A template with this ID is used to prompt a visitor for a set of credentials (usually a username/password combination) to login to the web site.

* `new_password` - A template with this ID is used to prompt a user who has initiated the password recovery process with a form to choose a new password.

* `new_password_reset_form` - A template with this ID is used to prompt a visitor of a web site for an email address for which to recover a password. If a user is found with that email address they will be sent a link to a form to reset their password. 

* `popup_image` - This rarely used template is used by Melody to present to render the screen that results from a user clicking on a image inserted into an entry with the option "Link image to full-size version in a popup window" selected from the Insert Image wizard. 

* `register_confirmation` - A template with this ID is used to present a message to a user upon completion of a registration form. The screen could present a success message, a message indicating that the user must verify their account via email first, or an error message. 

* `register_form` - A template with this ID is used to present the registration form to a user wishing to become a member of a web site or blog. It is on this form that they would enter a desired username, password and other profile information.

* `search_results` - A template with this ID is used to display search results on a web site.

### System Template Variables and Context

TODO - document the variables that are available in each of the various system templates.

## Widget Sets

Widget sets are nothing more than containers for a group of widgets. For many web sites, the term "widget set" might be interchangeable with the concept of "sidebars" in that widgets are often arranged in some way in the sidebar of each and every page of a web site. 

Widget sets have two primary properties: a name and a listing of widgets contained by them. Widget sets can be inserted into a web site using the template tag:

    <$mt:WidgetSet name="Homepage Sidebar"$>

Its properties are:

* Element name: *widgetset id*
* Parent Element: `widgetset`
* Properties:
  * `label` - The name of the widget set as it will appear in Melody's user interface and how a designer will reference it via the `<$mt:WidgetSet$>` template tag.
  * `widgets` - An ordered list of widget names that will comprise the sidebar. Each name listed should have a corresponding widget with the same defined within the `widget` section of the corresponding template sets configuration.

**Example**

      widgetset:
        homepage:
          label: "Homepage Sidebar"
          widgets:
             - 'Search Box'
             - 'Advertisement'
             - 'Recent Comments'
             - 'Popular Entries'

## Theme Options

Melody offers designers with a simple way of surfaces users of their themes with an options pane within the CMS that gives their users the means to configure and customize their theme without ever having to edit HTML, Melody template code, CSS or the like. It is the preferred mechanism by most designers to give their users who have very little technical knowledge a great deal of control over their web site in prescribed ways.

Furthermore, these options are defined strictly through a configuration file. There is no knowledge of Perl, no knowledge of PHP, no knowledge of a programming language of any kind required to be able to surface to your users a wide variety of controls for their web site.

When a theme defines options for itself, a menu item called "Theme Options" will automatically appear under Melody's  Design menu. Selecting that menu item will take the user to a dashboard listing all of the theme's options grouped nicely into sections for ease of use and organization.

Here is a sample `config.yaml` which declares a theme called "We Love Melody." In this theme we expose three options:

1. A place for a user to enter their "Feedburner ID."
2. A place for a user to toggle the use of Feedburner on and off.
3. A place for a user to enter how many entries they wish to appear on the front door.

In addition, this hypothetical theme defines three template tags for the designer to access the values entered by the user. Again, this is done automatically for you without any need to know or learn a programming language.

    id: DemoThemePlugin
    name: My Theme Demo
    template_sets:
      melody_rocks:
        label: "We Love Melody"
        options:
          fieldsets:
            homepage:
              label: 'Homepage Options'
            feed:
              label: 'Feed Options'
          feedburner_id:
            type: text
            label: "Feedburner ID"
            hint: "This is the name of your Feedburner feed."
            tag: 'MyPluginFeedburnerID'
            fieldset: feed
          use_feedburner:
            type: checkbox
            label: "Use Feedburner?"
            tag: 'IfFeedburner?'
            fieldset: feed
          posts_for_frontfoor:
            type: text
            label: "Entries on Frontdoor"
            hint: 'The number of entries to show on the front door.'
            tag: 'FrontdoorEntryCount'
            fieldset: homepage
            condition: > 
              sub { return 1; }

### Field Sets

Field sets are a grouping of related options associated with a theme. Field sets provide designers with a simple way of organizing and segmenting fields into different options screens under the "Theme Options" menu item. 

* Element name: fieldsets
* Parent Element: `options`
* Properties:
  * *fieldset_id* - A list of fieldsets each identified by a unique fieldset ID. Fields will reference this fieldset ID for placement. *complex type*
    * `label` - The display name of the fieldset.
    * `order` - The sort order of the fieldset determining its placement in the navigation between fieldsets.

### Fields

Fields represent each individual option you wish to expose to a theme's user or administrator. There is a wide variety of form element types to choose from, e.g. radio buttons, pull down menus, text areas, etc. The types of fields are also extensible so that if you find that there is particular type of field missing, contact a developers, they can create it for you.

TODO: Link:Theme Options Developer Reference

Each field definition supports the following properties:

* Element name: *field id*
* Parent Element: `options`
* Properties:
  * `type` - the type of the field. See "Field Types" for a list of supported types and any special syntaxes they support.
  * `label` - the label to display to the left of the input element
  * `show_label` - Determines whether or not to display the field's label. In some cases, as with checkboxes, it is desirable to suppress the label. Default: true.
  * `hint` - the hint text to display below the input element
  * `tag` - the template tag that will access the value held by the corresponding input element
  * `condition` - a code reference that will determine if an option is rendered to the screen or not. The handler should return true to show the option, or false to hide it.
  * `order` - the sort order for the field within its fieldset
  * `republish` - a list of template identifiers (delimited by a comma) that reference templates that should be rebuilt when a theme option changes

#### Supported Field Types

Below is a list of field types supported by Melody. APIs exist for developers to extend this list with custom fields/options should the list below not contain the field type you need.

* `text` - Produces a simple single line text box.

* `textarea` - Produces a multi-line text box. You can specify the `rows` sibling element to control the size/height of the text box.

* `select` - Produces a pull-down menu or arbitrary values. Those values are defined by specifying a sibling element called `values` which should contain a comma delimited list of values to present in the pull down menu

* `checkbox` - Produces a single checkbox, ideal for boolean values.

* `blogs` - Produces a pull down menu listing every blog in the system. *Warning: this is not advisable for large installations as it can dramatically impact performance (negatively).*

* `radio-image` - Produces a javascript enabled list of radio buttons where each "button" is an image. Note that this version of the radio type supports a special syntax for the `values` attribute. See example below.

* `tagged-entries` - Produces a pull down menu of entries tagged a certain way. This type supports the following additional attributes: `lastn` and `tag-filter`.

* `entry` - Produces a simple button that when clicked will surface a modal dialog in which a user can select an entry to link to. Ideal for selecting a featured story for the homepage.

**Example**

The following example shows how one would define a theme option of type "Radio Image," or set of radio buttons whose labels are graphical as opposed to text. 

The `radio-image` type supports a special syntax for the `values` attribute. The list of radio button is a comma-delimited list of image/value pairs (delimited by a colon). Got that? The images you reference are all relative to Movable Type's mt-static directory. Confused? I think a sample will make it perfectly clear:

      homepage_layout:
        type: radio-image
        label: 'Homepage Layout'
        hint: 'The layout for the homepage of your blog.'
        tag: 'HomepageLayout'
        values: >
          "plugins/Foo/layout-1.png":"Layout 1","plugins/Foo/layout-2.png":"Layout 2"

### Defining Template Tags

Each individual theme option or field can define a template tag by which a designer or developer can access the value saved by the user. 

*Tip: If a tag name terminates in a question mark then the system will interpret the tag as a conditional block element, allowing you to use the tag in conjunction with the `<mt:Else>` tag.*

**Example**

    feedburner_id:
        type: text
        label: "Feedburner ID"
        hint: "This is the name of your Feedburner feed."
        tag: 'FeedburnerID'
    use_feedburner:
        type: checkbox
        label: "Use Feedburner?"
        tag: 'IfFeedburner?'

And here are corresponding template tags that make use of these configuration options:

    <mt:IfFeedburner>
      My feedburner id is <$mt:FeedburnerID$>.
    <mt:Else>
      Feedburner is disabled!
    </mt:IfFeedburner>

## Global Templates