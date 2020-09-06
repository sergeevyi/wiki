**cd** — Use the "cd" command to go to a directory

**cd ..**  The two dots represent back.

**pwd** - It gives us the absolute path, which means the path that starts from the root

**ls** — Use the "ls" command to know what files are in the directory you are in. You can see all the hidden files by using the command “ls -a”.

**mkdir** Use the mkdir command when you need to create a folder or a directory.

**rmdir** delete an empty directory

**rm** - Use the rm command to delete files and directories. Use "rm -r" to delete just the directory.

**touch** — The touch command is used to create a file.

**man & --help** — To know more about a command and how to use it, use the man command. It shows the manual pages of the command. For example, “man cd” shows the manual pages of the **cd** command. Typing in the command name and the argument helps it show which ways the command can be used (e.g., cd –help).

**cp** — Use the cp command to copy files through the command line. It takes two arguments: The first is the location of the file to be copied, the second is where to copy.

**mv** — Use the mv command to move files through the command line. We can also use the mv command to rename a file.

**echo** — The "echo" command helps us move some data, usually text into a file (echo hello, my name is alok >> new.txt)

**cat -** Use the cat command to display the contents of a file

**tail** - the tail command reads a file, and outputs the last part of it (By default, tail prints the last 10 lines )

tail -n 100 myfile.txt  Outputs the last 100 lines of the file myfile.txt

tail -f access.log | grep 24.10.160.10 This is a useful example of using tail and grep to selectively monitor a log file in real time.

**wc** -l ****combined.txt  line count

**head -** Display the first lines of a file.

head -15 myfile.txt Display the first fifteen lines of myfile.txt.

**sudo** - run any command with root privileges

**df -** Use the df command to see the available disk space in each of the partitions in your system

If you want it shown in megabytes, you can use the command “df -m” ( by default in KBs)

**du** — Use du to know the disk usage of a file in your system. if you want to know the disk space used by the documents folder in Linux, you can use the command “du Documents”. You can also use the command “ls -lah” to view the file sizes of all the files in a folder.

**tar** — Use tar to work with tarballs (or files compressed in a tarball archive) in the Linux command line. For example, "tar -cvf" for creating a .tar archive, -xvf to untar a tar archive, -tvf to list the contents of the archive, etc. Since it is a wide topic, here are some examples of tar commands.

**uname -** Use uname to show the information about the system your Linux distro is running. Using the command “uname -a” prints most of the information about the system.

**apt-get** - Use apt to work with packages in the Linux command line. Use apt-get to install packages.

sudo apt-get install je - install an app

sudo apt-get update - update your repository

sudo apt-get upgrade - upgrade the system. We can also upgrade the distro by typing “sudo apt-get dist-upgrade

**chmod -** Use chmod to make a file executable and to change the permissions granted to it in Linux. To make a file executable, you can use the command “chmod +x [numbers.py](http://numbers.py/)” in this case. You can use “chmod 755 [numbers.py](http://numbers.py/)” to give it root permissions or “sudo chmod +x [numbers.py](http://numbers.py/)” for root executable

**hostname** — Use hostname to know your name in your host or network. Typing in “hostname -I” gives you your IP address in your network.

**ping** — Use ping to check your connection to a server.

**wget** - download a file from a server to your local computer

**ps / top** - the ps / top commands allow you to list the processes running on your computer ps -aux. Note that this will only generate a snapshot. You can, however, get a list that refreshes itself by using the top command

ps aux | grep java

**kill** - the kill command can be used to end a running task. Either way, you’ll have to find out the PID of the process (you can do that with ps or top)

t**ree** - list directory contents

sudo apt install tree

[https://www.howtoforge.com/linux-tree-command/](https://www.howtoforge.com/linux-tree-command/)

**curl**

[https://www.tecmint.com/linux-curl-command-examples/](https://www.tecmint.com/linux-curl-command-examples/)

**httpie** is a command-line HTTP client

[https://github.com/jakubroztocil/httpie](https://github.com/jakubroztocil/httpie)

[https://medium.com/swlh/introduction-to-httpie-a-lightweight-http-client-502e6e08ca6c](https://medium.com/swlh/introduction-to-httpie-a-lightweight-http-client-502e6e08ca6c)

**jq** is a lightweight and flexible command-line JSON processor

[https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/](https://www.howtogeek.com/529219/how-to-parse-json-files-on-the-linux-command-line-with-jq/)

**fx** - JSON viewer

[https://github.com/antonmedv/fx](https://github.com/antonmedv/fx)

**less** is a command line utility that displays the contents of a file or a command output, one page at a time.

**lsof**

[https://www.howtogeek.com/426031/how-to-use-the-linux-lsof-command/](https://www.howtogeek.com/426031/how-to-use-the-linux-lsof-command/)

[**youtube-dl](https://github.com/ytdl-org/youtube-dl)** - download videos from [youtube.com](http://youtube.com/) or other video platforms

[https://github.com/ytdl-org/youtube-dl](https://github.com/ytdl-org/youtube-dl)

**ctop** -Top-like interface for container metrics

[https://github.com/bcicen/ctop](https://github.com/bcicen/ctop)

**mc** - file manager

Links:

[https://www.computerhope.com/unix.htm](https://www.computerhope.com/unix.htm)

[https://maker.pro/linux/tutorial/intermediate-linux-commands](https://maker.pro/linux/tutorial/intermediate-linux-commands)
