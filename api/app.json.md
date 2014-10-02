# app.json

app.json is a [JSON](http://www.json.org) file that defines your application. It lives in the root of your app folder and defines things such as the root page of your application and how it looks. A basic app.json file can be found in [LigerMobile Common](https://github.com/reachlocal/liger-common), and a more advanced, if a bit contrived, version can be found in [LigerMobile iOS's test app](https://github.com/reachlocal/liger-ios/tree/master/LigerTestApp).

---

## What is in it?

#### appFormatVersion

This is the version of the app.json file. If your application complains that you have the wrong version, refer to [here](#upgrading-appformatversion) for upgrade instructions. Only after you have upgraded the file should you change the version number to the most current one (make sure your copy of LigerMobile is up to date, and don't use pre-release versions). So why do we have this? Simply to give you, the user of LigerMobile, a heads up when we change the file format in some way. We might rearrange something, add something, or deprecate something old. To keep your app running as smoothly as possbile and to avoid silent failures, LigerMobile only accepts the proper file version and format.

#### notifications

Set to true if you want to turn on push notifications, false otherwise. If the key is missing, it will be interpreted as false, but it's recommended to add it anyways for future compatibility. Only available for iOS.

#### rootPage

This will often be a **drawer** or **navigator** but can be any page, even a single page. It's quite common that you will open several pages via the args to the root page, like when you are using a **tab** page or a **navigator** stack.

* page - The first page in your app. Should not include '.html' in the name (e.g. use 'hello' instead of 'hello.html').
* args - An object with the arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation.

#### appearance

This sets a number of colors in your app, allowing you to set the theme for the LigerMobile pieces. All the colors are specified in the same way [CSS colors](http://www.w3.org/Style/CSS/) are.

You can skip any and all values (they all have defaults), and some override others, so be careful. Each operating system takes different options:

###### iOS7

* statusBar - light|dark The color of your iOS status bar.
* statusBarDialog - light|dark The color of your iOS status bar in dialogs.
* barColor - The navigation bar color.
* barTint - The tint of the navigation bar (barColor overrides this and sets a solid color).
* tint - The tint for the whole app.
* barText - Text color on the navigation bar.
* webBackground - The background color for web view based pages.
* menuBackground - The background color of the menu.
* menu1Text - Text color for the first array of menu items.
* menu2Text - Text color for the second array of menu items.
* menuSelected - Text color of the selected menu item.

###### iOS

* barColor - The color of the navigation bar.
* barText - The color of the text on the navigation bar.
* webBackground - The background color for web view based pages.
* menuBackground - The background color of the menu.
* menu1Text - Text color for the first array of menu items.
* menu2Text - Text color for the second array of menu items.
* menuSelected - Text color of the selected menu item.

###### Android

* Appearance options are currently unavailable in Liger Android.

---

## Upgrading appFormatVersion

#### 6

* The rootpage no longer refers to the menu but any page in the system. This means you can use a **tab** page or a **navigator** page as the root page now. To use a menu as the root page, you will need to use a **drawer** with a menu in its args. Don't forget to add a **navigator** for each menu alternative where you used to have a navigational interface in the past.

#### 5

* Menu has been replaced by rootPage. The args that goes into root page for appMenu is the same as menu, with the addition of the title key and the removal of the iconText.
* notifications added.

#### 4

* Use CSS colors.

---

## Example

```json
{
  "appFormatVersion": 6,
  "notifications": false,
  "rootPage": {
    "page": "drawer",
    "accessibilityLabel": "drawer",
    "args": {
      "page": "appMenu",
      "accessibilityLabel": "menu",
      "args": {
        "menu": [
          [
            {
              "name": "Page Test",
              "page": "navigator",
              "accessibilityLabel": "test",
              "args": {
                "title": "First Page",
                "page": "firstPage",
                "accessibilityLabel": "firstPage",
                "args": {}
              }
            }
          ],
          [
            {
              "name": "Mail us",
              "detail": "We like mail",
              "page": "email",
              "accessibilityLabel": "emailDialog",
              "dialog": true,
              "args": {
                "subject": "Liger",
                "body": "Hi,\n\nI would like to tell you how much I like Liger.\n\n//Me",
                "toRecipients": "liger@example.com",
                "html": false
              }
            }
          ]
        ]
      }
    }
  },
  "appearance": {
    "iOS": {
      "barColor": "",
      "barText": "",
      "webBackground": "",
      "menuBackground": "",
      "menu1Text": "",
      "menu2Text": "",
      "menuSelected": ""
    },
    "iOS7": {
      "statusBar": "",
      "statusBarDialog": "",
      "barColor": "",
      "barTint": "",
      "tint": "",
      "barText": "",
      "webBackground": "",
      "menuBackground": "",
      "menu1Text": "",
      "menu2Text": "",
      "menuSelected": ""
    }
  }
}
```