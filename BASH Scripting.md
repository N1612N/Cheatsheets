#! /bin/bash : shebang for bash

# Variables
```sh
# assign single word variables
$ first_name=Good
$ last_name=Hacker

# print variables
$ echo $first_name $last_name
Good Hacker

# user input
read -p 'Username: ' username
read -sp 'Password: ' password

# assign string as variable
$ greeting='Hello World'
$ echo $greeting
Hello World

# print with included strings
$ greeting2="New $greeting"
$ echo $greeting2
New Hello World

# Argument Variables
#!/bin/bash
echo "The first two arguments are $1 and $2"

$ ./arg.sh hello there
The first two arguments are hello and there

$0 -> script name
$1 -> argument 1 //hello
$2 -> argument 2 //world
```


Variable Name Description
$0 : The name of the Bash script
$1 - $9 : The first 9 arguments to the Bash script
$# : Number of arguments passed to the Bash script
$@ : All arguments passed to the Bash script
$? : The exit status of the most recently run process
\$$ : The process ID of the current script
$USER : The username of the user running the script
$HOSTNAME : The hostname of the machine
$RANDOM : A random number
$LINENO : The current line number in the script


Operator Description: Expression True if…
!EXPRESSION : The EXPRESSION is false.
-n STRING : STRING length is greater than zero
-z STRING : The length of STRING is zero (empty)
STRING1 != STRING2 : STRING1 is not equal to STRING2
STRING1 = STRING2 : STRING1 is equal to STRING2
INTEGER1 -eq INTEGER2 : INTEGER1 is equal to INTEGER2
INTEGER1 -ne INTEGER2 : INTEGER1 is not equal to INTEGER2
INTEGER1 -gt INTEGER2 : INTEGER1 is greater than INTEGER2
INTEGER1 -lt INTEGER2 : INTEGER1 is less than INTEGER2
INTEGER1 -ge INTEGER2 : INTEGER1 is greater than or equal to INTEGER 2
INTEGER1 -le INTEGER2 : INTEGER1 is less than or equal to INTEGER 2
-d FILE : FILE exists and is a directory
-e FILE : FILE exists
-r FILE : FILE exists and has read permission
-s FILE : FILE exists and it is not empty
-w FILE : FILE exists and has write permission
-x FILE : FILE exists and has execute permission

---
# Statements
```sh
IF Statements

if [ <some test> ]
then
<perform an action>
fi

# Example
if [ $age -lt 16 ]
then
echo "You might need parental permission to take this course!"
fi
```

```sh
IF ELSE Statement

if [ <some test> ]
then
<perform action>
else
<perform another action>
fi

# Example
if [ $age -lt 16 ]
then
echo "You might need parental permission to take this course!"
else
echo "Welcome to the course!"
fi
```

```sh
IF ELIF ELSE Statement
if [ <some test> ]
then
<perform action>
elif [ <some test> ]
then
<perform different action>
else
<perform yet another different action>
fi

# Example
if [ $age -lt 16 ]
then
echo "You might need parental permission to take this course!"
elif [ $age -gt 60 ]
then
echo "Hats off to you, respect!"
else
echo "Welcome to the course!"
fi
```

---
# Boolean Logical Operations

&& : AND
|| : OR

```sh
# Example for AND Operation
if [ $USER == 'kali' ] && [ $HOSTNAME == 'kali' ]
then
echo "Multiple statements are true!"
else
echo "Not much to see here..."
fi
```

```sh
# Example for OR Operation
if [ $USER == 'kali' ] || [ $HOSTNAME == 'pwn' ]
then
echo "One condition is true, this line is printed"
else
echo "You are out of luck!"
fi
```
---
# Loops

```sh
FOR Loops
for var-name in <list>
do
<action to perform>
done

# Example
for ip in $(seq 1 10); do echo 10.11.1.$ip; done
```

```sh
WHILE Loops
while [ <some test> ]
do
<perform an action>
done

# Example
while [ $counter -lt 10 ]
do
echo "10.11.1.$counter"
((counter++))
done
```

---
# FUNCTIONS

```sh
function function_name {
commands...
}

# Example
print_me () {
echo "You have been printed!"
}
print_me
```

---

---
