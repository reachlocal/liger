# Xcode

[Apple does document](https://developer.apple.com/library/ios/recipes/xcode_help-structure_navigator/articles/Adding_an_Existing_File_or_Folder.html) how you import files and folders into Xcode. This often isn't enough to get people going though and I've noticed that one of the biggest issues beginners have with Xcode is how this works. As LigerMobile is all about making things easier to do and understand we'll present a little tutorial that hopefully can shed some light on this the darkest of mysteries. I like to call it, yellow and blue folders.

# Xcode file structure

The project structure is not dictated by the folder structure on disk. This is often were trouble begins. The structure Xcode maintains are called groups. They are represented by yellow folders in the UI. You can have a flat folder structure on disk and use groups to, well, group your files in the UI. You can think of them as an unordered list in HTML with different levels, all with anchors whose hrefs points to a flat structure.

This can seem strange at first, as it would seem easier to just copy the structure on disk, and that is how a lot of IDEs/text editors do it today. Especially for certain types of programming languages. The upside is that it's more powerful. Understanding how it works is key to avoid frustration.

# How to add

You can add files or folders in several ways. Either from the File menu, by dragging them in, or by using the right click menu. They all have their quirks but if you don't already have a favorite I recommend right clicking like in our [tutorial for creating an iOS app](https://github.com/reachlocal/liger/blob/master/tutorials/4-ios-skeleton.md):

![Screenshot](/media/ios/AddFiles.png)

This way you can select which group you want to add your file or folders to, and it's not as fidgety as drag and drop.

# What do the add options mean to me?

![Screenshot](/media/ios/AddConfig.png)

## Copy items into destination group's folder (if needed)

This is kind of an advanced feature. What happens depends on if the files already are were you expect them to be or not. Checking this box is usually the easiest thing to do. If your files were already in a folder structure inside of your project they just stay there, but if there are anywhere else they will be copied into the project where Xcode expects them to be.

But not checking this you can reference to files or folders outside of your project. If you need this feature you will be very happy it's there. Feel free to play around with it in a dummy project if you ever find the need to use it to get a feel for how it works. It can be a good alternative to soft links when dealing with version control as several of those tools tend to break when trying to use soft links.

## Create groups for any added folders

If you add a file it will end up the group you right clicked on earlier. The yellow type of folder icon. But if you add a folder (from disk), it will add all the files in that folder, creating a group for any folders inside of it (and so on). This is very handy when importing many files at once.

Any files added will also automatically be added to the build settings for that project. So if you add a .m file (Objective-C implementation file) it will be compiled by the compiler and the result will be linked into the binary.

## Create folder references for any added folders

Instead of adding in the folder (and subfolders) as groups you will create a so called folder reference. This will create a blue folder icon in your project. This is like a portal into the filesystem. If you add a file to the filesystem it will be included, same thing if you delete it. You can add and remove subfolders as well. All will be copied over into the app when you build it, just as it looked on disk.

Caveat. The files will only be copied, not processed or compiled in any way. Do not try to use this as a "work around" to "just using the filesystem". In fact avoid this whole option unless you have a specific reason to use it.

# For those using LigerMobile

We add the app folder as a folder reference, a blue folder, as what we want in this case is that folder and everything in it, subfolders and all. This is because this is our HTML based app and we to preserve the folder structure. This means you can edit the content of this folder with your favorite text editor and add/remove subfolders and files at your hearts content. LigerMobile will look in this folder to find all the HTML app files.

Tip: Sometimes Xcode doesn't pick up on changes in blue folders (no idea why) and what we've found to work is to clean the app before you run it. Remember that the files you edit gets copied into the .app and it's the copies the app uses, so it has to be copied over (which is done by building the app).

# Is there a way to clean things up?

If you primarily are going to do HTML work you will more than likely not touch anything outside of the app folder after you are done setting up the app. But if that's not the case and you add in Objective-C code I have a little tip for you. To clean my group structure up I sometimes do this:

1. Select all the files and press delete
1. Make sure you only remove the references as we still want the files
1. Rearrange all the files on disk
1. Add the files again by adding the folder containing all the subfolders and files

This adds them back into the build in the project, and the groups now mimic how they look on disk. Like the smell of fresh coffee in the morning:)

A smaller tip is that if you right click on a group you can sort the items in it, as you can order them any way you like. I tend to like alphabetical though:)

---

[Home](/) | Up to [iOS Docs](/ios)
