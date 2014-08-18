# Native pages in LigerMobile

You can write your own native pages in Liger, that can be opened from an HTML page or visa versa. LigerMobile itself provides a number of native pages already which lowers the neccessity to write native pages. Many apps can get away without writing any at all. Below is a list of what LigerMobile supplies. If you write your own native pages they can be shared with others, and if you feel its quite generic do consider asking to have it added to LigerMobile itself.

## Collection pages

What makes a collection page different from other pages is that it contains and manages other pages. When you call ```openPage(...)``` it's a collection page that opens it for you. The collection page you most likely will be using the most is the ```navigator``` which implements the commonly used UI of pushing (```openPage(...)```)and popping (using the back button or ```closePage(...)```) pages.

| Page name                       | iOS | Android | short description                                                |
| ------------------------------- | --: | ------: | ---------------------------------------------------------------- |
| [drawer](pages/drawer.md)       | ✓   | ✗       | Menu on the left side collection. Takes a menu as an argument.   |
| [navigator](pages/navigator.md) | ✓   | ✗       | Basic stack navigation. Push / pop pages.                        |
| [tab](pages/tab.md)             | ✓   | ✗       | Basic tab page with native look.                                 |

## Generic pages

LigerMobile also comes with precreated single pages. These can be opened as either a page in a collection or in a dialog.


| Page name                   | iOS | Android | short description                                           |
| --------------------------- | --: | ------: | ------------------------------------------------------------|
| [appMenu](pages/appMenu.md) | ✓   | ✗       | Basic menu. Used in conjunction with a drawer               | 
| [browser](pages/browser.md) | ✓   | ✗       | Simple in app browser, if you don't want to leave your app. |

## Imported pages

Imported pages are leaf node (navigationally) pages. A lot of the time they aren't pages at all, but pure native code. An example is the email composer in iOS. We use the native view controller and give access to it from the ```openDialog(...)``` interface. This gives us a generic interface to access already existing functionality even when that functionality for technical reasons can't act as a page.

Imported pages are more often than not only available via ```openDialog(...)``` and not ```openPage(...)``` on iOS for technical reasons.

| Imported page name                    | iOS | Android | short description                     |
| ------------------------------------- | --: | ------: | ------------------------------------- |
| [email](pages/email.md)               | ✓   | ✗       | For sending emails.                   |
| [facebook](pages/facebook.md)         | ✓   | ✗       | For composing facebook messages.      |
| [image](pages/image.md)               | ✓   | ✗       | Getting an image.                     |
| [message](pages/message.md)           | ✓   | ✗       | Sending a message (text/iMesssage).   |
| [sinaweibo](pages/sinaweibo.md)       | ✓   | ✗       | For composing sina weibo messages.    |
| [tencentweibo](pages/tencentweibo.md) | ✓   | ✗       | For composing tencent weibo messages. |
| [twitter](pages/twitter.md)           | ✓   | ✗       | For composing twitter messages.       |
