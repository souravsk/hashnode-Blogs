## Linux Commands

# Linux Shell or “Terminal”

So, basically, a shell is a program that receives commands from the user and gives it to the OS to process, and it shows the output. Linux's shell is its main part. Its distros come in GUI (graphical user interface), but basically, Linux has a CLI (command-line interface). In this tutorial, we are going to cover the basic commands that we use in the shell of Linux.
To open the terminal, press Ctrl+Alt+T in Ubuntu, or press Alt+F2, type in gnome-terminal, and press enter.

# Basic Linux Commands

## pwd
When you first open the terminal, you are in the home directory of your user. To know which directory you are in, you can use the “pwd” command. It gives us the absolute path, which means the path that starts from the root. The root is the base of the Linux file system. It is denoted by a forward slash( / ). The user directory is usually something like "/home/username".


![pwd.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656591795972/RyVFieIRF.png align="left")

## ls
Use the "ls" command to know what files are in the directory you are in. You can see all the hidden files by using the command “ls -a”.


![ls.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656591877119/ZglIhfHzW.png align="left")

## mkdir & rmdir
Use the mkdir command when you need to create a folder or a directory. For example, if you want to make a directory called “DIY”, then you can type “mkdir DIY”. Remember, as told before, if you want to create a directory named “DIY Hacking”, then you can type “mkdir DIY\ Hacking”. Use rmdir to delete a directory. But rmdir can only be used to delete an empty directory. To delete a directory containing files, use rm.


![mkdir.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656591957999/yh5Jg29DT.png align="left")


![rmdir.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592281689/FdSYrMCUl.png align="left")

## cd
Use the "cd" command to go to a directory. For example, if you are in the home folder, and you want to go to the downloads folder, then you can type in “cd Downloads”. Remember, this command is case-sensitive, and you have to type in the name of the folder exactly as it is. But there is a problem with these commands. Imagine you have a folder named “Raspberry Pi”. In this case, when you type in “cd Raspberry Pi”, the shell will take the second argument of the command as a different one, so you will get an error saying that the directory does not exist. Here, you can use a backward slash. That is, you can use “cd Raspberry\ Pi” in this case. Spaces are denoted like this: If you just type “cd” and press enter, it takes you to the home directory. To go back from a folder to the folder before that, you can type “cd ..”. The two dots represent back. Use the "cd" command to go to a directory. For example, if you are in the home folder, and you want to go to the downloads folder, then you can type in “cd Downloads”. 


![cd.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592000024/WZkGBMJO6.png align="left")

## touch 
The touch command is used to create a file. It can be anything, from an empty txt file to an empty zip file. For example, “touch new.txt”.


![touch.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592052553/u0DUr9791.png align="left")

## rm
Use the rm command to delete files and directories.  Use "rm -r" to delete just the directory. It deletes both the folder and the files it contains when using only the rm command.


![rm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592098378/OCMj59pu1.png align="left")

## cp
 Use the cp command to copy files through the command line. It takes two arguments: The first is the location of the file to be copied, and the second is where to copy it.


![cp.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592139954/Y_LwqIcka.png align="left")

## mv
Use the mv command to move files through the command line. We can also use the mv command to rename a file. For example, if we want to rename the file “text” to “new”, we can use “mv text new”. It takes the two arguments, just like the cp command.


![mvv.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592182451/NxV1VZSsy.png align="left")

## man & --help
To know more about command and how to use it, use the man command. It shows the manual pages of the command. For example, “man cd” shows the manual pages of the cd command. Typing in the command name and the argument helps it show which ways the command can be used (e.g., cd –help).


![help.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592674779/Osmw6EYlU.png align="left")

# Intermediate Commands
 
## echo
The "echo" command helps us move some data, usually text into a file. For example, if you want to create a new text file or add to an already made text file, you just need to type in, “echo hello, my name is sourav >> new.txt”. You do not need to separate the spaces by using the backward slash here because we put in two triangular brackets when we finish what we need to write.


![echo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592741423/8oxevfcz2l.png align="left")

## cat
Use the cat command to display the contents of a file. It is usually used to easily view programs.


![cat.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592772347/FLidhe0vs.png align="left")

## nano, vi, jed
nano and vi are already installed text editors in the Linux command line. The nano command is a good text editor that denotes keywords with color and can recognize most languages. And vi is simpler than nano. You can create a new file or modify a file using this editor. For example, if you need to make a new file named "check.txt", you can create it by using the command “nano check.txt”. You can save your files after editing by using the sequence Ctrl+X, then Y (or N for no). In my experience, using nano for HTML editing doesn't seem as good, because of its color, so I recommend jed text editor. We will come to install packages soon.


![vi.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656592867221/HKPY8ceEN.png align="left")


![Screenshot from 2022-06-30 18-13-49.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593083246/_F7yIV4HR.png align="left")

## sudo
A  widely used command in the Linux command line, sudo stands for "SuperUser Do". So, if you want any command to be done with administrative or root privileges, you can use the sudo command. For example, if you want to edit a file like viz. also-base. conf, which needs root permissions, you can use the command – sudo nano alsa-base.conf. You can enter the root command line using the command “sudo bash”, then type in your user password. You can also use the command “su” to do this, but you need to set a root password before that. For that, you can use the command “sudo passwd”(not misspelled, it is passwd). Then type in the new root password.


![sudo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593125783/hTXmWoI-6.png align="left")

## df
Use the df command to see the available disk space in each of the partitions in your system. You can just type in df in the command line and you can see each mounted partition and their used/available space in % and in KBs. If you want it shown in megabytes, you can use the command “df -m”\


![df.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593158505/X2gEfrlXC.png align="left")

## du
 Use du to know the disk usage of a file in your system. If you want to know the disk usage for a particular folder or file in Linux, you can type in the command df and the name of the folder or file. For example, if you want to know the disk space used by the documents folder in Linux, you can use the command “du Documents”. You can also use the command “ls -lah” to view the file sizes of all the files in a folder.


![du.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593203965/eh1Ci8dgx.png align="left")

## tar
Use tar to work with tarballs (or files compressed in a tarball archive) in the Linux command line. It has a long list of uses. It can be used to compress and uncompress different types of tar archives like .tar, .tar.gz, .tar.bz2,etc. It works on the basis of the arguments given to it. For example, "tar -cvf" for creating a .tar archive, -xvf to untar a tar archive, -tvf to list the contents of the archive, etc.


## zip, unzip
Use zip to compress files into a zip archive, and unzip to extract files from a zip archive.

## uname
Use uname to show the information about the system your Linux distro is running. Using the command “uname -a” prints most of the information about the system. This prints the kernel release date, version, processor type, etc.


![uname.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593383871/lGmgJq9k4.png align="left")

## apt-get
Use apt to work with packages in the Linux command line. Use apt-get to install packages. This requires root privileges, so use the sudo command with it. For example, if you want to install the text editor jed (as I mentioned earlier), we can type in the command “sudo apt-get install jed”. Similarly, any package can be installed like this. It is good to update your repository each time you try to install a new package. You can do that by typing “sudo apt-get update”. You can upgrade the system by typing “sudo apt-get upgrade”. We can also upgrade the distro by typing “sudo apt-get dist-upgrade”. The command “apt-cache search” is used to search for a package. If you want to search for one, you can type in “apt-cache search jed”(this doesn't require root).


![apt.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593427069/D2CvWNV9F.png align="left")

## chmod
Use chmod to make a file executable and to change the permissions granted to it in Linux. Imagine you have a python code-named numbers.py in your computer. You'll need to run “python numbers.py” every time you need to run it. Instead of that, when you make it executable, you'll just need to run “numbers.py” in the terminal to run the file. To make a file executable, you can use the command “chmod +x numbers.py” in this case. You can use “chmod 755 numbers.py” to give it root permissions or “sudo chmod +x numbers.py” for root executable. 


![la.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593659347/8kZ73e5Dd.png align="left")

## hostname
Use hostname to know your name in your host or network. Basically, it displays your hostname and IP address. Just typing “hostname” gives the output. Typing in “hostname -I” gives you your IP address in your network.


![hostname.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593701284/RFAyTVBR6.png align="left")

## ping
Use ping to check your connection to a server. Wikipedia says, "Ping is a computer network administration software utility used to test the reachability of a host on an Internet Protocol (IP) network". Simply, when you type in, for example, “ping google.com”, it checks if it can connect to the server and come back. It measures this round-trip time and gives you the details about it. The use of this command for simple users like us is to check your internet connection. If it pings the Google server (in this case), you can confirm that your internet connection is active!


![ping.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656593752171/Ftp0Ubp9l.png align="left")

Thank You 
Please do share if you like it.
