# page.js API documentation

Below is a list of the most commonly used functions that LigerMobile provides. In most cases, you simply call the method with the required arguments. However, for callback functions such as PAGE.childUpdates and PAGE.closeDialogArguments, the common practice is to overwrite them in the calling page's Javascript.

---

## Table of contents

* [How to use](#how-to-use)
* [API](#api)
  * [openPage](#openpagetitle-page-args-options)
  * [closePage](#closepage)
  * [closeToPage](#closetopagepage)
  * [updateParent](#updateparentargs)
  * [updateParentPage](#updateparentpagepage-args)
  * [openDialog](#opendialogpage-args-options)
  * [openDialogWithTitle](#opendialogwithtitletitle-page-args-options)
  * [closeDialog](#closedialogargs)
  * [toolbar](#toolbaritems)
  * [canRefresh](#canrefresh)
* [Callbacks](#callbacks)
  * [childUpdates](#childupdatesargs)
  * [closeDialogArguments](#closedialogargumentsargs)
  * [onPageAppear](#onpageappear)
  * [headerButtonTapped](#headerbuttontappedbutton)
  * [pushNotificationTokenUpdated](#pushnotificationtokenupdatedtoken-type-error)
  * [notificationArrived](#notificationarrivednotification-background)

---

## How to use

In order to allow both the Cordova and the LigerMobile frameworks to initialize properly, we recommend using the following template for each of your app page's Javascript:

``` javascript
//  This will be called by the included page.js as part of the LigerMobile initialization.
PAGE.hello = function() {
  		HELLO.initialize();
}

/* 
*
*	If this page will be receiving updates from a child page, you can setup the unique
*	functionality by overwriting the PAGE.childUpdates() function here.
*
*/  		
PAGE.childUpdates = function(args) {
	// Maybe for instance you want to reintialize the page.
	HELLO.initalize();
}

//  All of the code unique to the page's functionality
var HELLO = {
	initialize: function() {
		var me = this;
		
		/* 
		*
		*	All arguments that have been passed to this page are now ready to be accessed.
		*	They can be found in the PAGE.args object.  
		*
		*
		*/
		
		if(PAGE.args) {
			if("world" in PAGE.args) {
				// Call other stuff that works with world object
			}
		}
		
		$("#openPage").click(function() {
			PAGE.openPage('title of next page', 'name_of_next_page', {'here': 'arguments'}, {'here': 'options'});
		});
	}
	
	// Lots of other cool stuff...
}
```

---
	
## API

#### openPage(title, page, args, options)

Opens a new page.

iOS: Pushes a UIViewController to a UINavigationController.

* title - The title of the page (title in UINavigationBar on iOS).
* page - The page to be opened. Should not include '.html' in the name (e.g. use 'hello' instead of 'hello.html').
* args - Map of arguments that will be sent to page.
* options - Map of options that will be sent to page.

#### closePage()

Closes the currently open page.
Can't close a root page.

#### closeToPage(page)
 
Closes all pages above 'page' in the navigation stack.
Can't close a root page.

* page - The page to be displayed after the pages have been closed.

#### updateParent(args)

Sends arguments to the parent page.

* args - Map of arguments that will be sent to childUpdates in the parent page.

#### updateParentPage(page, args)

Sends arguments to the closest ancestor page that is named 'page'.

* page - The name of the ancestor page (not including yourself) you want to send the arguments to.
* args - Map of arguments that will be sent to childUpdates in the ancestor page.

#### openDialog(page, args, options)

Opens a new page as a dialog.

iOS: Presents a UIViewController.

* page - The page to be opened. Should not include '.html' in the name (e.g. use 'hello' instead of 'hello.html').
* args - Map of arguments that will be sent to page.
* options - Map of options that will be sent to page.

#### openDialogWithTitle(title, page, args, options)

Opens a new page as a dialog with a title.

iOS: Presents a UINavigationController with a page in it.

* title - The title of the page (title in UINavigationBar on iOS).
* page - The page to be opened. Should not include '.html' in the name (e.g. use 'hello' instead of 'hello.html').
* args - Map of arguments that will be sent to page.
* options - Map of options that will be sent to page.

#### closeDialog(args)

Closes an open dialog.

iOS: Dismisses the current UIViewController.

* args - Map of arguments that will be sent to closeDialogArguments in the page that opened the dialog.
  * resetApp - (true|false) If true, will reset the app when dialog is closed. Use when closing a signout page, an advertiser selection page, or other similar pages.

#### toolbar(items)

Sets the toolbar items.

* items - An array of maps, one per item in the toolbar. The keys are:
  * iconText - The text that is displayed on the toolbar for the item.
  * callback - Javascript code in a string to be executed when the item is tapped.

#### canRefresh()

Indicates whether this web view can be refreshed by the user or not.

---

## Callbacks

#### childUpdates(args)

Called on the parent or ancestor of a page that called updateParent or updateParentPage.

* args - The arguments from updateParent or updateParentPage.

#### closeDialogArguments(args)

Called when a dialog launched from the page is closed.

* args - Map of arguments from the dialog being closed.

#### onPageAppear()

Called when the page is displayed.

#### headerButtonTapped(button)

Called when any header button is tapped.

* button - Name of the button that was tapped in all lower case.

#### pushNotificationTokenUpdated(token, type, error)

If notifications has been turned on, a push notification token will be sent to the root page. If an error occured, an empty token will be sent with an error.

* token - The push notification token for this app and device.
* type - iOSDeviceToken for iOS.
* error - A text string with the error, if an error occurred.

#### notificationArrived(notification, background)

If a notification arrives when the app is running (either in the foreground or background), this function will be called. If the app is started up as a result of a notification, the notification will be included in the args for the root page under the key 'notification'.

* notification - The notification that came in as a JSON string.
* background - true if the notification arrived while the app was in the background, otherwise false.