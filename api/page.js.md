# Page.js API documentation
	
## How to use 

In order to allow both the Cordova and LigerMobile frameworks to initialize properly, we recommend using the following template for each of your app's page's javascript.

``` javascript
//  This will be called by the included page.js as part of the LigerMobile initialization.
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
		
## API

Below is a list of the most commonly used functions that LigerMobile provides.  In most cases you simply call the method with the required arguments, however, in the case of the PAGE.childUpdates and PAGE.closeDialogArguments functions, the common practitice is to overwrite them in the calling pages javascript.


### openPage(title, page, args);

Opens a new page.

* iOS Pushes a UIViewController to a UINavigationController.

* title The title of the page (title in UINavigationBar on iOS).
* page The 'name' of the page to be open. Should not include html.
* args Json that will be sent to page.

### closePage()

Closes the currently open page.
Can't close a top level page.

### closeToPage(page)
 
Closes all pages above 'page' in the navigation stack.
Can't close a top level page.

* page The page to be displayed after the pages have been closed.

### updateParent(args)

Sends arguments to the parent page.

* args Arguments you want to be sent to childUpdates on the parent page.

### updateParentPage(page, args)

Sends arguments to the parent page.

* page The name of the first parent page (not including yoursef) you want to send the arguments to.
* args Arguments you want to be sent to childUpdates on the parent page.

### childUpdates(args)

Called on the parent of a page that called updateParent.

* args The arguments from updateParent.

### openDialog(page, args)

Opens a new page as a dialog.

* iOS Presents a UIViewController.

* page The 'name' of the page to be open. Should not include HTML.
* args Json that will be sent to openPageArguments.

### openDialogWithTitle(title, page, args)

Opens a new page as a dialog including a title.

* iOS Presents a UINavigationController with a page in it.

* title The title of the page (title in UINavigationBar on iOS).
* page The 'name' of the page to be open. Should not include html.
* args Json that will be sent to openPageArguments.

### closeDialog(args)

Closes an open dialog.

Sending {"resetApp": true} in the args will reset the app. Use when closing a signout page, advertiser selection page, or similar.

* iOS Dismisses the current UIViewController.

* args Json argument to send back to page that opened the dialog by calling closeDialogArguments.

### toolbar(items)

Sets the toolbar items.

* items An array of hashes, one per item. They keys are icon: character, callback: javascript code in a string to be executed when the item is tapped.

### canRefresh()

Indicates whether this web view can be refreshed by the user or not


## Callbacks

### closeDialogArguments(args)

This callback is called when a dialog launched from this page is closed.

* args Json arguments from the dialog being closed.

### pushNotificationTokenUpdated(token, type, error)

If notifications has been turned on a push notification token will be sent to
the root page. If an error occured an empty token will be sent and an error included.

* token The push notification token for this app and device.
* type iOSDeviceToken for iOS.
* error If an error has occured a text string with the error.

### notificationArrived(notification, background)

If a notification arrives when the app is running (either in the foreground or background)
this function will be called. If the app is started up as a result of a notification the notification
will be included in the args for the root page under the key 'notification'.

* notification The notification that came in as a json string
* background True if the notification arrived with the app was in the background, otherwise false.