
Start Android Studio
1. In the terminal elevate privilages to root using the command `sudo su` and enter your password
2. In Linux, we will need to start Android Studio using the following commands in your terminal:
```
cd /opt/android-studio/bin
./studio.sh
```

To view the InsecureBank app in the emulator do the following:

1. Follow the steps in the startup wizard to create a blank project using Android Studio
2. Once the Project is ready use the shortcut `ctrl+shift+a`  and search for AVD Manager.
3. Choose `Oreo API 27` as our system image. Others will work but this will keep us all on the same page.
4. 

```
In the directory /root/Android/

./emulator -avd Nexus_5X_API_25 -memory 768 -no-accel -gpu on