Liger Common
================================================================================

Liger is an extension of the idea put forth by Phonegap, Titanium and others, that having a single code base for mobile apps, while not the perfect solution, is the best solution right now.  Liger allows web developers to make use of their existing skill sets to write mobile applications using HTML, CSS and javascript, while maintaining much of user experience cues, users have come to expect.

# CI          [![Build Status](https://api.travis-ci.org/reachlocal/liger-common.png)](https://travis-ci.org/reachlocal/liger-common)

# Differences between Liger and Cordova, Phonegap, etc.

Liger extends the Cordova Framework, but the thought process behind them is vastly different.  The Cordova framework lends itself nicely to bringing the growing trend of single page apps to the mobile device.  In a cordova app there is generally a single web view that is loaded, and then all HTML updates are done within that webview.  

With Liger the goal was to keep the web view, but allow for multiple instances of it.  This allows for us to present native transitions to new pages whenever a view is required.

# Prerequisites

1.  Must be have downloaded either the Liger iOS or Liger Android repositories.

# Workflow

The following is the recommended workflow for building a liger app.

1. In the app.json define the name and page information (hello for this example) of the page that will be the home page as the first item in the menu object.

1. Create an html file (hello.html) of the same name in the same directory as the app.json.
1. In the hello.html, include references to the included vendor files and js/pages/hello.js (this is your page's unique functionality).

        <script type="text/javascript" src="vendor/cordova.js"></script>
        <script type="text/javascript" src="vendor/page.js"></script>
    	<script type="text/javascript" src="vendor/liger.js"></script>
    	<script type="text/javascript" src="app/js/pages/hello.js"></script>
    	
1. In the js/pages directory create a corresponding hello.js file.
1. In the hello.html, intialize the liger app, by calling PAGE.initialize("hello");

	<script>
        	PAGE.initialize("hello");
    	</script>
    	
1. At this point add your html via whatever method you're most comfortable.  This repo (link) shows examples using Handlebars, Angular.js, 
Underscore and plain HTML.

2. In your hello.js add any bindings, animations, etc., that bring your idea to life.

# What Liger Provides

Below is a list of the most commonly used functions that Liger provides.  In most cases you simply call the method with 
the required arguments, however, in the case of the PAGE.childUpdates and PAGE.closeDialogArguments functions, the common 
practitice is to overwrite them in the calling pages javascript.

- Open New Page Functionality

		PAGE.openPage(title, link, args)
		
- Close current page functionality

		PAGE.closePage(args)
		
- The ability to update parent pages

		PAGE.updateParent(args)
		
- The ability to update an individual page in the stack

		PAGE.updateParentPage(link, args)
		
- The ability to close all pages, down to a certain page in the stack

		PAGE.closeToPage(link)
		
- The ability to open a new dialog page

		PAGE.openDialog(link, args)
		
- The ability to close a dialog page

		PAGE.closeDialog(args)
		
# How To Setup Your Javascript

In order to allow both the Cordova and Liger frameworks to initialize properly, we recommend using the following template for each 
of your app's page's javascript.

		//  This will be called by the included page.js as part of the liger initialization.
		PAGE.hello = function(){
    		HELLO.initialize();
		}
		
		/* 
		*
		*	If this page will be receiving updates from a child page, you can setup the unique
		*	functionality by overwriting the PAGE.childUpdates() function here.
		*
		*/  		
		PAGE.childUpdates = function(args){
			// Maybe for instance you want to reintialize the page.
			HELLO.initalize();
		}

		//  All of the code unique to the page's functionality
		var HELLO = {
			initialize: function(){
				var me = this;
				
				/* 
				*
				*	All arguments that have been passed to this page are now ready to be accessed.
				*	They can be found in the PAGE.args object.  
				*
				*
				*/
				
				if(PAGE.args){
					if("world" in PAGE.args){
						// Call other stuff that works with world object
					}
				}
				
				$("#openPage").click(function(){
					PAGE.openPage({'nameofnextpage', {map of arguments to pass});
				});
			}
			
			// lots of other cool stuff
		}

# To Run The Tests

To run the tests you must have node.js installed.  If you have it installed skip this step, if not use brew to install it.

		brew install node

Then run.

		npm install
		npm test


