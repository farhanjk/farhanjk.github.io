`On a device like Samsung Y Duos with only 160MB of internal memory, it is common that the app gets installed first time but when you reinstall the app, you get:

`Failure [INSTALL_FAILED_INSUFFICIENT_STORAGE]`

This is an annoyance when an IDE is being used to deploy and redeploy app while in development. 

Usually the IDE does the following to install the package:

`adb shell "pm install -r '/data/local/tmp/com.your.package'"`

This results in the `INSTALL_FAILED_INSUFFICIENT_STORAGE` error if the app is already installed on the device. A simple solution to this is to uninstall the app first through command line (uninstalling app does not work when using Application manager in phone's settings):

`adb shell "pm uninstall com.your.package"`

And once the app is uninstalled, then either do a command line install or let the IDE handle installation.

`adb install YOUR_APK`