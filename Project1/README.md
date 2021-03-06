# CS 1XA3 Project01 - axentia

## Usage
**To execute** this script, the script must be kept in its 'Project1' folder, as well as the 'Project1' folder to be 
placed in the root of the repo. Then, the script can be executed with the following commands while in the 
'Project1' directory:

	chmod +x project_analyze.sh

	./project_analyze arg1

There is only one required argument with possible inputs 1, 2, 3, 4, 5, 6 or 7.
**List of inputs** with corresponding feature:

	1 - FIXME Log
	
	2 - File Type Count
	
	3 - Find Tag

	4 - File Synchronization

	5 - Last Backup Date

	6 - Switch to Executable

	7 - Backup and Delete / Restore

**References:** https://linuxize.com/post/bash-functions/ how to use functions in bash to make file look cleaner.

## Feature FIXME Log
**Description:** This feature will find every file in your repo that contains the word '#FIXME' in its last line.
These files will then be recorded into a new file (or overwritting an existing file) named fixme.log.

**Execution:** To execute this file, arg1 when calling the script must be '1' as such:

	./project_analyze 1

**Reference:** How to find the last line of a file: https://kb.iu.edu/d/acrj 

## Feature File Type Count
**Description:** The user is prompted for a file extension (txt, pdf, etc). The script will then output how many files 
of that type exist in your repo.

**Exectuion:** To execute this file, agr1 when calling the script must be '2' as such:

	./project_analyze 2

As well as inputting a correct file type extension when prompted by the script.

## Feature File Tag
**Description:** The user is prompted for a single specific word or 'tag'. The script then searches for every python
 file that has a line which begins with a comment which includes the tag on that line. The file along with 
the line is then recorded into a file tag.log (named after the inputted tag).

**Execution:** To execute this file, agr1 when calling the script must by '3' as such:

	./project_analyze 3

As well as inputting one word when prompted by the script.

**Reference:** https://www.computerhope.com/unix/uegrep.htm for how to use egrep and properly format the 'pattern' when 
searching for the tag.

## Custom Feature File Synchronization
**Description:** This script will compare two files (the user will be prompted for the two file paths) line by line 
and upon discovering a line that is different between the two files, the user will be asked which line they would
like to keep. After going through each of the lines, a new file will be created composed of all the identical lines,
as well as the lines that the user specified to keep. There will also be a log created that keeps track of which
lines were kept or not kept.

**Execution:** To execute this file, agr1 when calling the script must be '4' as such:

	./project_analyze 4

The user will also be prompted for two files, which must both be in the Project1 directory, and
 upon discovering unidentical lines, the user will be prompted for which one of the two 
lines they want to keep, for which they must input '1' or '2'.

**Note:** When inputting the file names, do not place quotations around the name, even if there are spaces. If there
are spaces, the files will still work even without quotes. 
Also, the script will only run through the number of lines contained in the smaller file. Excess lines in the other
file are then skipped.

**Reference:** https://www.geeksforgeeks.org/write-bash-script-print-particular-line-file/ Learned how to use sed
to print a specific line (by number) from a file.

https://askubuntu.com/questions/442914/calculating-the-number-of-lines-in-a-file a command that returns the
number of lines in a file, including empty lines.

## Custom Feature Last Backup Date
**Description:** This script searches for all files/directories with the word 'backup' at the end of the name. For every file/directory found, 
the last date modified will be displayed (while also being recorded into a log file to keep 
track of how up to date all of your backups are) as well as prompting the user if they would like to create a new
backup of that file/directory (given that the original name is the same just without 'backup').

**Execution:** To execute this file, arg1 when calling the script must be '5' as such:

	./project_analyze 5

The user will also be prompted for every file/directory found if they would like to create a new backup, for which
they must input 'y' or 'n'.

**Reference:** https://stackoverflow.com/questions/19482123/extract-part-of-a-string-using-bash-cut-split learned
how to use parameter expansion to extract parts of string such as extracting the file extension from the string, and
extracting everything after the last '/'.

## Feature Switch to Executable 
**Description:** This feature has two options, "change" or "restore". The user will be prompted for which option upon 
execution. The "change" option will change the permissions of all .sh files so that only people who have write
permissions can have executable permissions. Original permissions are then stored in permissions.log The "restore" 
option will restore the permissions of all .sh files to the permissions stored in the permissions log file.

**Execution:** To execute this file, arg1 when calling the script must be '6' as such:

	./project_analyze 6

The user will also be prompted to enter 'c' for change, 'r' for restore, or 'q' if they want to quit without
altering any permissions.

**Reference:** https://stackoverflow.com/questions/10551981/how-to-perform-a-for-loop-on-each-character-in-a-string-in-bash
used to go through a string letter by letter to find who has read permissions.

https://superuser.com/questions/1001973/bash-find-string-index-position-of-substring another reference used for extracting
string. Used to extract the file path from the string that includes both permissions and file path. 

## Feature Backup and Delete / Restore
**Description:** This feature has two options, "backup" or "restore". The user will be prompted for which option upon execution.
The "backup" option will move all .tmp files into a directory /backup while storing original locations in /backup/restore.log.
The "restore" option will move all files from the /backup directory to their orginal locations.

**Execution:** To execute this file, arg1 when calling the script must be '7' as such:

	./project_analyze 7

The user will also be prompted to enter 'b' for backup, 'r' for restore, or 'q' if they want to quit without moving any files.
