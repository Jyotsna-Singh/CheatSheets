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
