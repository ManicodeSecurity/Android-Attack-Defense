Logs are a part of daily life as an Android application developer. Log files may be used to keep track of statistics, application crashes, and errors. The problem occurs when sensitive data is logged. In this lab, we will explore Android logs in our emulator using `logcat`.

### Task 1: Using Logcat
In the `platform-tools` directory on our local machine, we first fire up `logcat` using the following command:

```
./adb logcat
```

Do not close the terminal window.

### Task 2: Enter our CC Number

Open up DVIA in the emulator and navigate to `1. Insecure Logging`.

Enter a FAKE credit card number (not your own obviously).

If you open up our `logcat` terminal window and find the log entry with our credit card number.

### Discussion Question
How could a malicious app take advantage of this flaw?

### Challenge
Can you find the lines of code responsible for this issue in JD-GUI?