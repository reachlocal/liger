# Step 4: Creating a LigerMobile iOS App

## Create a project

Open XCode and create a new project.

![Screenshot](/media/tutorial/ios/1-create-empty-project/1-new-xcode.png)

For project type, choose an Empty iOS Application.

![Screenshot](/media/tutorial/ios/1-create-empty-project/2-empty-app.png)

At minimum, give your product:

* A name (This is the name of your app. It's displayed on the device and in the App Store.)
* A Company Identifier (Combined with the app name, this forms a unique ID used for certificates)
* A three letter all uppercase Class Prefix (prevents namespace collisions with Apple's frameworks and third party projects)

![Screenshot](/media/tutorial/ios/1-create-empty-project/3-project-options.png)

Create the project.

![Screenshot](/media/tutorial/ios/1-create-empty-project/4-create-project.png)
![Screenshot](/media/tutorial/ios/1-create-empty-project/5-project-screen.png)

You should now close the project by pressing the red close button in the top left corner of the Xcode window. This will be the last time you open the project file directly.

## Create a Podfile

If you don't already have a Podfile create one by running this in a terminal:

```bash
cd your_project_folder
pod init
```

Open the Podfile you just created and add in LigerMobile:

```ruby
# Uncomment this line to define a global platform for your project
# platform :ios, "6.0"

target "ExampleIOS" do
    pod 'LigerMobile', '0.1.1'
end

target "ExampleIOSTests" do

end
```

### Install the pods

Time to install your pods:

```bash
pod install
```

This creates a workspace and installs all the pods in your Podfile as well as any dependencies.

## Open the Workspace

Open up your *xcworkspace*. It should be named something similar to ExampleIOS.xcworkspace. As mentioned previously you should not open the project file. Both your project and the pod project are included in the workspace, and without the pods your app won't work.

## Using LigerMobile's app delegate

Open up your project's **main.m**. You can do this either by selecting it in the list of files on the left (Hint: you can filter file names at the bottom of the list) or press **shift+command+o** and type 'main.m'. Working with large code bases it can be sometimes be difficult to find files and **shift+command+o** can make your life easier.

In the main.m file there's two things we need to do:

* Add in an import for _LGRAppDelegate.h_ near the top of your file.
* Replace the name of your AppDelegete with LGRAppDelegate. (Hint: UIApplicationMain(argc, argv, nil, NSStringFromClass([**AppDelegate** class]));)

You should start out with something like this:

```objective-c
//
//  main.m
//  ExampleIOS
//

#import <UIKit/UIKit.h>
#import "AppDelegate.h"

int main(int argc, char * argv[])
{
    @autoreleasepool {
        return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
    }
}
```

And when you are done it should look something like this:

```objective-c
//
//  main.m
//  ExampleIOS
//

#import <UIKit/UIKit.h>

#import "AppDelegate.h"
#import "LGRAppDelegate.h"

int main(int argc, char * argv[])
{
    @autoreleasepool {
        return UIApplicationMain(argc, argv, nil, NSStringFromClass([LGRAppDelegate class]));
    }
}
```

![Screenshot](/media/tutorial/ios/2-app-delegate/1-app-delegate.png)


## Add config.xml

LigerMobile is currently using Cordova to send messages between the web views and the native portions. Cordova is included as a dependency in the LigerMobile cocoapod so you will get the same version as we have. You do on the other hand have to supply a *config.xml* file. Using this as a template save it as a file named *config.xml* and include it in your project.

First, right-click your ExampleiOS project on the left-hand side and add a file:

![Screenshot](/media/tutorial/ios/3-config-xml/0-add-new-file.png)

For file type, choose Empty:

![Screenshot](/media/tutorial/ios/3-config-xml/1-empty-file.png)

Save the file as `config.xml` and ensure the ExampleIOS group & target is selected:

![Screenshot](/media/tutorial/ios/3-config-xml/2-config-xml.png)

Add the following content:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<widget xmlns     = "http://www.w3.org/ns/widgets"
        xmlns:cdv = "http://cordova.apache.org/ns/1.0"
        id        = "io.cordova.yourfancyapp"
        version   = "1.0.0">
    <name>Your fancy app</name>

    <description>
        Description of your fancy app
    </description>

    <author href="http://yourfancycompany.com" email="">
        You
    </author>

    <access origin="*" />
    <preference name="fullscreen" value="false" />
    <preference name="KeyboardDisplayRequiresUserAction" value="false" />
    <preference name="SuppressesIncrementalRendering" value="false" />
    <preference name="webviewbounce" value="true" />
    <preference name="UIWebViewBounce" value="true" />
    <preference name="TopActivityIndicator" value="gray" />
    <preference name="EnableLocation" value="false" />
    <preference name="EnableViewportScale" value="false" />
    <preference name="AutoHideSplashScreen" value="true" />
    <preference name="ShowSplashScreenSpinner" value="true" />
    <preference name="FadeSplashScreen" value="true" />
    <preference name="FadeSplashScreenDuration" value="2" />
    <preference name="MediaPlaybackRequiresUserAction" value="false" />
    <preference name="AllowInlineMediaPlayback" value="true" />
    <preference name="BackupWebStorage" value="cloud" />

    <plugins>
        <feature name="Liger">
            <param name="ios-package" value="LGRLiger" />
            <param name="android-package" value="com.reachlocal.liger.LigerPlugin" />
        </feature>
    </plugins>

</widget>
```

## Add the app folder

The HTML part of your app lives in a folder called _app_. What we need to do is to create that folder on disk and import it into Xcode so it moves those files into your app when it's compiled.

A good starting point for your app is using the app folder from [Liger common](https://github.com/reachlocal/liger-common/). It contains the necessary files for LigerMobile as well as a simple hello world page to start from. Download or clone the repo from [Github](https://github.com/reachlocal/liger-common/) and copy the app folder into your project folder.

Right click on your project and select "Add Files…".

![Screenshot](/media/tutorial/ios/4-add-files/1-add-files.png)

Find and select the app folder and add the files.
Make sure you have selected the right options for Destination and Folders.

![Screenshot](/media/tutorial/ios/4-add-files/2-complete.png)

The next step is to copy the supplied cordova.js from the Pod to your app folder. I found mine under _Pods/Cordova/CordovaLib/cordova.js_ but YMMV. Copy _cordova.js_ to _app/vendor/cordova.js_.

```bash
cp Pods/Cordova/CordovaLib/cordova.js app/vendor/
```

Now you should have a skeleton hello world app.
To summarize:

1. Create app folder
1. Copy the template app from LigerMobile Common
1. Copy cordova.js to app/vendor

## Run the app

If all went well you should be able to press the big play button in the top left (or just press *cmd-r*, it's a well worth it to remember shortcut) and run the app!

This should start the iPhone Simulator, install your app, and start it.

![Screenshot](/media/tutorial/ios/5-start-simulator/1.simulator.png)

If the app doesn't start as it should, make sure you have an iPhone Simulator selected. In the menu just next to the start and stop buttons select a simulator.

![Screenshot](/media/tutorial/ios/5-start-simulator/2-select-simulator.png)

If you have set up your iOS device for development you can hook it up with a cable, select iOS as the target, and press the play button. This will install and start the app on your device.

Tip, if your html/css/js changes doesn't seem to take effect, try cleaning the project (under the Product menu, for a deeper clean press option before selecting clean) and run it again. This seems to be an Xcode related issue and we are hoping Apple will fix it in a future release.
