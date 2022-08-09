# Scripting

In this section we will give you an introduction to shell scripting. In particular, we will focus on Bash scripting but the concepts that you will learn here can be applied to any other scripting language (Powershell or Python). We will discuss about variables, conditionals, functions, loops, arrays, and Bash-specific topics.

Bash is the shell that is installed on most of the Linux distributions. We use it in interactive mode when we work from the command line. However, we can also work with Bash in non-interactive mode. To do this we use Scripts. Scripts are lists of commands (like the ones you can type on the CLI), but stored in a file. When you run a script, all the commands are executed sequentially. 

## Variables

Variables are a space in memory that you can use to retrieve or store information. To store data in a variable, we use this:
```bash
#!/bin/bash

varname="PRFT"

# this is wrong because we cannot use spaces around the = sign.
varname2 = "PRFT"
```
If you noticed I added `#!/bin/bash` at the beginning of the script. This is called *interpreter directive* and specifies that /bin/bash will be used as the interpreter when this script is executed. 

To retrieve information from a variable we used the `$` sign, as follows:
```bash
#!/bin/bash

echo $varname # will output PRFT
```
there are some builtin variables called *special parameters*:
* `$1`, `$2`, ... `$n`: this contains the arguments that are passed to the current script or function.
* `$@` it expands to a list of all positional parameters.
* `$#` expands to the number of positional parameters that you passed to the function or the script.
* `$?` expands to the exit code of the most recently executed foreground command.

## Conditionals
`if` is the keyword to check that a command's exit code was successfull or not. An exit code is like a return value from the command's execution. It's 0 to denote success, and any other number less than 255 to denote failures.

```bash
#!/bin/bash

company="$USER"

if [[ $company = "Pepe" ]]
then
    echo "Hello Pepe, welcome to PRFT"
elif [[ $company = "Mat" ]]
then
    echo "Hello Mat, welcome to PRFT"
else
    echo "Hello other, welcome to PRFT"
fi
```

the comparison operatos `=`, `!=`, `>`, `<` treat their arguments as strings. To compare numeric values Bash has another set of operators: 
* `eq`: equal
* `ne`: no equal
* `lt`: less than, `le` less than or equal
* `gt`: greater than, `ge` greater than or equal

can you guess what's the output of the following script?

```bash
n1="314"
n2="9"

if [[ $n1 > $n2 ]]
then
    echo "$n1 is greater than $n2"
elif [[ $n2 > $n1 ]]
then
    echo "$n2 is greater than $n1"
else
    echo "$n1 is equal to $n2"
fi
```
Math is a joke for this script. It will output *9 is greater than 314*. Why? because we used the operators to compare strings, so the script is comparing the number lexicographically. Try to fix it by yourself.

## Loops
On Bash there are *While* and *For* loops. Also, there is a variant of the While loop called *Until*, and the For loop comes into two forms.
* `while` *command*: repeat as long as the *command* runs successfully.
* `until` *command*: repeat as long as the *command* runs unsuccessfully.
* `for` *variable* `in` *list*: repeat for each element in the list, setting *variable* to each element in turn.
* `for ((`*expression*`;`*expression*`;`*expression*`))`: starts evaluating the first arithmetic *expression* and will run as long as the second arithmetic *expression* is successfully, and at the end of each loop evaluates the third *expression* (generally this is an increment to variable in turn)

this is the geneal syntax of a Bash loop: 
```bash
# here comes one of the forms we saw, e.g., while *expression*
while expression
do
    commands
done
```

Let's see an example to print odd numbers less than 20 with all the loop forms:

```bash
#!/bin/bash

# With a while loop
(( i=20 ))
while (( i > 0 ))
do
    if [[ $(( $i % 2 )) -ne 0 ]]
    then
        echo "$i is an odd number"
    fi
    (( i-- ))
done

# With a for loop
for i in {20..1}
do
    if [[ $(( $i % 2 )) -ne 0 ]]
    then
        echo "$i is an odd number"
    fi
done

# You can also use the another variant of for loop
for (( i=20; i>0; i-- ))
do
    if [[ $(( $i % 2 )) -ne 0 ]]
    then
        echo "$i is an odd number"
    fi
done
```