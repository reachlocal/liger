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
* Verify that you do indeed have version 5.0.2 or newer by opening the about window. Liger will *not* work with older versions of Xcode

![Xcode](/media/tutorials/1-getting-started-mac-ios/Xcode.png)

* Install the command line tools. Start by starting Terminal.app and type `xcode-select --install`

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools1.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools2.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools3.png)

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeTools4.png)

* If this shows up you have probably already installed the tools

![Xcode](/media/tutorials/1-getting-started-mac-ios/XcodeToolsFail.png)


# Ruby and Cocoapods

It's recommended to keep up to date with [Cocoapods](http://cocoapods.org) at all times. Make it part of your routine to keep it updated.

## Option 1: Build in

If you don't plan on using Ruby for anything other than the tools you need for Liger you can install using the built in Ruby.

* Start terminal
* Type `sudo gem install cocoapods`
* OS X is going to ask for your account's password so it can install the gem as root using [sudo](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/sudo.8.html)
* You might be asked to overwrite certain files, only do this is if you feel comfortable about doing that. If not option 2 might be for you.
* Type `pod setup` in your Terminal window to set up cocoapods

## Option 2: Using RVM

Using a version manager for Ruby is more involved for a beginner but it has a lot of advantages. Another upside is that there is a wealth of information about RVM online. It can be quite helpful to make use of the [.ruby-version and .ruby-gemset](http://rvm.io/workflow/projects) files.

* [Install RVM](http://rvm.io)
* Install CocoaPods `gem install cocoapods` (using [gemsets](http://rvm.io/gemsets/) you get more control of what you install)
* Type `pod setup` in your Terminal window to set up cocoapods