# The built in default menu - appMenu

LigerMobile comes with a standard menu for use with **drawer**. You can use it or create your own. It's pretty easy to swap one out so don't be afraid of starting out with **appMenu* and switching later on.

The structure for the **appMenu** is specific to this implementation. If you implement your own you can use whatever format suits you as long as it can be sent as json.

While **appMenu** is a static menu you can implement your own menu and give it dynamic behavior. A menu in LigerMobile is a page like any other, so it can be implemented in either HTML or natively.

## appMenu menu format

The items (in args) consists of two arrays. The difference is how they are displayed in the menu. It's fully valid to keep the second array empty, but the first one needs at least one entry for the appMenu to work.

### First array

The first array should have objects with these keys in them:

* name - The text for your menu item.
* page - The page that the menu item should open.
* title - The title for the page when shown in the menu.
* args - An object with arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* dialog - true|false Set this to true if you want it to open as a dialog instead. If you add a _title_ a title bar will be added. Without the title no title bar will be shown.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation

### Second array

The second array should have objects with these keys in them:

* name - The text for your menu item.
* detail - A second line of text for your menu item.
* page - The page that the menu item should open.
* title - The title for the page when shown in the menu.
* args - An object with arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* dialog - true|false Set this to true if you want it to open as a dialog instead. If you add a _title_ a title bar will be added. Without the title no title bar will be shown.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation

## Example

```json
{
  "page": "appMenu",
  "accessibilityLabel": "menu",
  "args": {
    "menu": [
      [
        {
          "name": "Page tests",
          "page": "navigator",
          "accessibilityLabel": "Menu1",
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
```
