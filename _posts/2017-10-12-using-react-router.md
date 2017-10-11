---
layout: post
title:  "Setting Up And Using React Router"
date:   2017-10-12 11:14:13 -0400
categories: 		
---
## Setting Up And Using React Router

For the past month or so, I've been spending time learning how to use React on the front-end of a couple of projects. In my bootcamp, we learned how to use AngularJS on the front-end. AngularJS was difficult for me at that time. I'm not sure if it was just my inexperience with programming at that time, or if AngularJS is just tough to learn, but I've found React to be easier to pick up.

# Setting Up React Router

In React, there are several different Node package options that can be installed to allow you to setup your various routes for your project. The one I learned about and used for my projects is something called "React Router."

To learn more about React Router, visit the repo [here](https://github.com/ReactTraining/react-router) or alternatively you can visit the npm package page [here](https://www.npmjs.com/package/react-router).

Just a note here, I used version 3.0.0. for my projects. There is actually a newer version so things could be a bit different for the current version.

So to get started, you have to install React Router first. I'm using Meteor here as well:

  meteor npm install react-router@3.0.0

If you leave off the version number, it will automatically install the latest version.

After you've installed, be sure to go to your package.json file to be sure React Router has been added to your list of dependencies. You should see something like this:

  "react-router": "^3.0.0"

# Creating Routes with React Router

In order to use React Router, you will need to import it into your .js document. In my case, since I was using Meteor, that was my main.js within my client folder. At the top of the page, you will enter:

  import { Router, Route, browserHistory } from 'react-router';

In this example, let's assume we have a Signup component created within our project and you want the route to be "http://www.mydomain.com/signup". First, you have to have the component imported into the main.js file. At the top of the page you will have your import command with the location to the Signup component. In my case, that is:

  import Signup from '../imports/ui/Signup';

In my case, since I'm using Meteor, I also have to have the Meter startup method, passing in "routes":

  Meteor.startup(() => {
  ReactDOM.render(routes, document.getElementById('app'));
  });

Lastly, you will need to actually construct the route for your Signup component:

  const routes = (
  <Router history={browserHistory}>
    <Route path="/signup" component={Signup}/>
  </Router>
  );

Now, your browser will know that /signup is the route that points to the signup page of your app. If you have other routes, such as Login, you just add them in like so:

  const routes = (
  <Router history={browserHistory}>
    <Route path="/signup" component={Signup}/>
    <Route path="/" component={Login}/>
  </Router>
  );

Here the Login component has a route on the homepage of the app.
