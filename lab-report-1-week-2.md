[Index](https://jheidenr.github.io/cse15l-lab-reports)

# Step 1: Install VS Code

The first step is to install VS Code. Go to this [link](https://code.visualstudio.com/) and follow the instructions for your operating systsem on the website.

# Step 2: Remotely Connect

## Initial Step for Windows Users -

If you are using windows, you will need to install OpenSSH in order to be able to connect to other computers. To do this you must:

1. Go to Settings/Apps/Apps & Features/Optional Features
2. Click "Add a Feature" and install **OpenSSH Client** and **OpenSSH Server**

## Finding and Activating Your Personal Account

For this step you must go to [UCSD's Account Lookup Website](https://sdacs.ucsd.edu/~icc/index.php) and put in your information to find your account name. Then click **Change your password** to chang eyour accounts password and activate your account.

## Finally Connecting

First open a new terminal in VS Code. Then input this command:

>`ssh cs15lwi22zz@ieng6.ucsd.edu`

but replace `zz` with the letters found at the end of your username. When you first connect you may be given a long message and asked to say yes or no. Type `yes` to this message and enter your password.

**Note: You will not be able to see the characters of your password as you enter them**

*[image](screenshots/Step2ScreenShot.png)

# Step 3: Try Some Commands

Here are a few useful commands to try while you are connected:

* `cd (directory)/` - changes your working directory to the one that is specified

*  `ls` - lists all directories under the workig directory

* `pwd` - prints the path to the current working directory

* `mkdir (filename)` - creates a file in the working directory with the specified name

* `cp (sourcefile) (destinationfile)` - copies the first file to the second file. It creates the second file if it doesn't already exist.

Once your are done playing around with the commands, type `exit` to logout of the server.

# Step 4: Move Files Around With `scp`

First create a file anywhere on your computer and name it **WhereAmI.java**. Then open it and paste the following code into the file:

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
Run the program on your own computer by using
> `javac WhereAmI.java` and `java WhereAmI`

Then copy the file to the server by using the command:

**Replace `zz` with the letters from your account**

`scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`

You will be asked for you password as if your were connecting to the server. Once the file is copied, log back into the server and use `ls` and check if you can see the file. Then run the file on the server and notice the different output of the program.

# Step 5: Create an SSH Key

To create an SSH key use this following string of commands

# Step 6: Optimizing Remote Running