LigerMobile Common
================================================================================

LigerMobile is an extension of the idea put forth by Phonegap, Titanium and others, that having a single code base for mobile apps, while not the perfect solution, is the best solution right now.  LigerMobile allows web developers to make use of their existing skill sets to write mobile applications using HTML, CSS and javascript, while maintaining much of user experience cues, users have come to expect.

# CI          [![Build Status](https://api.travis-ci.org/reachlocal/liger-common.png)](https://travis-ci.org/reachlocal/liger-common)

# Differences between LigerMobile and Cordova, Phonegap, etc.

LigerMobile extends the Cordova Framework, but the thought process behind them is vastly different.  The Cordova framework lends itself nicely to bringing the growing trend of single page apps to the mobile device.  In a cordova app there is generally a single web view that is loaded, and then all HTML updates are done within that webview.  

With LigerMobile the goal was to keep the web view, but allow for multiple instances of it.  This allows for us to present native transitions to new pages whenever a view is required.

# Prerequisites

1.  Must be have downloaded either the LigerMobile iOS or LigerMobile Android repositories.

# Workflow

The following is the recommended workflow for building a LigerMobile app.

1. In the app.json define the name and page information (hello for this example) of the page that will be the home page as the first item in the menu object.

1. Create an html file (hello.html) of the same name in the same directory as the app.json.
1. In the hello.html, include references to the included vendor files and js/pages/hello.js (this is your page's unique functionality).

        <script type="text/javascript" src="vendor/cordova.js"></script>
        <script type="text/javascript" src="vendor/page.js"></script>
    	<script type="text/javascript" src="vendor/liger.js"></script>
    	<script type="text/javascript" src="app/js/pages/hello.js"></script>
    	
1. In the js/pages directory create a corresponding hello.js file.
1. In the hello.html, intialize the LigerMobile app, by calling PAGE.initialize("hello");

	<script>
        	PAGE.initialize("hello");
    	</script>
    	
1. At this point add your html via whatever method you're most comfortable.  This repo (link) shows examples using Handlebars, Angular.js, 
Underscore and plain HTML.

2. In your hello.js add any bindings, animations, etc., that bring your idea to life.

