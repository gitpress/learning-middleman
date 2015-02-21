# Initilizing your first Middleman site

Let's build that site already!

Now that you have Middleman installed, run the middleman init command to create a project with the name of your choosing:

```bash
#use middleman init to create the site
middleman init portfolio
```

As you may have noticed, the name after the **middleman init** command is where you write your project name. If it has more than one word use the Ruby tradition of "snake_case" rather than "camelCase".

So, if you wanted to call your project "My Totally Awesome Site" you'd write it my_totally_awesome_site.

This command will create a folder named after your project name as well as create a "gemfile" from which you can indicate what "gems" or Ruby libraries you want to save.

> INSERT IMG and EXPLANATION IF NEEDED of files
 
Let's move into the newly created folder to get building. For me I run:

```bash
# Because my project was called portfolio, I change directory into that folder
cd portfolio
```

You should now see four files and a folder called source. Your directory looks something like this:

* /source
* .gitignore
* config.rb
* Gemfile
* Gemfile.lock

Let's work from the bottom up. 

#### Gemfile.lock

Your Gemfile.lock is there to lock down the versions of Gems that you used to create the project and your various dependencies.

#### Gemfile

If you have a decent background in Ruby or Rails you will know what a Gemfile is. It is essentially your place to indicate what Gems you want to use for your project and if needed, the specific version or source for each gem.

On your initial load your gemfile will look something like:

```Ruby
#Example Gemfile with comments removed
gem "middleman", "~>3.3.7"
gem "middleman-livereload", "~> 3.1.0"
gem "wdm", "~> 0.1.0", :platforms => [:mswin, :mingw]
gem "tzinfo-data", platforms: [:mswin, :mingw]
```

At the moment we have the default gems but we'll soon edit it to add some more interesting functionality like blogging ability.

#### config.rb

This file is where you get to set up how you want your Middleman tool to work for you. As we go through this book we will make changes to this file but feel free to choose what works for you.

This includes enabling relative URLs, choosing whether certain pages have different layouts (templates) and utilzing other helper methods and tools.

For now, don't worry about changing it.

> A list of the options and things you can tweak are available on the [Middleman website](http://middlemanapp.com/) in various sections.

> In chapter x, I go through some possible options as well {{{INSERT LATER}}}

#### .gitignore

If you're not using git, and i'd recommend that you do or put it on your list to master, feel free to **ignore** the ```.gitignore``` file. If you do use it, you should know that it lists the files and directories that you ask git not to include when adding files to version control.

#### /source

This directory is where you will write your HTML, CSS and JS.

Inside you will see futher folders for images, javascripts, stylesheets which are all pretty self explanatory.

> Explanation anyway. Example of layout included:

you will also see an ebedded ruby HTML page that, on using the Middleman build command, will get wrapped into its layout.

```erb
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <!-- Always force latest IE rendering engine or request Chrome Frame -->
    <meta content="IE=edge,chrome=1" http-equiv="X-UA-Compatible">
    <!-- Use title if it's in the page YAML frontmatter -->
    <title><%= current_page.data.title || "The Middleman" %></title>
    <%= stylesheet_link_tag "normalize", "all" %>
    <%= javascript_include_tag  "all" %>
  </head>
  
  <body class="<%= page_classes %>">
    <%= yield %>
  </body>
</html>
```

You will also see some YAML at the top of the page which provides useful information to a template, like the title page etc.

```yaml
---
title: Welcome to Middleman
---
```

Lets see that work by building the static site from the Middleman source
