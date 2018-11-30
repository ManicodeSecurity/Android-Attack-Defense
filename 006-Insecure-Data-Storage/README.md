# Insecure Data Storage
Improper data storage is a massive problem in the Android ecosystem. These labs will cover how to exploit some common flaws around data storage locations.

## Find the Credentials

### Task 1: Enter Your "Creds"

Open up DVIA in the emulator and navigate to `4. Insecure Data Storage - Part 2`

Enter a fake username and password in the input fields. 

Now, our task is to find how these credentials were stored:

### Task 2: Find the Flaw

To understand where our app is storing the data, open the“InsecureDataStorage2Activity.class” file using JD-GUI in the Santoku VM. We can see that the application is running raw SQL queries to insert the credentials into a SQLite database.

```
this.mDB.execSQL(“INSERT INTO myuser VALUES (‘” + localEditText1.getText().toString() + “‘, ‘” + localEditText2.getText().toString() + “‘);”);
```

Now that we know the app is using SQLite, we can retrieve the data.

### Task 3: Use adb to Connect to the Emulator

We will use `adb shell` to connect to the emulator and explore the filesystem:

1. In the `platform-tools` directory on your local machine that we used to run `adb` in `001-Lab-Setup` run the following command:

```
./adb shell
```

This will drop us into our emulator and we can begin exploring the filesystem.

Run the following commands to view the credentials:

```
# First, escalate to root
su

# Navigate to the databases directory
cd /data/data/jakhar.aseem.diva/databases/

# Change permissions on the database file so we can pull it to our local machine
chmod 777 ids2

# Copy the file to the sdcard
cp ids2 /mnt/sdcard
```

### Task 4: Dump the Database File 

Now we can "pull" the SQLite database file to our local machine for further investigation.

```
# Open a new terminal window
./adb pull /mnt/sdcard/ids2
```

We will use the built in SQLite Command-line utility to analyze the file:
```
# Open the DB file
sqlite3 ids2

# Show the tables
sqlite> .tables

# Fetch the data
sqlite> select * from myuser;
```

As you can see, the credentials are stored in plaintext on the device in a SQLite table.

##  Find the Creds - Part 2

The goal is to see how attackers can retrieve user-entered data that is being stored in SharedPreferences and what flaw in the code may lead to this vulnerability. 

Open up DVIA in the emulator and navigate to `3. Insecure Data Storage - Part 1`

### Task 1: Enter Some Dummy Creds

Enter some data into the text fields of the application (such as ADMIN / ADMIN) Click “SAVE” button to save the data in the emulator app.

### Task 2: Find the Flaw

To better understand where the app is storing the data, open up “InsecureDataStorage1Activity.class” file using JD-GUI. The source code reveals that the app is using `SharedPreferences` to store the user entered sensitive data.

### Task 3: Use adb to Connect to the Emulator

Similar to the previous task of this lab, we will use `adb` to connect to our emulator:

```
./adb shell
```

This will drop us into our emulator and we can begin exploring the filesystem.

### Challenge

Can you find the credentials you entered in the `shared_prefs` file?
