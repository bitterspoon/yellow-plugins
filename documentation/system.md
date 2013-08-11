Configure system
================

All configuration is located in the **system folder**. You can change your website settings here.

![Screenshot](picture_system.png?raw=true)

The `config` folder contains configuration files. The `core` folder is for the Yellow software itself, its content changes only with a software update. The `plugins` folder is for Yellow plugins, to add new features. Most configuration happens in the `snippets` and `templates` folders, where the website layout and functionality is defined.

Changes in system folders affect the entire website.

Configuration files
-------------------
The main configuration file is `system/config/config.ini`. You can define the default settings of your website here. For a new installation you should set sitename, author and language. Here's an example:

    sitename = Anna's Design Company
    author = Anna's Design Company
    language = en
    template = default
    style = default
    parser = markdown

These settings can be overwritten in the meta data of a page. Configuration files should be stored in [UTF-8](http://en.wikipedia.org/wiki/UTF-8).

Templates
---------
The default template is `system/templates/default.php`. A template controls the output of a page. An individual template can be defined in the meta data of a page, for example `Template: welcome` uses the file `system/templates/welcome.php`. There are little limitations, templates can generate web pages and other output formats. Here's an example:

    <?php $yellow->snippet("header") ?>
    <?php $yellow->snippet("navigation") ?>
    <?php $yellow->snippet("content", $yellow->page->getTitle(), $yellow->page->getContent()) ?>
    <?php $yellow->snippet("footer") ?>

Write any [PHP](https://en.wikipedia.org/wiki/PHP) code you like and use the [Yellow API](yellowapi.md) for common functionality.

Snippets
--------
Snippets are pieces of PHP located in the `snippets` folder. They allow to re-use the same code in multiple templates:

    <?php $yellow->snippet("navigation") ?>

You can pass arguments to snippets:

    <?php $yellow->snippet("content", $argument1, $argument2) ?>

Have a look at some of the existing snippets. There are [snippets](https://github.com/markseu/yellowcms-extensions/tree/master/snippets)  and [templates](https://github.com/markseu/yellowcms-extensions/tree/master/templates) you can download.

Error handling
--------------
Yellow will tell you when something goes wrong. For example a missing file shows "File not found" with corresponding [HTTP status code](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes). The file `system/config/error404.txt` defines how a missing file looks like. You have complete control over what's shown to visitors. 

Check the web server logfile for further information.