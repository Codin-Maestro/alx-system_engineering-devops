## 0x02. Shell, I/O Redirections and filters

[0-hello_world](./0-hello_world) - Write a script that prints “Hello, World”, followed by a new line to the standard output.

[1-confused_smiley](./1-confused_smiley) - Write a script that displays a confused smiley "(Ôo)'.
#!/bin/bash
echo "\"(Ôo)'"



[2-hellofile](./2-hellofile) - Display the content of the /etc/passwd file.
#!/bin/bash
cat /etc/passwd



[3-twofiles](./3-twofiles) - Display the content of /etc/passwd and /etc/hosts
#!/bin/bash
cat /etc/passwd /etc/hosts



[4-lastlines](./4-lastlines) - Display the last 10 lines of /etc/passwd
#!/bin/bash
tail -n 10 /etc/passwd



[5-firstlines](./5-firstlines) - Display the first 10 lines of /etc/passwd
#!/bin/bash
head -n 10 /etc/passwd




[6-third_line](./6-third_line) - Write a script that displays the third line of the file iacta.
The file iacta will be in the working directory. 
You’re not allowed to use sed
#!/bin/bash
head -n3 iacta |tail -n1



[7-file](./7-file) - Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.
#!/bin/bash
 echo "Best School" > '\*\\'\''"Best School"\'\''\\*$\?\*\*\*\*\*:)'



[8-cwd_state](./8-cwd_state) - Write a script that writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.
#!/bin/bash
ls -la > ls_cwd_content



[9-duplicate_last_line](./9-duplicate_last_line) - Write a script that duplicates the last line of the file iacta
The file iacta will be in the working directory
#!/bin/bash
tail -n 1 iacta >> iacta



[10-no_more_js](./10-no_more_js)- Write a script that deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.
#!/bin/bash
find . -type f -name '*.js' -delete



[11-directories](./11-directories) - Write a script that counts the number of directories and sub-directories in the current directory.
The current and parent directories should not be taken into account
Hidden directories should be counted
#!/bin/bash
find . -mindepth 1 -type d | wc -l



[12-newest_files](./12-newest_files) - Create a script that displays the 10 newest files in the current directory.
Requirements:
One file per line
Sorted from the newest to the oldest
#!/bin/bash
ls -t1 | head -n 10



[13-unique](./13-unique) - Create a scripts that takes a list of words as input and prints only words that appear exactly once.
Input format: One line, one word
Output format: One line, one word
Words should be sorted
#!/bin/bash
sort | uniq -u



[14-findthatword](./14-findthatword) - Display lines containing the pattern “root” from the file /etc/passwd (grep it)
#!/bin/bash
egrep 'root' /etc/passwd




[15-countthatword](./15-countthatword) - Display the number of lines that contain the pattern “bin” in the file /etc/passwd
#!/bin/bash
egrep -c 'bin' /etc/passwd

or 

#!/bin/bash
 grep 'bin' /etc/passwd | wc -l




[16-whatsnext](./16-whatsnext) - Display lines containing the pattern “root” and 3 lines after them in the file /etc/passwd.
#!/bin/bash
egrep -A 3 'root' /etc/passwd



[17-hidethisword](./17-hidethisword) - Display all the lines in the file /etc/passwd that do not contain the pattern “bin”.
#!/bin/bash
egrep -v 'bin' /etc/passwd



[18-letteronly](./18-letteronly) - Display all lines of the file /etc/ssh/sshd_config starting with a letter.
include capital letters as well
#!/bin/bash
egrep ^[[:alpha:]] /etc/ssh/sshd_config




[19-AZ](./19-AZ) - Replace all characters A and c from input to Z and e respectively.
#!/bin/bash
tr 'A' 'Z' | tr 'c' 'e'




[20-hiago](./20-hiago) - Create a script that removes all letters c and C from input.
#!/bin/bash
tr -d "cC"



[21-reverse](./21-reverse) - Write a script that reverse its input.
#!/bin/bash
rev




[22-users_and_homes](./22-users_and_homes) - Write a script that displays all users and their home directories, sorted by users.
Based on the the /etc/passwd file
#!/bin/bash
cut -f 1,6 -d ':' /etc/passwd | sort




[100-empty_casks](./100-empty_casks) - Write a command that finds all empty files and directories in the current directory and all sub-directories.
Only the names of the files and directories should be displayed (not the entire path)
Hidden files should be listed
One file name per line
The listing should end with a new line
You are not allowed to use basename, grep, egrep, fgrep or rgrep
#!/bin/bash
find . -empty -printf "%f\n"



[101-gifs](./101-gifs) - Write a script that lists all the files with a .gif extension in the current directory and all its sub-directories.
Hidden files should be listed
Only regular files (not directories) should be listed
The names of the files should be displayed without their extensions
The files should be sorted by byte values, but case-insensitive (file aaa should be listed before file bbb, file .b should be listed before file a, and file Rona should be listed after file jay)
One file name per line
The listing should end with a new line
You are not allowed to use basename, grep, egrep, fgrep or rgrep
#!/bin/bash 
find . -type f -name "*.gif" -printf "%f\n" | rev | cut -d '.' -f2- | rev | LC_ALL=C sort -f




[102-acrostic](./102-acrostic) - An acrostic is a poem (or other form of writing) in which the first letter (or syllable, or word) of each line (or paragraph, or other recurring feature in the text) spells out a word, message or the alphabet. The word comes from the French acrostiche from post-classical Latin acrostichis). As a form of constrained writing, an acrostic can be used as a mnemonic device to aid memory retrieval. Read more.
Create a script that decodes acrostics that use the first letter of each line.
The ‘decoded’ message has to end with a new line
You are not allowed to use grep, egrep, fgrep or rgrep
#!/bin/bash
echo "$(cut -c 1 | tr -d '\n')"


[103-the_biggest_fan](./103-the_biggest_fan) - Write a script that parses web servers logs in TSV format as input and displays the 11 hosts or IP addresses which did the most requests.
Order by number of requests, most active host or IP at the top
You are not allowed to use grep, egrep, fgrep or rgrep
#!/bin/bash
tail -n +2 | cut -f 1 | sort | uniq -c | sort -nr | head -11 | cut -c 9-
