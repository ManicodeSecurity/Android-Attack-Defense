# Lab Setup
The goal of this lab is to successfully prepare your environment for the remainder of the labs. We will be using a variety of technologies including:

### Requirements
- VirtualBox
- Santoku Linux Virtual Machine
- Android Studio installed on your local machine

### Task 1: Clone This Repository
On your local machine in an easy-to-find location (such as the Desktop) run the following command:
```
git clone https://github.com/ManicodeSecurity/Android-Attack-Defense
```

### Task 2: Run DIVA in Android Emulator
[Damn Insecure and Vulnerable App (for Android)](https://github.com/payatu/diva-android) is an intentionally insecure Android application built to help students and researchers learn about Android security in a legal environment. It was built by [payatu](https://github.com/payatu) as free and open source software. We will use DIVA extensively throughout the course. 

The APK can be found in the `DIVA-Android` directory.

We will first load the `.apk` file using the command-line utility, `adb`.

1. Create a new Android Virtual Device (AVD)
Open up Android Studio and click `Tools` then `AVD Manager`
![AVD Manager](../images/avd_manager.png?raw=true "AVD Manager")

2. In the AVD Manager page, click `Create Virtual Device`:
 `Create New Device`
![Create New Device](../images/Create_New_Device.png?raw=true "Create New Device")

3. We will create a Pixel device running Android Oreo. Select `Pixel` from the list of hardware:
`Pixel`
![Pixel](../images/Pixel_Hardware.png?raw=true "Pixel Hardware")

4. Now we will download Android Oreo API 26 to run on the Pixel Emulator:
`Oreo`
![Oreo](../images/Oreo_API_26.png?raw=true "Oreo")

When it is done downloading select Oreo with API 26 and click `Next`. On the final screen leave everything as default except for the name of the AVD. Please change it to `Manicode-Mobile-Training`.

`AVD Name`
![AVD Name](../images/AVD-Name.png?raw=true "AVD Name")

5. Click `Finish` and we will now have the AVD available to run in the emulator. 

`AVD List`
![AVD Manager](../images/AVD_List.png?raw=true "AVD List")

6. To launch the Emulator, click the green "Play" button to the right of the AVD named `Manicode-Mobile-Training` in the AVD list. The Emulator should now be running.

### Task 3: Sideload the .apk in the Emulator   

We will use the built-in Android tool called Android Debug Bridge (`adb`) to load our DIVA .apk file into our emulated Pixel device.

1. We first need to find where the `adb` binary is installed. If you are running OSX, `adb` can often be found in the ~/Library/Android/sdk/platform-tools` directory. 

You can also use Android Studio to find out where adb is located by navigating to `Tools` -> `SDK Manager`. The local SDK path be in at the top of the screen. The `platform-tools` directory can be found in this directory.

`adb Location`
![adb Location](../images/adb_location.png?raw=true "adb Location")

2. Now we load the .apk file into our running emulated device using `adb`. First, navigate to the directory where `adb` is located and run the following command (your path may differ):

First, make sure the `adb` can communicate with your emulator:
```
adb devices 
```
The output should look like this:

`adb devices`![adb devices](../images/adb_devices.png?raw=true "adb devices")

```
./adb install ~/Desktop/Android-Attack-Defense/001-Lab-Setup/DIVA-Android/diva-beta.apk
```

3. Open up the emulator and you will see the DIVA is successfully installed!

`Emulator`
![Emulator](../images/emulator.png?raw=true "Emulator")

### Task 3: Santoku Linux Setup
[Santoku Linux](https://santoku-linux.com/) is an open-source virtual machine that comes pre-installed with a number of useful tools needed for mobile security testing, malware analysis, and mobile forensics. 

If you have not already downloaded the .ISO file, please do so now. 

Please follow the directions outlined in the official [Santoku Linux Documentation](https://santoku-linux.com/howto/installing-santoku/installing-santoku-in-a-virtual-machine/) to complete the setup in VirtualBox.

*! Important !* Please ensure VirtualBox Guest additions is installed per the instructions.

### Task 5: Install Docker in the VM
We will need to use [Docker](https://www.docker.com/) to run some tools in our VM. Below is how we install it in this Ubuntu VM:


```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install docker-ce
```

Ensure Docker is installed and running:
```
sudo docker images
```

### Task 6: Clone This Repo in the VM

To avoid setting up shared folders in VirtualBox, we will just simply clone the repo in the Santoku VM. Open a terminal in the VM and run the following commands:

```
cd ~/Desktop

git clone https://github.com/ManicodeSecurity/iOS-Attack-Defense
```




