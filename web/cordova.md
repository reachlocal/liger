## Cordova

LigerMobile uses [Cordova](http://cordova.apache.org) internally. While you shouldn't make use of the LigerMobile Cordova plug-in directly yourself, as there's no guarantees LigerMobile will include Cordova at all in the future, you might want to use a different Cordova plug-in. Here lies Dragons. This is truly an advanced topic so first see if any of these alternatives would work for you.

Look to see if HTML offers what you want. Over the recent years HTML5 has grown to support more and more types of functionality. <audio> and <video> tags are an example of this. Hit those search engines and forums! This is the easiest way to solve your issues.

Next down the road look at writing a native Page. Look at the forums to see if someone else already has, and if not write your own. That might not be a reasonable proposition for you, but this is a sure fire way to add that special feature you so genuinely want to grace your users with. An option is to find someone else to help you, which also might be possible through the forums. Don't forget to look for the native support LigerMobile comes with out of the box, such as an in app browser, email and messaging dialogs.

Next you might attempt a Cordova plug-in. But before you do, make sure it's reasonably compatible with LigerMobile. Many are not. Again the forums can be your friend here. If you do find a plug-in and it's your only option, here's some quick pointers.

* The Cordova podspec includes subspecs for their plug-ins.
* If you can't find it as a pod you need to add the code into your own project.
* Don't forget to update your config.xml to include the plug-ins you have added.
* You need to create a **cordova_plugins.js** file and include it in your project somehow.
* You need to include the js for the plug-ins.
