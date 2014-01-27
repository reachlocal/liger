# App.json

App.json is a [json](http://www.json.org) file that defines your application. It lives in the root of your app folder and defines things such as the root pages of your application and how it looks.

## What is in it?

### appFormatVersion

This is the version of the app.json file. If your application complains that you have the wrong version refer to this documentation for upgrade instructions. Only after you have upgraded the file should you change the version number to the most current one (make sure your copy of Liger is up to date!). So why do we have this? Simply to give you, the user of Liger, a heads up when we change the file format in some way. We might rearrange something, add something, or deprecate something old. To keep your app running as smoothly as possbile, and avoid silent faliures, Liger only accepts the proper file version and format.

### menu

Menu consists of two arrays. The difference is how they are displayed in the menu. It's fully valid to keep the second array empty, but the first one needs at least one entry for the app to work.

#### First array

The first array should have objects with these keys in them:

* name - The text for your menu
* page - The page that the menu should open
* args - An object with arguments for the page. The same type of arguments you would send in an openPage call
* dialog - true|false Set this to true if you want it to open as a dialog instead
* iconText - The character that shows up as an icon to the left of the menu choice
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation

#### Second array

The second array should have objects with these keys in them:

* name - The text for your menu
* detail - A second line of text for your menu
* page - The page that the menu should open
* args - An object with arguments for the page. The same type of arguments you would send in an openPage call
* dialog - true|false Set this to true if you want it to open as a dialog instead
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation

### Appearance

This sets a number of colors in your app. This so you can theme the Liger pieces to work well with your app. All the colors are specified the same way as [CSS colors](http://www.w3.org/Style/CSS/) are. All to improve the familiarty for those of you arriving from a strict HTML background.

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

### 4

Use CSS colors


---

[Home](/) | Up to [Web Docs](/web)
