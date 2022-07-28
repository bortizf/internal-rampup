# The Linux Operating System
Most of the UNIX-Like operating systems (OS) share the same structure. It's divided into the parts that saw on [chapter 2](../ch2). We are going to focus on Linux because it's free and you will find some of its flavors while working on real infrastructure. We are not going to explain the internals or how it's designed. We will prepare you so that you feel confident working from the terminal. When doing this you will learn important topics in the linux world. Finally, at this point it's important that you have a host with Linux installed to do the exercise we will provide you. It can be a VM, WSL or a website. 

Before start playing with the terminal we need to know what a terminal is. A terminal is a program that runs a shell. And a shell is a Command Line Interface (CLI) to interact with the OS from the user point of view. You are likely familiar with a Graphical User Interface (GUI), that's another way end-users interact with the OS. The built-in shell on Linux is Bash, however there are several (Do you know of another? If not, try looking for them).  

## Shell Commands
In this section we will give you several commands that will help you to navigate on the terminal, to manipulate files and text, work with processes and basic networking, and manage services.  

### Navigation 

* **cd**: Moves between directories
* **ls**: Lists files and directories in your current working directory 
* **pwd**: Displays the absolute path of your current working directory

```bash
cd myfolder/ # moves to myfolder/ directory
ls myfolder/ # displays the content inside myfolder/
pwd # displays the absolute path of myfolder, e.g., /home/user/myfolder/
```

### Files and Text
From this section we will use variables to abreviate words. When we use $pwd we'll be refering to you current working directory. 

* **mkdir**: Creates a directory in your $pwd. Throws an error if the directory you're trying to create already exists
* **rmdir**: Removes an empty directory. Throws an error if you try to remove a directory that isn't empty.
* **rm**: Removes a file. You can also remove a directory if you pass it the *-r* flag
* **touch**: Creates a file. If the file already exists it will update its modification time.
* **mv**: Moves a file from one location to another. You can move directories if you pass the *-r* flag. Also, this command can be used to rename files. 
* **cp**: Copies a file from one location to another. You can move directories if you pass the *-r* flag. 
* **cat**: Prints the file content to the standard output (stdout).
* **echo**: Prints any argument to the stdout.
* **head**: Prints the first lines of a file to the stdout.
* **tail**: Prints the last files of a file to the stdout
* **chmod**: Adds or removes permissions to a file. You can learn more about files permissions [here](https://linuxize.com/post/understanding-linux-file-permissions/).
* **find**: Search for files based on several parameters. You can filter by name, size, time creation, and much more. Also, you can execute other commands on the files that this command finds.

```bash
mkdir newdir # Creates newdir 
rmdir newdir # Removes newdir because it's empty.

mkdir folder
cd folder
touch newfile # Creates newfile in folder/
rmdir folder # throws an error because it has content
rm -r folder/ # Removes folder with all its content

mv file1 file2 # Renames file1 as file2
cat file2 # displays the file2 content

chmod u+x file2 # Allows the file owner to execute file2. 
```

### Text Processing with Grep, AWK and Sed

**Grep** is a utility to find text on files using regular expressions. It has many flags to expand its functionality, you can learn more on its manual page (man grep). Let see that you want to know if a file (*test-file*) contains a word (*word-test*) and if so, you want to know on what line it's. 

```bash
grep "word-test" $pwd/test-file # If it exists, it will return the string you passed it. Otherwise, it won't display anything. With the '-n' flag you will get the number line where it's located.

grep -l "word-test" *.txt # With the '-l' flag you can search for all filenames txt files that contains that string.

grep "word-*test" $pwd/test-file # You can use regular expression in your searchs. In this case it will match any of these strings: word-test, word--test, wordtest or word-------test. The '*' matches 0 or more '-'.
```