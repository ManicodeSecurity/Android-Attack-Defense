### Task 1: Decompile classes.dex
We want to begin exploring our `classes.dex` file in a more human-readable format. We will use the classing Android hacking tool called `dex2jar` which is pre-installed in the Santoku VM:

In the directory you unzipped in the previous lab, run the following command:
```
d2j-dex2jar classes.dex
```

This creates a files named `classes-dex2jar.jar` which we can then open using the GUI tool for exploring .jar files called `jd-gui`:

```
jd-gui class-dex2jar.jar`
```

Take some time to browse the classes in the application in JD-Gui.
