# Unix Shell

## Commands
- pwd: display present working directory
- date: display the date and time
- cal: display a calender
- whereis bash: displays path of bash
- cd <path>: navigating directories
- ls: list all files and directories
- cp <source> <destination>: copy stuff. if destination specified is a file, that file will just be overwritten (name remains same, contents change)
- mv <source> <destination>: move stuff or change name of file. can change name if destination is not a dir
- touch <file>: updates when the file was last modified (meta data)
- head <file>: displays the first 10 lines of a file
    - head -n X <file>: displays first X lines of a file
- tail <file>: displays the last 10 lines of a file
    - tail -n X <file>: displays last X lines of a file
- cut [OPTION] [FILE]: used to remove or cut out certain sections of each line from a file
    - cut -d ',' -f 1 [FILE]: for example, for CSVs if we want to display only the first field of each line you can use -d to specify the delimiter (comma in this case) and -f to specify the field number. Kind of like splitting.
- uniq [INPUT]: removes duplicate lines
- wc [FILE]: prints "lines | words | characters"
- grep [PATTERN] [FILE]: stands for global regex print. prints all lines in a file that much a specified pattern.


## Types of Files
Two main kinds
- Directories
- Executable files / Readable files (human text)

## Misc Notes
- / at the front of the path denotes root folder


## Output Redirection
- Redirecting stdout: > or >> to append
- Redirecting stderr: 2> or 2>> to append
- Both stderr and stdout: &> or &>> 

## Child Shells 
- Type bash to start a subshell. This will be in the same shell. To exit type "exit" or press Ctrl + D.

## Pipelining
- program1 | program2
Redirect the output of one program as the input of another. Examples,
- cut -d ',' -f 1 parking_tickets.csv | sort : grab the first field of each line and sort it
- cut -d ',' -f 4 parking_tickets.csv | sort | uniq | grep FIRE : grab the fourth field of each line, sort them, make the list unique, and display anything from that list that contains "FIRE"

## Arithmetic
Use $(( )) around any math. Example:
```
result=$((4 + 10))
echo $result
```

## Expansion & Variables

### Brace Expansion
Used to make arbitrary strings.


## Shell Scripts
Have .sh extension. Executable shell scripts files. Make sure to do the command: `chmod u+x myscript.sh` to make your script executable.

## Executables
Can execute commands / programs. If you type a command in directly into bash like this:

```
command
```

 your system looks for the command in directories in the PATH environment variable. Those directories are typically in `/user/bin/` and `/usr/local/bin`.

To run executables in a specific directory (ones not in that PATH that you made perhaps), then you must provide the full path instead of just the executable name. For example if you have a shell script named myscript.sh in your pwd, you would type the following:

```
./myscript.sh
```

## Variables


## Functions

Two syntax for specifying functions in bash:

With function keyword:
```
function greet() {
    echo "hello"
}
```

Without function keyword:
```
greet() {
    echo "hello"
}
```

Strangely enough, it actually doesn't matter whether we use this keyword or not. However using the function keyword is not part of the POSIX shell standard.

## Shebangs
One example is using #!/bin/bash. You put this at the start of a shell script to tell the system to execute the script with bash.
