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
You can pipe one program's output to anothers input using `|`. Here is an example of piping output from `program1` as input for `program2`
```
program1 | program2
```

Now we show some specific examples. The following code grabs the first field of each line in a CSV file `parking_tickets.csv` and sorts it into a list before printing the results to `stdout` (stdout stands for standard output, which is usually the client console/terminal).
```
cut -d ',' -f 1 parking_tickets.csv | sort
```

The following code grabs the fourth field of each line from a CSV, sorts them, makes the sorted list unique, then filters the list to have only lines which contain the  word "FIRE", and lastly prints it to `stdout`.
```
cut -d ',' -f 4 parking_tickets.csv | sort | uniq | grep FIRE
```

## Arithmetic
Use `$(( ))` around any math. Example:
```
result=$((4 + 10))
echo $result
```

## Expansion & Variables

### Brace Expansion
Used to make arbitrary strings. I'll add notes for this later.

## Shell Scripts
Have .sh extension. Executable shell scripts files. Make sure to do the command: `chmod u+x myscript.sh` to make your script executable.

## Executables
Can execute commands / programs. If you type a command in directly into bash like this:

```
command
```

 Note that the OS looks for the command in directories in the PATH environment variable. Those directories are typically in `/user/bin/` and `/usr/local/bin` for UNIX systems.

If you want to run executables in a specific directory (ones not in that PATH that you made perhaps), then you must provide the full path instead of just the executable name. For example if you have a shell script named myscript.sh in your `pwd` (present working directory), you would type the following:

```
./myscript.sh
```

Note the `./` specifies that the path of `myscript.sh` is in the `pwd`.


## Variables
I'll make some notes on this later. Here is a basic usage example:
```
name="faisal"
echo "hello $name"
```

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

Note that if you want to use functions directly in command line without having to execute scripts in which they are defined, you have to source them as follows:
```
source path/to/script/myscript.sh
funct_x
```
The above assumes `funct_x` is some function defined in myscript.sh. This source will only last for the shell session. If you want functions to last forever then you should define them in a file that is sourced by default, such as `.bashrc`.

## Shebangs
I'll make more notes on this later but one example is using #!/bin/bash. You put this at the start of a shell script to tell the system to execute the script with bash.
