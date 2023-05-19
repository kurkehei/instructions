# Git commands and notes

## .gitignore
Git can be instructed to not track certain files by using a **_.gitignore_** file. This file contains a list of all files that should be ignored and not tracked by Git. A collection of useful .gitignore template files provided by GitHub can be found [here](https://github.com/github/gitignore).

## GitHub repository
An SSH key must be created and added to the GitHub account to allow connections to remote repositories. This can be done by following the instructions [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

1. Press the green 'New' button on the GitHub homepage to create a new repository.

2. Give the repository a name and choose if it is a private or public repo. Do not choose to add the README, .gitignore, and license files at this stage.

3. Create a local directory and repository using the command line.

```
mkdir <directory> && cd <directory>
git init
```

4. Create the **_README.md_** and **_.gitignore_** files.

5. Connect to the remote repository.

```
git remote add origin git@github.com:<username>/<repo-name>.git
```

6. Create the **_main_** branch.

```
git branch -M main
```

7. Push the local repository to the new remote repository on GitHub.

```
git push -u origin main
```

## Git commands

### Repository configurations

| Command                                                                     | Description                                        |
| --------------------------------------------------------------------------- | -------------------------------------------------- |
| `git init`                                                                  | Creates a new repository in the current directory. |
| `git clone ssh://git@github.com/<username>/<repo-name>.git`                 | Clones a remote repository on the local machine.   |
| `git remote set-url origin ssh://git@github.com/<username>/<repo-name>.git` | Change remote repository url                       |

### Staging

| Command              | Description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| `git status`         | Displays the state of the working directory and the staging area. |
| `git add <filename>` | Adds the file or directory to the staging area.                   |
| `git rm <filename>`  | Removes the file or directory from the staging area.              |

### Commiting

| Command                               | Description                                                                                                         |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `git commit -m "Commit message here"` | Commits any staged files and adds a short message that briefly describes the changes.                               |
| `git log [--summary] [--oneline]`     | Outputs a log of all commits made, including the commit ID and message.                                             |
| `git revert <commit_ID>`              | Reverts the repository to the commit specified by the ID. Does not delete the commits made after the specified one. |
| `git reset <commit_ID>`               | Same as the revert command but deletes all commits made after the specified commit.                                 |

### Changes

| Command                          | Description                                                               |
| -------------------------------- | ------------------------------------------------------------------------- |
| `git diff`                       | Shows differences between files that are not staged yet                   |
| `git diff -staged`               | Shows difference between files in the staging area and the latest version |
| `git diff <branch-1> <branch-2>` | Differences between the two branches                                      |

### Updating changes

| Command     | Description                                                                      |
| ----------- | -------------------------------------------------------------------------------- |
| `git fetch` | Checks for updates in the remote repository.                                     |
| `git pull`  | Same as the fetch command but downloads any new changes to the local repository. |
| `git push`  | Uploads the changes made on the local repository to the remote repository.       |

### Branches

| Command                                                             | Description                                     |
| ------------------------------------------------------------------- | ----------------------------------------------- |
| `git branch`                                                        | View all branches in the repository.            |
| `git branch <branch-name>`                                          | Creates a new branch with the given name.       |
| `git branch -D <branch-name>`                                       | Deletes the local branch.                       |
| `git branch -m <current-name> <new-name>`                           | Rename a local branch                           |
| `git branch --track <new-local-branch> origin/<remote-base-branch>` | New local branch based on the remote branch.    |
| `git push origin`                                                   | Pushes the named branch to GitHub.              |
| `git push --delete origin/<remote-branch-name>`                     | Deletes a remote branch.                        |
| `git merge <source-branch> <target-branch>`                         | Merge the source branch into the target branch. |
| `git checkout <branch-name>`                                        | Switch to the named branch.                     |
| `git checkout -b <branch-name>`                                     | Create and switch to the named branch.          |
