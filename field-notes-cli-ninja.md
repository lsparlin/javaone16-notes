# Field Notes of a Command Line Ninja
Rustam Mehmandarov @rmehmandarov
 * javaBin [Norwegian JUG] Leader
 * architect for 10 years

### Sudo Tidbit
 `sudo !! # sudo previous command` 

## History command
 * `history`  - shows prev commands
 * `ctrl + r` - search your history
 * `ctrs + shift + r` - reverse
 * `!` - search shorthand
   * `![?]cat[:p]` - Finds and runs last command with found text, `:p` mean do not execute
   * `!$` - last argument of last command - also supports `:p`
   * `!^:p` - first argument of last command
   * `!*:p` - all arguments of last command
 * `^badcmd^correctcmd`  will replace command and keep parameters

## Aliases
 * `alias aname='command'`
 * `unalias`

## Expansions
 * `touch myfile{2..10}.txt` - creates 9 files myfile2.txt - myfile10.txt
 * `mv myfile{1,-old}.txt` renaming
 * 

## Useful Commands
 * `type` and `which` 
 * `apropos downloader` - search for command that relates to the keyword
 * `tree` - ?
 * `bc` command line repl calculator - or pipe param into it
 * `<<word` - defines own end of file keyword
 * `lsof` - what is using the file?
 * `sl` - train?
 * `telnet star wars thing` ??? where is this
 * `python -m SimpleHTTPServer`

## Examples IRL
 * `ls -thor` :D
 * 
