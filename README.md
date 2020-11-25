# BASH notes

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

agergag

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
