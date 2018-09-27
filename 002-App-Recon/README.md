# App Recon: Exploring an Android APK
A packaged Android file, better known as an APK is just a zipped up collection of files and folders marked with the `.apk` extension. If an attacker is targeting your application, this is the first place they will look.

### Task 1: Inspect the AndroidManifest.xml file

Every app project must have an AndroidManifest.xml file at the root of the project source set. The manifest file describes essential information about your app to the Android build tools, the Android operating system, and Google Play. This is the first stop for many curious individuals wanting to learn more about your Android application. Let's take a look at how easy it is to read the AndroidManifest.xml file. 

On your local machine, open up Android Studio. We will use the built in `apkanalyzer` tool to investigate our the DIVA APK file. When plugins are enabled in Android Studio, it is simple to analyze an APK file but navigating to `Build -> Analyze APK`:

![Analyze APK](../images/analyze_apk.png?raw=true "Analyze APK")

Now, open up the `diva-beta.apk` file located in the `001-Lab-Setup/DIVA-Android` directory.

## Discussion Questions
What permissions does this app request?

How many methods does the app itself define?


### Task 2: Unzipping the APK
We will perform this task in the Santoku Linux VM. Open up a terminal shell in the VM and unzip the DIVA .apk file to begin reverse engineering the application:

1. Make a copy of the .apk on the Desktop of the VM:
```
cp /path/to/001-Lab-Setup/DIVA-Android/diva-beta.apk ~/Desktop
```

2. Unzip the .apk into a new directory called `DIVA`. 
```
unzip diva-beta.apk -d DIVA
```

Browse the contents of the unzipped apk.

### Task 3: Unzip the Additional APKs
In the `/other_apps` directory, you will find a few older APKs. Unzip them and see if you can find anything interesting. Note - these are chosen at random and may or may not have issues or vulnerabilities. 


