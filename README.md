Liger Common [![Build Status](https://api.travis-ci.org/reachlocal/liger-common.png)](https://travis-ci.org/reachlocal/liger-common)

Liger iOS [![Build Status](https://api.travis-ci.org/reachlocal/liger-ios.png)](https://travis-ci.org/reachlocal/liger-ios)

#Liger

##Introduction
Liger is a lightweight open source framework that provides tools to develop hybrid apps quickly and easily. If you are looking for a framework that can help you build a hybrid app, create a prototype, or just need a stepping stone to full native app development--this is a great way to begin. 

Liger is suited for web developers and others who are not ready to learn native app development. If you know HTML, JavaScript and CSS you are in a good position to start using Liger.

While hybrid apps are no replacement for native app development, Liger addresses many of the issues with hybrid app development.

- **Native-like** - Liger blends in. Since there are multiple web views, you have access to use native transitions between them. That means a much more native feel to your web apps. 

- **Performance** - Liger is a powerful beast. Because Liger is built to use support multiple pages or web views, you can avoid memory performance pitfalls inherent in single view apps.

- **Flexibility** - Liger is nimble. He deftly switches between native and web views and can share data between them.  If you want to create native pages, no problem--Liger supports this too. 

- **Lightweight** - Liger doesn’t judge. You want to use Angular.js, go for it. CoffeeScript, Underscore, no problem. Even plain ol’ HTML, the front end is yours to do with as you please.

##What’s Inside
Liger will give you all the tools to get going.

- **Cordova** - the go to tool for accessing native device functions
- **Liger Common** - your common repo where your web app will live.
- **Liger iOS** - your iOS app.
- **Liger Android** - your android app.

##What’s Required
- An Apple computer with xcode installed (version 5 required)
- Xcode command line tools (Install via the terminal app included with your mac. At the prompt type `xcode-select --install` hit return and follow the instructions)
- Cocoapods (via terminal, type `sudo gem install cocoapods` and hit return)
- [Liger Common](https://github.com/reachlocal/liger-common)
- [Liger iOS](https://github.com/reachlocal/liger-ios) and/or [Liger Android](https://github.com/reachlocal/liger-android)

##Getting Started
Once you have cloned Liger Common and Liger iOS and/or Liger Android repositories follow the instructions below. They will help you setup your project.

###Creating Your Project###
- [Creating an iOS Project](https://github.com/reachlocal/liger/wiki/Create-iOS-app)

###Creating your App
Once your project is up and running here is how to start working with Liger. Liger-Common is where all the action is, it’s shared between your Android and iOS repos. Look for the app.json file.

> 1. In the app.json define the name and page information (hello for this example) of the page that will be the home page as the first item in the menu object.
> 2. Create an html file (hello.html) of the same name in the same directory as the app.json.
> 3. In the hello.html, include references to the included vendor files and js/pages/hello.js (this is your page's unique functionality).
>` <script type="text/javascript" src="vendor/cordova.js"></script>`
>` <script type="text/javascript" src="vendor/page.js"></script>`
>` <script type="text/javascript" src="vendor/liger.js"></script>`
>` <script type="text/javascript" src="app/js/pages/hello.js"></script>`

> 5. In the js/pages directory create a corresponding hello.js file.
> 6. In the hello.html, initialize the liger app, by calling PAGE.initialize("hello");
> 7. At this point add your html via whatever method you're most comfortable. This repo (link) shows examples using Handlebars, Angular.js, Underscore and plain HTML.
> 8. In your hello.js add any bindings, animations, etc., that bring your idea to life.

##Documentation
Looking for details on Liger’s APIs? Looking to dig deeper into Liger? 

- [app.json](https://github.com/reachlocal/liger/wiki/app.json) - This is where you define your page(s) in your app, and customize native elements (colors) of your app.
- [Creating native iOS pages](https://github.com/reachlocal/liger/wiki/Custom-iOS-pages)
- [Liger's JavaScript API](https://github.com/reachlocal/liger-common?source=cc#what-liger-provides) 
- [Structuring your JavaScript](https://github.com/reachlocal/liger-common?source=cc#how-to-setup-your-javascript)
- [Using Tests](https://github.com/reachlocal/liger-common#to-run-the-tests)  - Building with test driven development requires node.js, follow the instructions here to start building with tests.


##Resources
Helpful links to get you on your way.

- [Working with xcode Folders](http://struct.ca/2010/xcode-folder-references/) - New to using Xcode, here is a brief intro on how to import files and folders into xcode.
