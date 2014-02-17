# Step 1: Setting up your environment

It's time to get you set up to develop Liger iOS apps on a Mac. You can set yourself up for Android development as well, one doesn't exclude the other. If you are new to mobile development it can easily feel daunting to get to grips with new tools. We will do our best to guide you through it and show you the important bits.

# Xcode

* Make sure you have an [Apple ID](http://appleid.apple.com). Chances are good that you already have one as the one Apple account is used for all things Apple. 
* Start the App Store, search for XCode, and download XCode

![AppStore](/media/tutorials/1-getting-started-mac-ios/AppStore.png)

![AppStore](/media/tutorials/1-getting-started-mac-ios/AppStoreInstall.png)

* Enter your credentials if you haven't already

![Credentials](/media/tutorials/1-getting-started-mac-ios/AppStoreAppleID.png)

* Depending on your internet speed it can take quite a while to install Xcode
* Start Xcode, ready the license agreement and decide if you want to agree to it
* OS X will ask you for your password so it can install additional components
* Verify that you do indeed have version 5.0.2 or newer (screenshot!)

![Xcode](/media/tutorials/1-getting-started-mac-ios/Xcode.png)

* Install the command line tools. Start by starting Terminal.app and type `xcode-select --install`

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools1.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools2.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools3.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools4.png)

* If this shows up you have probably already installed the tools

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeToolsFail.png)


# Ruby

## Build in

If you don't plan on using Ruby for anything other than the tools you need for Liger you can install using the built in Ruby.

* Start terminal
* Type `gem install cocoapods`
* Type `pod setup`

## Using RVM

Link to RVM page, common with RoR developers, more advanced, tip to use .ruby-version / .ruby-gemset.
