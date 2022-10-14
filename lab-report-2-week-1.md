# Lab Report 2 (Week 1)
	
## Part 1 - Installing VScode
In order to get started with coding, you will need an IDE, or an integrated development environment. These are most often in the forms 
of software IDE's are used to run and compile code for you and will make your lives easier. The IDE that we will be using is 
Visual Studio Code (VS Code), since it is free and highly versatile in its diverse and built in functions.
The first thing to do is to download Visual Studio Code from https://code.visualstudio.com/ by clicking the download button shown below.

![image](https://user-images.githubusercontent.com/114563712/193394470-dadbfbc0-fcd8-4a16-93fa-418f80f9bebf.png)

After downloading Visual Studio Code, your VS Code should look like this.

![image](https://user-images.githubusercontent.com/114563712/193394436-878621be-0cca-4ab1-9aca-fb98b5e4f119.png)

## Part 2 - Remotely Connecting
The first thing you want to do before you remotely connect is to set up your remote account. You can look for your account with
the [Account Lookup Tool](https://sdacs.ucsd.edu/~icc/index.php). After going to the link, your browser should look like this:
![image](https://user-images.githubusercontent.com/114563712/195775580-90fe0a65-0e6f-48e6-bb20-115ed9e3c4ee.png)
Now type in your UCSD username and PID as shown, and click submit. The browser should display all accounts that are linked with
your UCSD account, the one that we will be using for this course is "cs15lfa22" followed by a few characters. Remember what the
account name is as you will be using it to log in remotely. Now click "change your password" and change your accounts password
according to the conditions shown. 

After successfully changing your password, you will want to go back to your VS Code and open up a new terminal. You can do so by
clicking on terminal in the top bar then new terminal as shown in the image below: 

![image](https://user-images.githubusercontent.com/114563712/195776339-5f9e0544-4e23-4669-80f6-c7e98d22ac99.png)

To actually connect to your remote account, you want to type into the terminal you just created
```
ssh cs15lfa22zz@ieng6.ucsd.edu
```
where the zz are the characters from your account name, and the @ieng6.ucsd.edu is the server you are trying to connect to. 
After typing this command in, the terminal will prompt you to enter a password, this is the password that you had just set 
your account to. Input your new password to finally log in remotely to your account.

This is what should show up once you've successfully remotely connected to your account.
![image](https://user-images.githubusercontent.com/114563712/193394530-48a4431d-2f4b-4165-880e-8e666b540a38.png)

## Part 3 - Trying Some Commands
Now just explore the remote account with some commands. This is a list of some commands that you could use.
![image](https://user-images.githubusercontent.com/114563712/193394589-61df54cb-971d-43be-bf8c-e604130980ff.png)


Here are the commands I used.

![image](https://user-images.githubusercontent.com/114563712/193394578-6e5c73f6-a9ff-4bc4-b1b2-5a99f73eccde.png)

## Part 4 - Moving Files with scp
Next, you will be learning about moving files locally to remote servers using the SCP command. First you will want to
create a new file called WhereAmI.java and paste this code into it.
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

After pasting this code into your new file, compile and run your code using the commands:
```
javac WhereAmI.java
java WhereAmI
```
Now, to copy it over to your remote account, you will want to use the scp command.
```
scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/
```
SCP is a command that allows you to copy files remotely, the typical format is scp followed by the file you want
to copy, followed by your remote account. (Again the zz after the cs15lfa22 here are the characters from your account)
Here we added :~/ to the end of the remote account to copy it directly to the main directory. After running this
command, it will prompt you to enter your password again similarly to logging in with the ssh command.

After copying it over, you would want to log back in to your remote account and check if it actually copied, so 
log back in with the steps from part 2. After seeing that it copied over, compile and run it. In the image below,
I demonstrate how I did all of the previous steps for this part.

![image](https://user-images.githubusercontent.com/114563712/193394632-d0d97417-52bb-4be4-b648-205a2a39bbac.png)

## Part 5 - Setting an SSH Key
Everytime we log in to our remote account, or move files using SCP, the terminal will ask us to enter a password,
which can get frustrating at times while you are in a rush. SSH Keys are the solution to this problem as they 
replace our need to input the password. You can generate SSH Keys using a program by calling the command
```
ssh-keygen
```
which creates two files called public key and private key. The public key is copied to the server while the private
key is copied to the client. Here is what the entire process of running `ssh-keygen` should look like:

![image](https://user-images.githubusercontent.com/114563712/193394723-6c0dd920-53f4-4543-9169-97d954cb8cf7.png)

After doing this, you can now use SSH and SCP without inputting your password every single time you want to run the command.

## Part 6 - Optimizing Remote Running

There are also some helpful tips that you can pick up, such as running multiple commands at the same time, or even 
running multiple commands directly into your SSH account.

For example:

![image](https://user-images.githubusercontent.com/114563712/193394961-c0539296-f358-484a-bced-e6768cbcc36e.png)

You can also run the command
```
cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```
to give the result:

![image](https://user-images.githubusercontent.com/114563712/195783681-417d48d9-0a67-428f-9dfd-a6d12822272f.png)

# This concludes the lab!
