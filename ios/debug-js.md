# Debugging Javascript with Safari and the iPhoneSimulator

Now that you're creating code in LigerMobile, you're going to need to lift the hood every once in a while and take a look at the details of the running code. Safari developer tools to the rescue!

# Get the Develop menu
1. Open Safari on your desktop. I know... you're now saying, "Wait, I want to debug the code running in the simulator, don't you want me to open that Safari?" No, you'll use safari on your desktop to remotely connect to the safari instance running in the simulator.
1. Open Safari's preferences (cmd+,) and select the advanced tab
   ![Screenshot](/media/ios/debug-js/prefs0.png)
1. Make sure "Show Develop menu in menu bar" is selected at the bottom of the dialog
   ![Screenshot](/media/ios/debug-js/prefs1.png)
1. The Develop menu should be visible in Safari
   ![Screenshot](/media/ios/debug-js/menu.png)

# Use the Develop menu
1. Open Safari
1. It can get cluttered with a lot of Safari windows open on the screen. You can hide or minimize them if you want to, or close them outright. The only thing you do need access to is the Develop menu
1. Run your project's simulator from X-code
1. Command-tab to Safari
1. Select the Develop menu
1. Select "iPhone Simulator" on the menu and a fly-out menu shows on the right
   ![Screenshot](/media/ios/debug-js/dev_menu0.png)
1. Select your page from the fly-out menu
   ![Screenshot](/media/ios/debug-js/dev_menu1.png)

# Debug your code
1. Click the "Debugger" button
1. Set a breakpoint on a line you want to inspect
   ![Screenshot](/media/ios/debug-js/set_breakpoint.png)
1. Click the "Console" button
1. At the bottom of the console, type the code to initialize your page, e.g. `PAGE.initialize('hello')`, where 'hello' can be replaced by the name of the javascript class for the page you want to initialize. I initalized hello.js for my hello.html page.
   ![Screenshot](/media/ios/debug-js/initialize_page_from_console.png)
1. And it should hit your breakpoint.
   ![Screenshot](/media/ios/debug-js/hit_breakpoint.png)

# Tips and tricks

You need to attach the debugger after you have loaded the page and this can make it difficult to debug anything that happens in the initialization part of your page. You can either rerun the initialization or temporarily remove it from your html and just run it in the console of the debugger. The code you would be looking for is something like this:

```html
    <script>
        PAGE.initialize("nameOfYourPage");
    </script>
```


---

[Home](/) | Up to [iOS Docs](/ios)
