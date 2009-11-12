# Creating a Theme in Melody

This manual will be your guide and reference in building themes for the Melody platform.

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

## Basic Theme Metadata

    template_sets:
      theme_id:
        base_path: templates/theme_id
        label: 'My Theme'
        order: 101

## Templates

    templates:
      index:
      individual:
      module:
      widget:
      widgetset:
      system: 

**Template IDs**

**Template Content**

      index:
        some_template_id:
          label: 'My Template'
          filename: 'password_reset.mtml'

### Index Templates

      index:
        apache:
          label: 'Apache Include'
          outfile: 'httpd-chicagonow.conf'
          rebuild_me: 0
          build_type: 2

### Individual Archives

      individual:
        entry:
          label: Entry
          mappings:
            individual:
              archive_type: Individual
              file_template: %y/%m/%-f
              preferred: 1
        page:
          label: Page
          mappings:
            page:
              archive_type: Page
              file_template: %-c/%-f
              preferred: 1

### Archive Templates

      archive:
        gallery_category_entry_listing:
          label: 'Category Entry Listing'
          mappings:
            category:
              archive_type: Category
              preferred: 1
              build_type: 4

### Modules

      module:
        sitemap_mod:
          label: 'Sitemap Include'
          cache:
            expire_type: 1
            expire_interval: 60

### Widgets

      widget:
        w_learn_more:
          label: 'Learn More'
        w_photo_of_the_day:
          label: 'Photo of the Day'

### System Templates

      system:
        new_password_reset_form:
          label: 'New Password Reset Form'
          filename: 'password_reset.mtml'

### Widget Sets

      widgetset:
        homepage:
          label: Homepage
          widgets:
             - 'Search Box'
             - 'Ad: Sidebar, Placement 1'
             - 'Subscribe (Feed)'
             - 'Recent Comments'
             - 'Juitter Tweets'
             - 'Featured Entries'

## Theme Options
v
## Global Templates