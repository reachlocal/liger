# Step 3: Adding web content

## Editing web content

Once your project is up and running here is how to begin working with LigerMobile. Liger-Common is where all the action is, it’s shared between your Android and iOS repos. Look for the app.json file.

1. In the app.json define the name and page information (hello for this example) of the page that will be the home page as the first item in the menu object.
2. Create an html file (hello.html) of the same name in the same directory as the app.json.
3. In the hello.html, include references to the included vendor files and js/pages/hello.js (this is your page's unique functionality).
` <script type="text/javascript" src="vendor/cordova.js"></script>`
` <script type="text/javascript" src="vendor/page.js"></script>`
` <script type="text/javascript" src="vendor/liger.js"></script>`
` <script type="text/javascript" src="app/js/pages/hello.js"></script>`

5. In the js/pages directory create a corresponding hello.js file.
6. In the hello.html, initialize the LigerMobile app, by calling PAGE.initialize("hello");
7. At this point add your html via whatever method you're most comfortable. This repo (link) shows examples using Handlebars, Angular.js, Underscore and plain HTML.
8. In your hello.js add any bindings, animations, etc., that bring your idea to life.
