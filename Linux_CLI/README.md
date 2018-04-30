# Linux Basic Commands


## Search for Email Adresses Recursively

The following grep will match all email adresses @gmail.com :

`grep -rIHEo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | grep gmail.com`

* `-r` Read all  files  under  each  directory,  recursively.
* `-I` Process a binary file as if it did not contain matching data.
* `-H` Print the file name for each match.  This is  the  default  when there is more than one file to search.
* `-E` Interpret  PATTERN  as  an extended regular expression.
* `-o` Print only the matched (non-empty) parts  of  a  matching  line, with each such part on a separate output line.

To generate list file from addresses found : 

`grep -rhIEo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | grep gmail.com | sort -u > mails.txt`

* `-h` disables filename printing
* `sort -u` removes duplicates

## List Open Files For Process

`lsof -p PID`

* PID = Process ID


## Display files and folders sorted by size

### Ascending
`du -hs ~/web/* | sort -h`

### Descending
`du -hs ~/web/* | sort -hr`
