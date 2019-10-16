# Automated Scanning
While running tools such as `strings` are very useful in our quest to understand the inner-workings of an app from an attackers perspective, we have some excellent automated solutions available to us that can be plugged directly to our pipeline and SDLC. One of those tools is [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF).

Mobile Security Framework is an automated, all-in-one mobile application (Android/iOS/Windows) pen-testing framework capable of performing static analysis, dynamic analysis, malware analysis and web API testing. 

We will be using Docker to run MobSF. If you do not already have Docker installed on your laptop feel free to use the free in-browser Docker playground called Play With Docker:

[https://labs.play-with-docker.com](https://labs.play-with-docker.com)

* You will need an account on Docker Hub to use Play With Docker.

```
sudo docker pull opensecurity/mobile-security-framework-mobsf
sudo docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

Now open up Firefox or Chromium in the VM and go to the following URL:
```
http://localhost:8000
```

This will open the MobSF web UI. From here, we can start analyzing our .apk files. MobSF handles things like running `strings` and performing dynamic analysis for us. Tools like these are being run against your Android applications constantly looking for issues.

First, we will scan our `diva-beta.apk` file using MobSF. Drag the .apk in Santoku into the browser running MobSF.

There are a few additional apk files located in this lab that you can also scan. These were chosen at random and are not necessarily vulnerable. The files are located in the `/other_apks` directory of this lab.

Did you anything interesting?

## Discussion Question
How would you plug a tool like this into your current CI/CD pipeline?
