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

You will also see a folder called "layouts".

##### /source/layouts/

Inside this file is an erb file (Embedded RuBy = erb) which defines the HTML structure your html pages are injected into.

This file provides the stuff that wraps around your individually created pages like the meta information, the html tag, head tag etc. and injects every page into this layout into the area called ```yield```.

As this is an erb file, your ruby and Middleman helpers are contained within the <% %> tags.

Think of these as ways of injecting ruby code into the file.

When you see a tag have a ```<%``` and an equals file after the percentage sign, ie ```<%= %>```, that means "turn this code into a visible entitiy, turn it into HTML or text"

So, the following tag will print out the first line "I love cats" into every HTML page but not the second line:

```erb
<%= "I love cats!" %>
<% "And slime for dinner!" %>
```

Naturally when you are printing things out into the HTML you can call more interesting things than just a string of words. You can call some powerful ruby code.

> You may also be thinking "Why would I write code but not output it into my HTML?". The answer is, the non-printed erb tag sets up your page to connect to data files and the like. So, you might use the non-printing erb tag to call up a database or a bit of ruby code to loop over several times which you then print out selected outputs from that database call. Still lost? Don't worry, we'll cover this and erb later [link](link)

> Link to erb section

> Explanation anyway. Example of layout included:

Let's have a quick look at our layout file:

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

Here we can see some erb in action in different ways. Let's start from the bottom and make our way up.

The ```<%= yield %>``` tag, as we mentioned, is the place where your invidiual page HTML files will be injected in. This saves us from having to include the head section in each page as well as the footer, navigation or other common page structures.

In the body element you will see an outputted Ruby method called ```page_classes``` inside a CSS class.

This is a Middleman method that is given to us for free, what it does is for each page, it locates the name of the page and then injects that name into the body class. The value of this is  that it gives us the ability to optionally style a particular page and its body class

You will also see some YAML at the top of the page which provides useful information to a template, like the title page etc.

```yaml
---
title: Welcome to Middleman
---
```

Lets see that work by building the static site from the Middleman source
