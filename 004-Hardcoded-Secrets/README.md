### Task 1: Running Strings
Strings will help us discover hardcoded credentials, URLs, keys, and more. It is a simple tool that is used as the first step in recon of an app. We will run strings on the `classes.dex` file that was produced after we unzipped the .apk. Below are some simple examples. Feel free to experiment further

```
strings classes.dex | egrep -i 'http|https'
strings classes.dex | egrep 'key'
strings classes.dex | egrep 'password'
strings classes.dex | egrep 'secret'
```

### Discussion Question

Were you able to find anything of interest when running strings?

### Challenge: Hardcoded Vendor Backdoor

Open up DVIA in the emulator and navigate to `2. Hardcoding Issues - Part 1`

Enter a value in the vendor key input box and observe what happens.

### Challenge
Using our decompiled application in JD-GUI, can you find where the hardcoded credentials for the vendor key is are located?