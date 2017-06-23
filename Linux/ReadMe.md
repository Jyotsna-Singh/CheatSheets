# Linux Commands - CheatSheet
<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Linux/tux.jpg" />
</p>

## Navigation commands
| # | Command            | Description                                                                                                     |
|---|--------------------|-----------------------------------------------------------------------------------------------------------------|
| 1 | `pwd`              | It stands for print working directory, It simply print the absolute path name of your current working directory |
| 2 | `cd thisdirectory` | It stands for change directory, and it simply change your current directory to this directory                   |
| 3 | `cd /`             | Changes to your root directory                                                                                  |
| 4 | `cd ~`             | Changes to your home directory                                                                                  |
| 5 | `cd ..`            | Changes to your parent directory                                                                                |
| 6 | `cd .`             | Doesn't do anything !                                                                                           |
| 7 | `cd -`             | Changes to your previous directory                                                                              |
| 8 | `ls`                | Stands for list, It simply lists all the files on your current working directory                                |


## Using ls like cd
| # | Command                 | Description                                                                                                                                                                       |
|---|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `ls /`                  | This will list the files in your root directory                                                                                                                                   |
| 2 | `ls ~`                  | This will list the files in your home directory                                                                                                                                   |
| 3 | `ls ..`                 | This will list the files of your parent directory                                                                                                                                 |
| 4 | `ls /home/user/Desktop` | Here we are using the absolute pathname to list the files that are present on user's Desktop.,Put your username instead of user to see the files that are present on your desktop |
| 5 | `ls ~/Desktop`          | Here we are using the relative pathname to list the files that are present on your Desktop.            |


## ls command options

| # | Command  | Description                                                                                                                                                             |
|---|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `ls -a` | This will list all the files in your current working directories including hidden files that start with .                                                               |
| 2 | `ls -l` | That's a long listing that we saw before, It shows many impotant information about a file. Permssions,Number of Links,Owner,Group,File size,Modification Date,File name |
| 3 | `ls -t` | This will list the files sorted by modification date. Newest first                                                                                                      |
| 4 | `ls -r` | This will list the files in reversed fashion.                                                                                                                           |
| 5 | `ls -i` | This will list the index node number of each file in the current working directory                                                                                      |
## rm options

| # | Command | Description                                                                                                                                                                                                                                                          |
|---|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `rm -i` | Prompt you before removing any existing file. It's kind of like a double check policy.You use it when you want to make sure that you are aware of every file you remove.If this option is not specified, rm will silently dielete filesi here means interactive mode |
| 2 | `rm -f` | Never prompt you before removing a file. And will not display a warning message if the file you are trying to remove doesn't exist, Meaning that it will ignore non existant files.f here means force (forcefully remove files)                                      |
| 3 | `rm -v` | Verbose mode (print the name of each file before removing it). It explains what is being done all the time.v here means verbose.                                                                                                                                     |
| 4 | `rm -R` | Recursively delete files.If the file is a directory, remove the entire directory and all its contents, including subdirectories. To delete a directory, this option must be specified. R here means Recursive                                                        |
| 5 | `rm -r` | Same like rm -R                                                                                                                                                                                                                                                      |


## rm examples

| # | Command             | Description                                                                                 |
|---|---------------------|---------------------------------------------------------------------------------------------|
| 1 | `rm file1`          | Delete file1 silently                                                                       |
| 2 | `rm -i file1`       | Before deleting file1, prompt the user for confirmation                                     |
| 3 | `rm -r file1 dir1`  | Delete file1 and dir1 and its contents. Ofcourse, we mean the contents of dir1              |
| 4 | `rm -rf file1 dir1` | Same as above, except that if either file1 or dir1 does not exit, rm will continue silently |


## cp options

| # | Command | Description                                                                                                                                                                      |
|---|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `cp -i` | Before overwriting an existing file, prompt the user for confirmation.If this option is not specified. cp will silently overwrite files by default.i here means interactive mode |
| 2 | `cp -v` | Verbose mode (print the name of each file that was copied). It explains what is being done all the time.v here means verbose.                                                    |
| 3 | `cp -R` | Recursively copy directories and their contents.Just like the rm command, this option must be specified when copying a directoryR here means Recursive                           |
| 4 | `cp -r` | Same like cp -R                                                                                                                                                                  |

## cp examples

| # | Command                  | Description                                                                                                                                            |
|---|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `cp file1 file2`         | Make a copy of file1 named file2. If file2 exists, it is overwritten with the contents of file1.                                                       |
| 2 | `cp -i file1 file2`     | Same as above. But if file2 exists, the user is prompted before it is overwritten.                                                                     |
| 3 | `cp -r file1 dir1 dir2` | Copy file1 and dir1 into dir2. The destination dir2 must exists for the command to execute.                                                            |
| 4 | `cp -r dir1 dir2`       | Here we have two cases.If dir2 exist then dir1 will be copied into dir2.If dir2 doesn't exist then, dir2 will be created which is just a copy for dir1 |


## mv options

| # | Command | Description                                                                                                                                                                      |
|---|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | `mv -i` | Before overwriting an existing file, prompt the user for confirmation.If this option is not specified. mv will silently overwrite files by default.i here means interactive mode |
| 2 | `mv -v` | Verbose mode (print the name of each file that was moved or renamed). It explains what is being done all the time.v here means verbose.                                          |

## mv examples

| # | Command              | Description                                                                                                            |
|---|----------------------|------------------------------------------------------------------------------------------------------------------------|
| 1 | `mv file1 file2`     | Rename file1 to file2. If file2 exists, it is overwritten with the contents of file1.                                  |
|   | `mv -i file1 file2`  | Same as above. But if file2 exists, the user is prompted before it is overwritten.                                     |
|   | `mv file1 dir1 dir2` | Copy file1 and dir1 into dir2. The destination dir2 must exists for the command to execute.                            |
| 2 | `mv dir1 dir2`       | Here we have two cases.If dir2 exist then dir1 will be moved into dir2.If dir2 doesn't exist then, rename dir1 to dir2 |

## Keyboard Shortcuts

| #  | Command  | Description                                                                                                   |
|----|----------|---------------------------------------------------------------------------------------------------------------|
| 1  | Ctrl + A | Move your cursor to the beginning of the line                                                                 |
| 2  | Ctrl + E | Move your cursor to the End of the line (E ­­ > end)                                                          |
| 3  | Ctrl + D | Delete the character at the cursor location                                                                   |
| 4  | Ctrl + F | Move your cursor Forward one character. Same as your right arrow key                                          |
| 5  | Ctrl + B | Move your cursor Backward one character. Same as your left arrow key                                          |
| 6  | Alt + F  | Move your cursor Forward one word (Jump to the next word)                                                     |
| 7  | Alt + B  | Move your cursor Backward one word (Jump to the previous word)                                                |
| 8  | Alt + L  | Convert all the characters beginning from the cursor location to end of the word to Lowercase.                |
| 9  | Alt + U  | Convert all the characters beginning from the cursor location to end of the word to Uppercase.                |
| 10 | Ctrl + K | Cut the text from the cursor location to the end of the line. In Linux, we say Kill text (Just like Cut text) |
| 11 | Ctrl + U | Cut the text from the cursor location to the beginning of the line.                                           |
| 12 | Ctrl + Y | Paste the text that you did cut. Pasting in Linux is Yanking                                                  |
| 13 | Ctrl + L | Clear the screen just like the clear command                                                                  |
