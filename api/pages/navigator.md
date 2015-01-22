# The stack-based collection page - navigator

LigerMobile provides an easy way to navigate between pages using the **navigator**. **navigator** pushes pages onto a stack when opened and pops pages when closed. The page at the top of the stack is the one displayed on screen, and the page at the bottom of the stack is the root page of **navigator**.

A parent/ancestor page is one that is lower on the stack, and a child/decendant page is one that is higher on the stack. Pages can send arguments to their parent/ancestor using ```updateParent(...)``` and ```updateParentPage(...)```, and the callback function ```childUpdates(...)``` can be overwritten in the parent page to use those arguments and do something. Passing arguments between parent page amd child page is the primary way in which they interact with each other.

Any page on the stack of **navigator** can open a new page using ```openPage(...)```, and any page except the bottom page can close itself using ```closePage(...)```.

---

## navigator arguments

* pages - An array containing one or more page objects. If more than one page object is passed in, then the first page will be the bottom of the stack and the last page will be the top. The array must not be empty for **navigator** to work, and the first page is always used as the root page of **navigator**.

#### Page object format

Each object in *pages* should have the following keys in them:

* title - The title of the page.
* page - The page to be opened.
* args - An object with the arguments for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* options - An object with the options for the page. Same as ```openPage(...)``` and ```openDialog(...)```.
* accessibilityLabel - The accessibility label to use for testing with UIAutomation or any testing framework that uses UIAutomation.

---

## navigator options

There are no options specific to this page.

---

## Example

```json
{
  "page": "navigator",
  "accessibilityLabel": "stack",
  "args": {
    "pages": [
      {
        "title": "First Page, Bottom of Stack",
        "page": "firstPage",
        "accessibilityLabel": "firstPage",
        "args": {},
        "options": {}
      },
      {
        "title": "Second Page, Middle of Stack",
        "page": "secondPage",
        "accessibilityLabel": "secondPage",
        "args": {},
        "options": {}
      },
      {
        "title": "Third Page, Top of Stack",
        "page": "thirdPage",
        "accessibilityLabel": "thirdPage",
        "args": {},
        "options": {}
      }
    ]
  }
}
```