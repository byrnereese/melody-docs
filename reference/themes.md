# Creating a Theme in Melody

This manual will be your guide and reference in building themes for the Melody platform.

## What is a Theme?

A theme in Melody, also known as a "template set," is a collection of templates that when used together define the look and feel, as well as the behavior of a web site. 

## Packaging a Theme

A theme is a type of plugin in Melody that defines one or more sets of templates that a user can later apply to their blog or web site quickly and easily. As with plugins, the heart of every theme in Melody is a configuration file, named `config.yaml`, which defines all of its various characteristics, including a list of all the templates the theme contains and utilizes. In addition, this configuration file is responsible for defining:

* Any configuration options associated with a theme.
* Any blog settings and/or preferences that a theme relies upon to operate properly. 

In addition to this configuration file, and the templates a theme utilizes, a theme must also contain all of the javascript, CSS, images and other static files needed by your web site. These files live in a directory called `mt-static`, the standard location for all such files in Melody. 

With this in mind therefore, you can think of a theme being broken into two groups of files: program files (which includes the templates) and static files. Program files are placed in the `plugins` directory and static files placed in the `mt-static` directory. Let's take a look at a hypothetical theme exactly as it would appear following you downloading it, and unzipping it onto your desktop:

    MyTheme/
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

The structure mentioned above should be immediately apparent. At the top of the directory tree in the example above is a folder called MyTheme. This is the one folder that is created after unzipping your newly downloaded theme and it contains **all of the files** needed by the theme. Within this folder are two other sets of folders. They are:

* `plugins/MyTheme/`
* `mt-static/plugins/MyTheme/`

You can see that both your theme's program files and static files are grouped together into a folder bearing the same name, which in this case is "MyTheme." This convention is used to prevent the files from one theme from overwriting or colliding with files from another theme or plugin. 
            



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