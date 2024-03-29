# The Linux Operating System
Most of the UNIX-Like operating systems (OS) share the same structure. It's divided into the parts seen on [chapter 2](../ch2). We are going to focus on Linux because it's free and you will find some of its flavors while working on real infrastructure. We are not going to explain the internals or how it's designed. We will prepare you so that you feel confident working from the terminal. When doing this you will learn important topics in the linux world. Finally, at this point it's important that you have a host with Linux installed to do the exercise we will provide you. It can be a VM, WSL or a website. 

Before start playing with the terminal we need to know what a terminal is. A terminal is a program that runs a shell. And a shell is a Command Line Interface (CLI) to interact with the OS from the user's perspective. You are likely familiar with a Graphical User Interface (GUI), that's another way end-users interact with the OS. The built-in shell on Linux is Bash, however there are several (Do you know other? If not, try looking for them).  

## Shell Commands
In this section we will give you several commands that will help you to navigate on the terminal, to manipulate files and text, work with processes and basic networking and manage services.  

### Navigation 

* **cd**: Navigate between directories
* **ls**: List files and directories in your current working directory 
* **pwd**: Display the absolute path of your current working directory

```bash
cd myfolder/ # it moves you to myfolder/ directory
ls myfolder/ # it displays the content inside myfolder/
pwd # it displays the absolute path of myfolder, e.g., /home/user/myfolder/
```

## Files and Text
From this section we will use variables to abbreviate words. When we use $pwd we'll be refering to your current working directory. 

* **mkdir**: Creates a directory in your $pwd. Throws an error if the directory you're trying to create already exists
* **rmdir**: Removes an empty directory. Throws an error if you try to remove a directory that isn't empty.
* **rm**: Removes a file. You can also remove a directory if you pass it the *-r* flag
* **touch**: Creates a file. If the file already exists it will update its modification time.
* **mv**: Moves a file from one location to another. You can move directories if you pass the *-r* flag. Also, this command can be used to rename files. 
* **cp**: Copies a file from one location to another. You can copy directories if you pass the *-r* flag. 
* **cat**: Prints the file content to the standard output (stdout).
* **echo**: Prints any argument to the stdout.
* **head**: Prints the first lines of a file to the stdout.
* **tail**: Prints the last files of a file to the stdout
* **chmod**: Adds or removes permissions to a file. You can learn more about file permissions [here](https://linuxize.com/post/understanding-linux-file-permissions/).
* **find**: Search for files based on several parameters. You can filter by name, size, time creation, and much more. Also, you can execute other commands on the files that this command finds.

```bash
mkdir newdir # Creates newdir 
rmdir newdir # Removes newdir because it's empty.

mkdir folder
cd folder
touch newfile # Creates newfile in folder/
rmdir folder # throws an error because it has content
rm -r folder/ # Removes folder with all its content

mv file1 file2 # Renames file1 to file2
cat file2 # displays the file2 content

chmod u+x file2 # Allows the file owner to execute file2. 
```

Another powerful feature of the shell is piping. It allows you to redirect input and output of commands. If you need to order a file you can do this:
```bash
cat /etc/passwd | sort
```
where the metacharacter | connects the output of *cat* with the input for the *sort* command. You can connect commands as much as you want, and you can solve complex tasks with this.  

The > metacharacter redirects the output of a command to another file (or device). If you need to save the output of cat on file, you can do this:
```bash
cat /etc/passwd > output.txt
```
Instead of displaying the content to the stdout, it will be redirected to the output.txt file.

We also have the < metacharacter. This redirects the stdin. Although this is not as useful as its opposite. Finally, if we want to save the errors of a command, we can redirect the stderr too. This is done via 2> metacharacter. 

## Text Processing with Grep and Sed

**Grep** is an utility to find text on files using regular expressions. It has many flags to expand its functionality. You can learn more on its manual page (man grep). Let's say that you want to know if a file (*test-file*) contains a word (*word-test*) if so, you want to know on what line it's. 

```bash
grep "word-test" $pwd/test-file # If it exists, it will return the string you passed it. Otherwise, it won't display anything. With the '-n' flag you will get the number line where it's located.

grep -l "word-test" *.txt # With the '-l' flag you can search for all filenames txt files that contains that string.

grep "word-*test" $pwd/test-file # You can use regular expressions in your searches. In this case it will match any of these strings: word-test, word--test, wordtest or word-------test. The '*' matches 0 or more '-'.
```

**Sed** performs editing operations on text. You can print or delete a range of lines, but you also can substitute words or phrases based on regular expressions. Let's see these tree operations:

To *print* the n line of a file you will use 'np'. For example, to print the fifth one:
```bash
sed -n '5p' file
```
You will need the -n flag because sed prints each line by default, and if you specify the *p* option, it will print twice each line.

You can also use a range format to print lines. For example, to print lines 10th-16th:
```bash
sed -n '10,16p' file
```
To *delete* a line will be a similar format, but instead of using *p* letter you will use *d*. For example, to delete the first 5 lines:
```bash
sed '1,5d' file
```
In this case you no longer need the -n flag because the operation isn't print.

Finally, the most well-known operation of sed - *substitute*. You can perform the search based on a regular expression. The basic syntax for is 's/old_w/new_w/'.  The / is used to separate the words, however you can use other characters as well. Let's see this example:

```bash
echo "www.mywebsite.com/login.html" | sed 's_.com/login_.net/home_'
# The output will be www.mywebsite.net/home.html
```
In the previous example we used the _ character as a delimiter. If you need to replace multiple ocurrences of a word you will need to specify it because sed command operates on the first match. 

```bash
string="TEXT TEXT TEXT HELO TEXT HELLO TEXT"
echo $string | sed 's/TEXT/text/' # this will replace the first occurrence of TEXT
echo $string | sed 's/TEXT/text/g' # this will replace all occurrences of TEXT
```

## Managing running processes
A process is an instance of a program running on a computer. From the shell you can execute, pause, stop or kill them. Also, you can put them in the background or bring them to the foreground. When you put a process in the background, you will not see any output or execution on your terminal, whereas if you run it in the foreground you will see the output and you will have to wait for it in order to execute another command on the same shell. A process has an unique identifier called a Process ID (PID). 

### ps command
The first command we will use to manage running process is ps. With ps you can only list them. On the default output of ps command you will see, among others, the user who executes the program, the process ID (PID). Also, you will see the memory and CPU consumed by the process. 

* `ps u`: list the processes running on your terminal.
* `ps ux`: list all the processes running on your system for the current user.
* `ps aux`: list all the processes running on your system for all users.

### top command
The top command provides a screen-oriented. You can kill process with this command, but also sort them based on your needs.

Once it displays the screen you can use different keys to perform tasks. For example, to sort based on the Memory consumption press the key **M**. To sort by CPU press **P**. Also, if you need to filter the process by user type **U** and enter the username you want to see. Finally, you can kill a process if you type **K** and enter the PID. To find information about the commands type **H**

### Background and foreground
Sometimes you only have access to a machine via terminal and you need to execute multiple commands. If you run a program that stays on your main terminal (on foreground), then you won't be able to run another one. To avoid this, you can send the process to the background and you can continue using the terminal. 

To send a process to the background you add the ampersand (&) to the end of the command line. Let's see
```bash
sleep 180s &
```
this will output the job number surrounded by [] and the PID. You won't see anything else unless the command send data to the stdout. 

To check which commands are running in the background (with their PIDs) use the *jobs* commands as follows:
```bash
jobs -l
```

If you need to bring a process to the foreground, you can use the *fg* command. For example, to bring the second job you can use this:
```bash
fg %2
```

### Killing processes
When a process is running we can send to them signals that can change their behavior. The most common signals that you might send are SIGKILL (9), SIGTERM (15), and SIGHUP(1). Type `man 7 signal` to read about all the availables signals.
* SIGTERM tries to terminate a process cleanly.
* SIGKILL kills a process immediately.
* SIGHUP tells a process to reread its config files.
* SIGSTOP pauses a process.
* SIGCONT continues a stopped process.

In order to manipulate a process you need to know its PID. Let's say a process has the 180 ID. To send signals to it, we use the `kill` command as follows:

- To send a SIGTERM signal: `kill 180` or `kill -15 180`. The default signal that the kill command uses is SIGTERM (15), that's why the previous commands are equivalent.
- To kill it immediately: `kill -SIGKILL 180`. You can also use the number 9: `kill -9 180`

## Network commands
On this section you will find commands that will help you troubleshoot networking related issues, get information about your network or other networks, and send request to a DNS server.

### ip command
This command has many options, but let's take a look at the basics ones. In most cases the outputs of this command aren't easy to read, that's why we add ` | column -t` at the end of the command line. 
* `ip link | column -t` will display all your physical and logical network interfaces.
* `ip addr` will display your physical and logical interfaces, but it will also add the ip address, subnet mask, and broadcast address.
* `ip route | column -t` will display your routing table.

you can add the `-brief` flag to get a shorter output, e.g. `ip -br link | column -t`

### ping command
This command will help you when you need to check connectivity between hosts. For example, to check if you have internet connection you can ping to the google's servers 
```bash
ping -c 3 www.google.com
```
or if you need to check if your VMs are reachable, you can execute: `ping -c 3 10.1.2.3` where 10.1.2.3 is the IP address of other VM.

If you don't add the `-c` flag the execution will not finish until you press Ctrl+C.

### traceroute command
Use the traceroute command to follow an entire route from the beginning to the end. You can install it on Debian-based systems as follows:
```bash
sudo apt-get install inetutils-traceroute
```
To find out what hops your packets does to get to google.com:
```bash
traceroute -I google.com
``` 
some hosts have restrictions and you will see a * instead of their IP address.

### ss command
With ss command you will get information about the TCP/UDP connections on your system. The `t` flag is for TCP and `u` for UDP.
* `ss -tln` displays all listening TCP connections. If you add the `n` flag, then it will show you the port number too.
* `ss -uln` displays all listening UDP connections. 
* `ss -utln` combines TCP and UDP connections. 

You can use `a` flag to display all connection states. For example, `ss -tan` will display all TCP connections, not just the listening ones.

### dig command
dig command is used to query DNS servers. It's also used to troubleshoot DNS related issues. You can verify all DNS records. 

to query the google's DNS do this: 
```bash 
dig google.com
```
this will output an A record by default. If you are interested in other record types, you can pass it as a parameter like this:
```bash
dig google.com MX
```
Use the `ANY` parameter to dispaly all the record types. Also, you can pass the `+short` flag to get a shorter output: `dig google.com +short`. This command is an improvement to `nslookup` command, if you want to learn about [this](https://www.tecmint.com/8-linux-nslookup-commands-to-troubleshoot-dns-domain-name-server/) is a good place to start.

## Service management
The main goal of a server is to provide services. A service is a process that runs in the background (AKA daemon), and does not interact with the end-user. On Linux systems services are managed by the Init Daemon. The Init Daemon is the first process started by the kernel. It has a PID 1. It's responsible for launching other processes configured to be started at boot time. Systemd init is the most widely used init daemon today, so we are going to work with this. If you are interested on other init daemons, look for SysVinit, or BSD Init, or Upstart Init.

Systemd is based on a concept called Unit. A Unit is a group consisting of a name, type, and configuration file. There are eight systemd units types, but to work with services we just need the *service unit*. These units are located in `/etc/systemd/system/` and `/lib/systemd/system/`. To list all the service units in your system, type this:
```bash
sudo systemctl list-unit-files --type=service
```
The *service unit* configuration file contains information such as what other services must be started or which environment file use, but also what's the executable of the service. Here is an example of the cups' unit configuration file:
```bash
[Unit]
Description=CUPS Scheduler
Documentation=man:cupsd(8)
After=sssd.service
Requires=cups.socket

[Service]
ExecStart=/usr/sbin/cupsd -l
Type=simple
Restart=on-failure

[Install]
Also=cups.socket cups.path
WantedBy=printer.target
```

You can stop, start, restart, reload or see the status of a service with systemd. To check the status of the cups service, you can do this:
```bash
sudo systemctl status cups.service
```
This will provide you information about the current status and other important information. Also, in that output you can check if a service unit is enabled or not. An enabled service unit means that the service will be started at boot time.

Similarly, you can start or stop a service:
```bash
sudo systemctl stop cups.service
sudo systemctl start cups.service
```
Finally, with the reload command you can tell the service unit to rereads its config file. The service will not be stopped. However, you can also use the restart command to stop and start again a service unit in the event of a failure.

## Challenges
In this section you will find tasks that will help you to practice the commands we have seen and others.

* Display the content of the /etc/passwd, count how many lines it has and sort in a decreasing order (z-a).
* Find what is your User ID and Group ID. This information is stored in the /etc/passwd file. Also, find what's the line they are. Of course, you should do this without displaying the file's content.
* List files and directories that are hidden on your $pwd. Also, list them by time (use the man page to see what flag you need).
* Create a file called *myfile*. Update its permissions so only your user can read, write, and execute it. 
* Create 5 files (f1,f2,...,f5) without having to type 5 times the touch command. 
* Move to another location where those 5 files are not. Then do a search to find them, and execute the *ls -l* command to each of those. This should be done with just one command. 
* Create the directory d1/d2/d3/foo/d4. If the previous directories don't exist, then they should also be created automatically.
* Given the following text "We have 5 days to finish 5 lines of code of the Hi5b project" Replace all "5" by "five", the number must be alone, cannot be in a word.
* List all processes running on your system and sort them by the username that's running each process.
* Run the gedit program, search for it's PID and send it a signal to stop it. After this, send another one resume its execution.
* Install SSH server. Start the service, and check its status. If it is not enabled, do it. 
* Display the network interfaces on your system. Do you see one that isn't physical? What's that interface?
* What's your IP and MAC address?
* Can you communicate outside your private network? Test this with a command. 
* What happens to a packet going to a host outside of the network?
* What is the IP of your gateway(s)? Can you check this with two commands?
* Trace the route being taken to connect to cloudflare.com.
* What's the IP address of perficient.com? What's their mail server?
* List all TCP and UDP connections on the system.
* What ports do you have open on the system?
* List only the listening connections on the system.