# App Recon: Exploring an Android APK
Remember, a packaged Android file, better known as an APK is just a zipped up collection of files and folders marked with the `.apk` extension. If an attacker is targeting your application, this is the first place they look.

### Task 1: Unzipping the APK
We will perform this lab in the Santoku Linux VM. Open up a terminal shell in the VM and unzip the DIVA .apk file to begin reverse engineering the application:

1. Make a copy of the .apk on the Desktop of the VM:
```
cp /path/to/001-Lab-Setup/DIVA-Android/diva-beta.apk ~/Desktop
```

2. Unzip the .apk into a new directory called `DIVA`. 
```
unzip diva-beta.apk -d DIVA
```

### Task 2: Inspect the AndroidManifest.xml file

Every app project must have an AndroidManifest.xml file at the root of the project source set. The manifest file describes essential information about your app to the Android build tools, the Android operating system, and Google Play. This is the first stop for many curious individuals wanting to learn more about your Android application. Let's take a look at how easy it is to read the AndroidManifest.xml file. 

On your local machine, open up Android Studio.


### Task 2: Running Strings
Strings will help us discover hardcoded credentials, URLs, keys, and more. It is a simple tool that is used as the first step in recon of an app. We will run strings on the `classes.dex` file that was produced after we unzipped the .apk. Below are some simple examples. Feel free to experiment further

```
strings classes.dex | egrep -i 'http|https'
strings classes.dex | egrep 'key'
strings classes.dex | egrep 'password'
strings classes.dex | egrep 'secret'
```

Did you find anything interesting?

### Task 3: Decompile classes.dex
We want to begin exploring our `classes.dex` file in a more human-readable format. We will use the classing Android hacking tool called `dex2jar` which is pre-installed in the Santoku VM:

In the directory you unzipped run the following command:
```
d2j-dex2jar classes.dex
```

This creates a files named `classes-dex2jar.jar` which we can then open using the GUI tool for exploring .jar files called `jd-gui`:

```
jd-gui class-dex2jar.jar`
```

Take some time to browse the classes in the application.


### Task 4: Reverse Engineering Using APKtool

`APKtool` is a tool for reverse engineering 3rd party, closed, binary Android apps. It can decode resources to nearly original form and rebuild them after making some modifications. It also makes working with an app easier because of the project like file structure and automation of some repetitive tasks like building apk, etc.

Let's run APKtool on our DVIA .apk file:

```
apktool d diva-beta.apk
```

When we inspect the output you will see 

