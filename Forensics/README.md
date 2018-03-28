# Forensics


## Search for Email Adresses Recursively

The following grep will match all email adresses @gmail.com :

`grep -rIHEo "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" | grep gmail.com`

* `-r` Read all  files  under  each  directory,  recursively;  this  is equivalent to the -d recurse option.
* `-I` Process a binary file as if it did not contain matching data; this is equivalent to the --binary-files=without-match option. 
* `-H` Print the file name for each match.  This is  the  default  when there is more than one file to search.
* `-E` Interpret  PATTERN  as  an extended regular expression.
* `-o` Print only the matched (non-empty) parts  of  a  matching  line, with each such part on a separate output line.
