# Git & Github Commands - CheatSheet
<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/git.png">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/github.png" width="280" height="auto"  />
</p>

## Git Terminologies
| #  | Git Command     | Description                                                                                                                                                                             |
|----|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | Bare Repository | Repository without a working directory.                                                                                                                                                 |
| 2  | Branch          | A branch is an active area of development in Git. The most recent commit shows the tip of the branch.                                                                                   |
| 3  | Blame           | Describes the last modification to every line in the file. Shows Revision, Author & Time.                                                                                               |
| 4  | Checkout        | This refers to the process in which any given commit is selected from the repository and the state of the associated file and the directory tree is recreated in the working directory. |
| 5  | Commit          | This is a single point in Git history which holds the information about a changeset.                                                                                                    |
| 6  | Diff            | A Diff is the difference in changes between two Commits, or saved changes.                                                                                                              |
| 7  | Detached Head   | The state in which a specific commit is checked out instead of a branch.                                                                                                                |
| 8  | Fetch           | Fetching means to get latest changes in the branch and the local/remote repos.                                                                                                          |
| 9  | Fork            | By Forking the repository, you will be able to add Commits and create Pull Requests.                                                                                                    |
| 10 | Hash            | A unique SHA1 code for every Commit                                                                                                                                                     |
| 11 | Head            | A named reference to the Commit at the tip of a Branch                                                                                                                                  |
| 12 | Index           | A collection of files with state information.                                                                                                                                           |
| 13 | Merge           | To bring out the content of another Branch in the current Branch.                                                                                                                       |
| 14 | Master          | The default development Branch in Git                                                                                                                                                   |
| 15 | Origin          | The default Upstream Repository                                                                                                                                                         |
| 16 | Pull Request    | Suggests changes into the Master Branch                                                                                                                                                 |
| 17 | Push            | Pushes new changes after Committing them                                                                                                                                                |
| 18 | Repository      | A collection of Commits, Branches and Tags to identify Commits.                                                                                                                         |
| 19 | Working Tree    | The tree of actual checked out files                                                                                                                                                    |

## Git Configuration

| # | Git Command                        | Description                                                           |
|---|------------------------------------|-----------------------------------------------------------------------|
| 1 | `git config –global user.name`     | Set the username to be used for all actions                           |
| 2 | `git config –global user.email`    | Set the email to be used for all the actions.                         |
| 3 | `git config –global alias`         | Create a shortcut for the Git command.                                |
| 4 | `git config –system core.editor`   | Set the text editor for all the command actions.                      |
| 5 | `git config –global –edit`         | Open global configuration file in the text editor for manual editing. |
| 6 | `git config –global color.ui auto` | Enable helpful colourization of command line outputs.                 |

