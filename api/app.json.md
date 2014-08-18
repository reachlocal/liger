# App.json

App.json is a [json](http://www.json.org) file that defines your application. It lives in the root of your app folder and defines things such as the root pages of your application and how it looks. A basic app.json file can be found in [LigerMobile Common](https://github.com/reachlocal/liger-common) and a more advanced, if a bit contrived, can be found int [LigerMobile iOS's test app](https://github.com/reachlocal/liger-ios/tree/master/LigerTestApp).

## What is in it?

### appFormatVersion

This is the version of the app.json file. If your application complains that you have the wrong version refer to this documentation for upgrade instructions. Only after you have upgraded the file should you change the version number to the most current one (make sure your copy of LigerMobile is up to date! But don't use pre-release versions.). So why do we have this? Simply to give you, the user of LigerMobile, a heads up when we change the file format in some way. We might rearrange something, add something, or deprecate something old. To keep your app running as smoothly as possbile, and avoid silent faliures, LigerMobile only accepts the proper file version and format.

### notifications

true if you want to turn on push notifications, false if not. If the key is missing it will be interpreted as false for now, but it's recommended to add it anyways for future compatibility. Only available for iOS.

### rootPage

This will often be a **drawer** or **navigator**, but can be any page, even a single page. It's quite common that you will open several pages via the args to the root page. For instance a menu, a tab page, or a navigational interface with a rootPage itself.

* page - The name of the first page in your app.
* args - Any arguments for your first page.
* options - Any options you want to send to the first page.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation

### Appearance

This sets a number of colors in your app. This so you can theme the LigerMobile pieces to work well with your app. All the colors are specified the same way as [CSS colors](http://www.w3.org/Style/CSS/) are. All to improve the familiarty for those of you arriving from a strict HTML background.

You can skip any and all values (they all have defaults) and some override others so be careful.

#### iOS7

* statusBar - light|dark The color of your iOS status bar
* statusBarDialog - light|dark The color of your iOS status bar in dialogs
* barColor - The navigation bar color
* barTint - The tint of the navigation bar (barColor overrides this and sets a solid color)
* tint - The tint for the whole app
* barText - Text color on the navigation bar
* webBackground - The background color for web view based pages
* menuBackground - The background color of the menu
* menu1Text - Text color for the first array of menu items
* menu2Text - Text color for the second array of menu items
* menuSelected - Text color of the selected menu item

#### iOS

* barColor - The color of the navigation bar
* barText - The color of the text on the navigation bar
* webBackground - The background color for web view based pages
* menuBackground - The background color of the menu
* menu1Text - Text color for the first array of menu items
* menu2Text - Text color for the second array of menu items
* menuSelected - Text color of the selected menu item

#### Android


## Upgrading to version

### 6

The rootpage no longer referes to the menu but any page in the system. To convert a version 5 app.json you would need to use a **drawer** with a menu in it's args and don't forget to add a **navigator** for each menu alternative where you used to have a navigational interface in the past.

### 5

Menu has been replaced by rootPage. The args that goes into root page for appMenu is the same as menu, with the addition of the title key and the removal of the iconText.

notifications added.

### 4

Use CSS colors
