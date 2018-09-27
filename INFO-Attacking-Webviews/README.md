2. In the same way we loaded the DIVA app in 001-Lab-Setup, we need to load the .apk file into our running emulated device using `adb`. First, navigate to the directory where `adb` is located and run the following command (your path may differ):

First, make sure the `adb` can communicate with your emulator:
```
adb devices 
```
The output should look like this:

![adb devices](../images/adb_devices.png?raw=true "adb devices")

```

```