# BASH notes
## Linux
### Gottcha's
- Monitors, keyboards, directories ----> they are all files!
- Linux doesn't care about the extension e.g. you can rename image.png to
image.txt and it will still be an image
  - However, software WILL care about the extension
- Case sensitive
- Avoid naming things with spaces unless you want to escape every time
```bash
mkdir my documents
mkdir "my documents"
cd my\ documents/
```
- Hidden files and folders with `.` at the beginning of the name
  - Can check for hidden files with `ls -a` or `ll -a`
- rm to remove
  - rm -rf directories
- flags for bash commands are options i.e. -a, -u
  - check options using `man {command}`
## Head, Tail, Sort
### Head
-Head displays the first X lines of a file
- Syntax is ``head {options} {file}``
- One option is `head -n{number} {file}` which will get the first {number} lines
 e.g. first 5 or first 50
### Tail
- Tail displays the last X lines of a file
- Syntax is ``tail {options} {file}``
- One option is `tail -n{number} {file}` which will get the last {number} lines
 e.g. first 5 or first 50
- Default for both of them is 10 lines
### Sort
- Shows a sorted version of the data (by default it sorts alphabetically)

## Permissions
- Define what a user or process can do to a file or folder e.g. write to it,
read from it etc.
- To change file permissions we use the `chmod` command followed by the permission level and file we would like to edit.
- `chmod 666 example_file.txt`
- Permissions use binary, execute is 1, write is 2, read is 4
  - Can add these together e.g. read + write would be 6, all of them together
  would be 7 etc.

| Value | Meaning                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------ |
| 777   | No restrictions, anyone can do anything. Not advised.                                            |
| 755   | The file's owner may read, write and execute the file. All others may read and execute the file. |
| 700   | The file's owner may read, write and execute the file. Nobody else has any rights.               |
| 666   | All users may read and write the file                                                            |
| 644   | The owner may read and write a file while all others may only read the file                      |
| 600   | The owner may read and write a file, all others have no rights                                   |

- You can also change permissions using flag names.
- For example: `chmod +x <filename>`
- Adding `+x` will make the file executable
- Adding `-w` will remove the write permissions
- Otherflags available:
  - `+r` gives read rights
  - `+w` gives write rights
- Can alias the u (user), g (group), o (other)

## Streams and Redirects
### Streams
- Streams of data are stored in memory buffers
#### Stdout
- Standard output stream (stream id 1)
- Displays output from commands in text form
- Screen is the default stdout device (generally displaying in the terminal)
#### Stdin
- Standard input stream (stream id 0)
- Provides input to commands
- Keyboard input is the default stdin device
#### Stderr
- Standard error stream (stream id 2)
- Displays error output from commands
### Redirects
- Redirecting the streams of data from their default destinations to the ones
specified in the command e.g. a file or device
#### Output redirection
- `>` used for output redirection
- `{command} > {file}` redirects output of the command to a file e.g.
`ls > contents` will take the output of the ls command and redirect it to a
file called contents
- If the contents file already exists, its content will be deleted and replaced
with the output being redirected
- `{command} >> {file}` redirects output of the command to a file **without**
overwriting it, instead appending the redirected output to the file
- Useful when the output of a command would make viewing it instantly
undesirable e.g. a command that produces a very large output
#### Input redirection
- `<`used for input redirection
- `{command} < {file}` will take the content of a file and redirect it to the
command
#### Pipe redirection
-  `command1 | command2` can connect the output of one command to the input of
another
- This can be done pipe together as many commands as you want as long as it
makes sense to do so i.e. the latter command can reasonably take in the output
of the former command
#### Error redirection
- Can redirect the contents of a stderr stream with the output redirection
symbols `2>` and `2>>` as it is an output data stream
- Can differentiate between stdout and stderr by their differing stream id's
- This can be seen in the above example, as 2 is the stream id for stderr
- An example of it being used is below, which will redirect the error stream
into the error.txt file.
`ls fffff 2> error.txt`

## Wildcards
- Characters that act in place of other characters
- ``*`` can be used in place of any sequence of characters
  - `*md` would find any file ending in md
- ``?`` can be used to search for a fixed number of characters, each ?
symbolises each character
  - ``???.txt`` will find files with a 3 character long name
- ``[]`` can be used to match the characters of a defined range or group of
characters
  - ``[a-d].txt`` will find files with names that only include characters
  between a and d e.g. it could find bad.txt

## Greps and ps aux
- Grep is used to search for string/text from a file or from the output of
another command
- It returns the lines where it finds a match
- We can also use grep to return the lines where it doesn't match, by using
``grep -v```
- ``ps`` shows a list of processes and their process id's
- ``ps -a`` shows the processes from all users
- ``ps -u`` shows the processes alongside the users
- ``ps -x`` shows the processes not attached to the current terminal
- ``ps aux`` shows the processes that are running regardless from where they
have been executed
- Can kill a process with `kill {process id}`
- Can make a process run in the background with `&` e.g. `{process start} &` so
that you can still use the terminal
