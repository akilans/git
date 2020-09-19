# GIT for beginners

- Git is used to track the versions of files. It is a distributed version control system VCS
- SCM - Source Code Management
- SVN - Centralized Version control System - Source code & versions are in central server. SVN client checkout code & working on that. Each commits happens on the central repository.
- GIT - Distributed Version Control System. Each developer has their own repository. Each commit happens in locally. Then finally push their code into remote repository

# GIT setup

- Install git in your machine
- git config --global user.name "akilan" - Setting the name
- git config --global user.email "akil.dove@gmail.com" - Setting the email
- git config --global core.editor "gedit"
- git config --global color.ui true
- git config --list - It shows name & email
- git config user.name - It shows akilan
- All config values are located in /home/akilan/.gitconfig

# Git Basic Flow - Make Changes. Add Changes, Commit Changes

### New Repository

- git init - creating .git folder to track the changes. It is invisible

### Existing Repository

- git clone git@github.com:akilans/test-git.git

### Add,Commit, Push

- ls -la .git/ - It maintain information about the project & repository
- SVN puts a tracking file in every folder but GIT has only one folder to track all the changes
- git add . - Add all the changes made in the entire project
- git commit -m "Commit mesage" - Commits the changes with single line commit message
- git status - to check the status of the project
- git remote add origin git@github.com:akilans/test-git.git
- git push -u origin master - Push the changes to remote repo

### git logs

- git multiline commit message is a good practice & set a standard for a commit message
- git log - Shows the recent log information
- git log -n 5 - Last 5 commits
- git log --since=01-01-2017 --until=01-12-2017 Lists the logs From jan 1, 2017
- git log --grep="Ini" - Filter logs using regular expression
- git log --author="akilan" - Filter logs by author name

# Git Architecture

- Two tree Architecture - Repository & Working Copy
- Three tree Architecture - Repository , Staging Index [ Add file before commit & then commit] & Working. Git uses thi
  s one
- [Working Copy ] Create a new file- Add the file [ git add Staging] - Commit changes [ Repository]
- Each commits geneartes checksum 40 digit numebr to track. It is called commit id
- HEAD points to the last commit id

# Diff and rm

- git diff - Shows All the changes b/w working copy and Staging
- git diff file_name - Shows the changes b/w working copy and Staging
- git diff --staged - shows all the changes b/w staging and HEAD
- git diff --staged file_name - Shows the changes in the staging not working copy

- git rm file_name - remove deleted file from staging. [Also deletes the file from working directory ]
- After rename the file manualy git status shows old file deleted & new file with new name got added in the working direcory
- After adding the new filein the stagin it shows Rename
- git mv old_file_name.txt new_file_name.txt - It directly shows rename [ no need of adding & it directly goes to staging]
- git diff --color-words file_anme.txt - Shows the changes in the color diffrerence not as a two diffrent lines
- git commit -a -m "Commit message" - It adds + commits by single command [ It must be a parent directory.Deleting files not calculated]

# GIT Undo Changes

### Remove Untracked files

- git clean -n - shows what are the untracked files going to remove
- git clean -f - removes untracked files in the working directory. If the files goes to staging index it will not delete

### Undo local changes [Not went to Staging]

- git checkout -- file_name or foler_name - Here "--" indicates it is not a branch. It removes the working copy & checkout the file or folder from staging

### Undo Staging Changes [The one went to staging]

- git restore --staged hello.txt - undo changes of files or folder it went to staging.
- git reset HEAD file_name or folder_name - undo changes of files or folder it went to staging.

### Undo commited Changes

- git revert h8732h387dsdfs8s78fds - It reverts all changes made in that commit & commits the new commit
- git revert -n h8732h387dsdfs8s78fds - It reverts all changes made in that commit but it will not commit

- git commit --amend -m "commit msg" - it ignores the previous commit for that particular file & commits the new changes
- git checkout dsb8s7sd98dh87qw8 -- file_name or folder_name - checkout the older versions of file

### RESET :

- cat .git/HEAD - Shows the head ref [ .git/refs/heads/master & this show last commit hash value]
- git reset --soft HASH_value - it changes pointer to that head [ keeps untracked files,staging changes, local changes and deletes all the commit logs ]
- git reset --mixed HASH_value - It changes the pointer to that head [ changing stagind index not working directory ]
- git reset --hard HASH_value - It changes the pointer to that head [ keeps untracked files, deletes the staging changes, local changes and all the commit logs]

# Branch

- git branch -a - lists all the branches
- git pull - fetches all the branch info from remote repo
- git branch - list local branches
- git branch akilan - create local branch
- git checkout akilan - switch local branch
- git checkout -b akilan - creates branch and switches
- git add . && git commit -m "msg" && git push -u origin akilan
- git branch inba origin/inba - local branch mapped to remote branch

# Ignore files

- add .gitignore file & add the list of files & folders in regular expression format or normal way to ignore tracking
- Examples
  - .php - ignore all php files
  - !index.php - Don't ignore index.php file
  - assets/videos/ - Ignore videos directory
