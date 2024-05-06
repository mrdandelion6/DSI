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
