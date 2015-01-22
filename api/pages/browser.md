# The in-app browser - browser

LigerMobile provides a **browser** page for viewing web links within the app, rather than within an external browser.

**browser** can be opened using Javascript with the ```PAGE.openPage(...)``` or ```PAGE.openDialog(...)``` methods.

---

## browser arguments

* link - HTTP(S) link to the webpage.
* allowZoom - (true|false) Allow or disallow zoom.

---

## browser options

There are no options specific to this page.

---

## Example

#### Javascript

```javascript
PAGE.openPage('Link', 'browser', {link: "https://github.com/reachlocal/liger/blob/master/readme.md", allowZoom: true}, {});
```

#### JSON

```json
{
  "name": "Link",
  "page": "browser",
  "accessibilityLabel": "browser",
  "args": {
    "link": "https://github.com/reachlocal/liger/blob/master/readme.md",
    "allowZoom": true
  },
  "options": {}
}
```