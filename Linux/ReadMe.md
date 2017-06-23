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
