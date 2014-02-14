# Page.js API documentation
	
## How to use 

In order to allow both the Cordova and Liger frameworks to initialize properly, we recommend using the following template for each 
of your app's page's javascript.

``` javascript
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
```
		
# API

Below is a list of the most commonly used functions that Liger provides.  In most cases you simply call the method with the required arguments, however, in the case of the PAGE.childUpdates and PAGE.closeDialogArguments functions, the common practitice is to overwrite them in the calling pages javascript.

- Open New Page Functionality

``` javascript
		PAGE.openPage(title, link, args)
```	

- Close current page functionality

``` javascript
		PAGE.closePage(args)
```
		
- The ability to update parent pages

``` javascript
		PAGE.updateParent(args)
```
		
- The ability to update an individual page in the stack

``` javascript
		PAGE.updateParentPage(link, args)
```
		
- The ability to close all pages, down to a certain page in the stack

``` javascript
		PAGE.closeToPage(link)
```
		
- The ability to open a new dialog page

``` javascript
		PAGE.openDialog(link, args)
```
		
- The ability to close a dialog page

``` javascript
		PAGE.closeDialog(args)
```