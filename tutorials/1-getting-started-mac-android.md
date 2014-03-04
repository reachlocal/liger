# Step 1: Setting up your environment

## Install Android Studio

Android Studio is a new IDE based on IntelliJ designed specifically for Android development. The easiest way to install is directly from the [Android Developer page](https://developer.android.com/sdk/installing/studio.html) as this version comes pre-installed with an SDK and will make setup easier.

Once installed, choose "Import project" and open the folder you cloned liger-android to (clone URL TBA):

![Import project](/media/tutorials/1-getting-started-mac-android/1-import-project.png)

Android Studio will likely ask how to configure gradle. Choose "Use customizable gradle wrapper."

![Select gradle type](/media/tutorials/1-getting-started-mac-android/2-select-gradle-type.png)

After opening, several background tasks will run (visible in the bottom right of the IDE). After awhile, new users will get an SDK error:

![Missing sdk platform](/media/tutorials/1-getting-started-mac-android/3-gradle-missing-sdk-platform.png)

We'll have to install tools using the SDK manager, which can be found under Tools -> Android -> SDK Manager. After opening, select the SDK tools, SFK platform tools, API 19 & 18, Support Repository, Support Library, Google Repository, and the Intel x86 Emulator.
This download will take some time.

![SDK downloads](/media/tutorials/1-getting-started-mac-android/4-sdk-download-selections.png)

Wait for the downloads to finish, then close the SDK manager. You may also need to close & reopen Android Studio to trigger detection of the new download.

After all that's settled, choose the `liger-android-bbc` build target in the drop down (upper toolbar of the IDE), then click the debug button to the right.

![Select build target](/media/tutorials/1-getting-started-mac-android/5-select-build-target.png)

A popup will appear asking where to deploy the device. Assuming you want to launch via the emulator, new users will have to add a device to emulate. Click the trippe-dot button to the right of "Android virtual device" and configure phone settings as desired - here, we added a Nexus 4.

![Choose device](/media/tutorials/1-getting-started-mac-android/6-run-choose-device.png)
![Device added](/media/tutorials/1-getting-started-mac-android/7-added-device.png)

Click OK. An emulator will launch and the Liger BBC Demo application will be installed. Launch it from the app folder on the emulator.
