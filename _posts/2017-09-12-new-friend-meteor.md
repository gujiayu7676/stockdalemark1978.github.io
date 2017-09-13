---
layout: post
title:  "My New Friend Meteor"
date:   2017-09-12 12:37:43 -0400
categories: 		
---
## My New Friend Meteor

Since the completion of my web dev bootcamp, I've been playing around with some technologies that we did not learn during the camp. One of my new favorites is a called Meteor.

Meteor is a complete platform for building web and mobile apps using pure javascript. This means that it's a full-stack system, meaning it allows you to build everything you need for both front-end development and also back-end development. You won't need a separate back-end setup, such as PHP and PostgreSQL for example.

Meteor is free and open-source and is written using Node.js. It uses MongoDB as it's database and comes with it's own templating engine for front-end work, but you can also use React, Angular, or whatever you want. In short, it's basically a collection of a bunch of tools that are designed to work well together.

Meteor comes bundled with all of it's dependencies which means when you install it, everything is included. You don't have to install everything separately. Things such as Node.js and NPM come already included.


The way that Meteor flows is something like this:

![Meteor Diagram](/img/Meteor Diagram.jpg)


So Meteor looks pretty neat, right?!

# How To Install Meteor

Now that you see how cool Meteor is, you have to get it installed so it can be used. Fortunately, installing Meteor is pretty simple and it can be installed on Mac, Windows, or Linux.

If you are on Windows, there is a install package that makes things pretty simple. Head on over to https://www.meteor.com/install and click "Download Installer" for Windows.

If you are on a Mac or Linux machine, you will install Meteor via the terminal like so:

    curl https://install.meteor.com/ | sh

This will run the downloader and install Meteor and all of it's dependencies on your machine. If you are prompted for your password, simply enter it and the install process will begin.

After the process has finished we will check to see that Meteor was installed properly by typing:

    meteor --version  

If Meteor has been installed properly, after typing this command you will see the version of Meteor that is now on your machine. For me, at the time of this writing, my version is 1.5.2 so in my terminal I see:

    Meteor 1.5.2

You may see a different version number depending on when you run the installation.

If you've made it this far, then you've successfully installed Meteor. Congratulations!

One last thing I want to show you is the "help" command. Using the help command will show you a whole list of commands you can use from the terminal for Meteor. This list can come in pretty handy especially when you are new to using Meteor. To access the help list, type:

    meteor --help

You will now see a long list of commands you can use. It will look something like this:

    Built-in Commands:
       run                [default] Run this project in local development mode.
       debug              Run the project, but suspend the server process for debugging.
       create             Create a new project.
       update             Upgrade this project's dependencies to their latest versions.
       add                Add a package to this project.
       remove             Remove a package from this project.
       list               List the packages explicitly used by your project.
       add-platform       Add a platform to this project.
       remove-platform    Remove a platform from this project.
       list-platforms     List the platforms added to your project.

       build              Build this project for all platforms.
       lint               Build this project and run the linters printing all errors and warnings.
       shell              Launch a Node REPL for interactively evaluating server-side code.
       mongo              Connect to the Mongo database for the specified site.
       reset              Reset the project state. Erases the local database.
       deploy             Deploy this project to Meteor.
       logs               Show logs for specified site.
       authorized         View or change authorized users and organizations for a site.
       claim              Claim a site deployed with an old Meteor version.
       login              Log in to your Meteor developer account.
       logout             Log out of your Meteor developer account.
       whoami             Prints the username of your Meteor developer account.
       test-packages      Test one or more packages.
       test               Test the application
       admin              Administrative commands.
       list-sites         List sites for which you are authorized.
       publish-release    Publish a new meteor release to the package server.
       publish            Publish a new version of a package to the package server.
       publish-for-arch   Builds an already-published package for a new platform.
       search             Search through the package server database.
       show               Show detailed information about a release or package.

Alright, that's it for now. I hope this was helpful!
