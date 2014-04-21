# Custom pages

## Creating your own iOS custom pages using LGRViewController

So you want to write your own LigerMobile pages in Objective-C? Then you've come to the right place! Using the standard LigerMobile page **browser** as an example we'll walk you through how it works.

This guide will assume that you are familiar with Xcode and iOS.

### Inherit from LGRViewController

The first thing you want to do is create a new **UIViewController**, name it something appropriate and then inherit from **LGRViewController** instead. This is the relevant code from **LGRBrowserViewController**:

```objective-c
	#import "LGRViewController.h"

	@interface LGRBrowserViewController : LGRViewController

	@end
```

### Page name

The next step is making sure the LigerMobile framework finds your custom page. Decide on a name and implement the **nativePage** class method. This is the string you will use in **openPage** and **openDialog** to open up your page. This so that it can be opened both from _Javascript_ and _Objective-C_. You can create and use it as a normal **UIViewController** as well as **LGRViewController** inherits from it. A nice bonus is that the functionality to open pages and dialogs comes from **LGRViewController** so if you want to open an _HTML_ page (or another custom page) from your custom page you can do so. This way your own custom pages aren't relegated to being leaves in the UI's navigational model.

Here's the relevant code from **LGRBrowserViewController**:

```objective-c
	+ (NSString*)nativePage
	{
		return @"browser";
	}
```

### Initializing your custom page

**LGRPageFactory** needs to be able to initialize your custom page properly, and that's done using the **initWithPage:title:args:** selector. It's up to you how much of the arguments are useful to you but you have to make sure that you call one of **LGRViewController**'s two init methods. If you want to use a _nib_/_xib_ file for your custom class you **initWithPage:title:args:nibName:bundle:** instead of **initWithPage:title:args:**. They both perform the same essential function, and among other things will save the page, title, and args that is later accessible through properties.

If your custom page takes arguments you can extract them here to change the behavior of your
controller, or you can use **self.args[@"key"]** to access them later on.

Here's the relevant code from **LGRBrowserViewController** with the custom init removed for clarity.

```objective-c
	- (id)initWithPage:(NSString*)page title:(NSString*)title args:(NSDictionary*)args
	{
		self = [super initWithPage:page title:title args:args nibName:@"LGRBrowserViewController" bundle:nil];
		if (self) {
			// Custom init code goes here
		}
		return self;
	}
```

### Write your new custom page!

The sky's the limit! You can add or do anything you normally can do with a **UIViewController**. If you want to embed another **UIViewController** or class inheriting from it you can do so as a child view controller. This is how we implement the HTML controller ourselves. It's also highly recommended that you use the built in methods to open and close pages and dialogs rather than using the **UIViewController**'s methods directly. This to avoid bugs when using the page inside of the LigerMobile framework.

That said, you might want to provide even more advanced functionality. If that's the case try to use the
methods in **LGRViewController** and overload them where appropriate. You can provide custom animations for a
**UINavigationController** push of a view controller this way for instance. Don't be afraid to look at LigerMobile's source code to figure this out either.

### Giving back

Feel free to contribute custom pages back to the community. Maybe in the form of a custom page cocoapod even.
That way others can include your work easily. Maybe you have a service you want other's to use, or a piece of
hardware you sell and a custom page is a great way to expose that. Or your custom page is just generally very
cool and useful! Don't forget that you can distribute pre-made HTML pages as well. Remember, everyone's invited!

## But dear LigerMobile developers, I already have a UIViewController!

Maybe it's already written, maybe you can't change it for some reason. Maybe even worse, you don't even have the source code! Is all lost? No, you are in luck! Apple provides a number of a useful dialogs and we expose them in LigerMobile. The caveat is that they have to be leaf nodes, as they don't know how to open up a new page. The good news is that it's pretty much always the case anyways.

### Show what do I do then?

You create a class that uses the **LGRImportedViewConctroller** (importing into LigerMobile) protocol:

```objective-c
	#import "LGRImportedViewController.h"

	@interface LGRMessageImported : NSObject <LGRImportedViewController>

	@end
```

And as you might have figured out we are using the iOS message controller as an example. This is included in LigerMobile so you can go look at the full source code for the details.

### Fill in the code

The next step is giving it a page name:

```objective-c
	+ (NSString*)importedPage
	{
		return @"message";
	}
```

And a way to initialize the imported page:

```objective-c
	+ (UIViewController*)controllerForImportedPage:(NSString*)page title:(NSString*)title args:(NSDictionary*)args parent:(LGRViewController*)parent
	{
		MFMessageComposeViewController *picker = [[MFMessageComposeViewController alloc] init];

		picker.recipients = [self recipientsArray:args[@"recipients"]];
		picker.subject = args[@"subject"];
		picker.body = args[@"body"];
		
		picker.delegate = parent;
		
		return picker;
	}
```

### Delegates

Something worth nothing, if you run into the same situation is this line:

```objective-c
	picker.delegate = parent;
```

**LGRMessageImported** has no idea about the callbacks for the message composer's delegate. So what I did was to add a category to **LGRViewController** so it knows how to answer the delegate callback. Take a look in _LGRViewController+MessageUI.h_. There are a number of protocols and other things added to the category on **LGRViewcontroller**, and we implement the callbacks. This way we can use the parent of our page as our delegate and react properly. And here's what we do in the callback:

```objective-c
	- (void)messageComposeViewController:(MFMessageComposeViewController *)controller didFinishWithResult:(MessageComposeResult)result
	{
		[self dismissViewControllerAnimated:YES completion:^{
			[self dialogClosed:@{@"result": [NSNumber numberWithInteger:result]}];
		}];
	}
```

When the message has been sent we dismiss the view controller, and when that has finished we send the **dialogClosed:** message with our result. This way, the parent page gets the information back in the normal LigerMobile way, and both custom pages and HTML pages know what to do. Some dialogs are going to be far more interesting, others more mundane. For a really interesting use look at the imported image dialog's callback:

```objective-c
	- (void)imagePickerController:(UIImagePickerController *)picker didFinishPickingMediaWithInfo:(NSDictionary *)info
	{
		NSString *url = [info[UIImagePickerControllerMediaURL] absoluteString];
		if (!url)
			url = [info[UIImagePickerControllerReferenceURL] absoluteString];

		if (!url)
			url = @"";

		NSDictionary *metaData = info[UIImagePickerControllerMediaMetadata];
		if (!metaData) {
			metaData = @{};
		}
		
		[self dismissViewControllerAnimated:YES completion:^{
			[self dialogClosed:@{@"MediaType": info[UIImagePickerControllerMediaType], @"URL": url, @"MetaData": metaData}];
		}];
	}
```

Here, when we close the dialog, we send back the URL for an image, with some other nice-to-have data. You can ask the user to select an image and then use that URL (due to some magic currently residing in Cordova) directly in your HTML app. That's pretty neat!
