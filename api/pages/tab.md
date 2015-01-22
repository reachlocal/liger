# The tabular collection page - tab

LigerMobile comes with a built-in tab page with a native look.

**tab** is usually used as the root page of the application, but it can also be opened through a menu or with the ```PAGE.openPage(...)``` or ```PAGE.openDialog(...)``` Javascript methods.

**tab** can display at most five tabs.

---

## tab arguments

* pages - An array containing a page object for each tab. It is recommended to use a **navigator** for each tab to be able to open/close more pages. The array must not be empty for **tab** to work, and the first tab is always used as the root page of **tab**.

#### Page object format

Each object in *pages* should have the following keys in them:

* title - The text that is displayed on the tab.
* page - The page that the tab should open.
* args - An object with the arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
  * icon - A filepath (relative from app.json) to an image file which is used as the icon for the tab. Recommended size is 30px by 30px for iOS.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation.

---

## tab options

* selectedImageTintColor - Color to tint the selected tab. Uses CSS color.

---

## Example

```json
{
  "page": "tab",
  "accessibilityLabel": "tab",
  "args": {
    "pages": [
      {
        "title": "Text on First Tab",
        "page": "navigator",
        "accessibilityLabel": "first",
        "args": {
          "title": "Title of First Page",
          "page": "firstPage"
        },
        "options": {
          "icon": "/assets/images/first.png"
        }
      },
      {
        "title": "Text on Second Tab",
        "page": "navigator",
        "accessibilityLabel": "second",
        "args": {
          "title": "Title of Second Page",
          "page": "secondPage"
        },
        "options": {
          "icon": "/assets/images/second.png"
        }
      },
      {
        "title": "Text on Third Tab",
        "page": "navigator",
        "accessibilityLabel": "third",
        "args": {
          "title": "Title of Third Page",
          "page": "thirdPage",
          "options": {
            "right": {"button": "test"},
            "left": {"button": "here"}
          }
        },
        "options": {
          "icon": "/assets/images/third.png"
        }
      }
    ]
  },
  "options": {
    "selectedImageTintColor": "#ff0000"
  }
}
```