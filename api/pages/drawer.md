# The slide-out collection page - drawer

LigerMobile provides a page which slides out like a drawer, hence its name.

It is not recommended to open **drawer** inside another page, as this behavior is undefined. Rather, its best use is as the root page of an application (see [app.json](../app.json.md) on how to set the root page of a LigerMobile application).

If is recommended to use **drawer** as a menu, and the argument should be a menu page (such as **appMenu**). However, you can open any page in **drawer**, not just menu pages.

---

## drawer arguments

* page - The page to be opened within drawer.
* args - An object with the arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation.

---

## drawer options

There are no options specific to this page.

---

## What is cached?

By default, **drawer** will cache a page that has been opened. This is enabled or disabled by setting a boolean value to the *cached* option for a page that is opened through **drawer**.

Imported pages and pages opened in a dialog cannot be cached.

---

## Example

```json
{
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
            },
            "options": {
              "cached": false
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
}
```