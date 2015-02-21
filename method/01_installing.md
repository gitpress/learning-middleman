# Installing Middleman

To get Middleman working we need to download the gem. If you like, feel free to create a file which we can work in for the rest of the book: 

```sh
# CLI command to create a file and move into the directory
$ mkdir middleman && cd middleman
```

> If you are using Windows this command won't work because of the operator && (stands for AND. That is,  do the first command AND the second). If you must use Windows I recommend installing a Linux-y command line tool to follow along. You can also install git bash and use that.

> Alternatively, you can work through your browser and connect to a Linux box using one of the many in-browser IDEs. I personally do this all the time and find it a great experience for when I am on a Windows machine. My personal preference is to use [Codio](http://www.codio.com), as it has a brilliant free tier and is the most reliable.

Now download the Middleman gem by running the following command:

```sh
# download the middleman gem
$ gem install middleman
```

this downloads the necessary files. It may take a while due to documentation so feel free to brew yourself a cup of tea. 

> This command won't work if you don't have Ruby installed on your machine. If you don't go do that.

If you are using a ruby version manager like rbenv you may need to refresh your gemset. Using rbenv this command is:

```shell
# refresh your rbenv gemset
rbenv rehash
```

Right, you should now have a ready to use Middleman gem. We now have at your fingertips the ability to run Middleman commands.
