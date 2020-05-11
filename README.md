GitHub Notes
==========

### One Computer Two Git Accounts
  - Link: https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574
  - Differences for the second Git:
    - git push git@github-JustinNew:JustinNew/GitHubNotes.git
    - git pull git@github-JustinNew:JustinNew/GitHubNotes.git

### Create a branch 

[This](https://confluence.atlassian.com/bitbucket/branching-a-repository-223217999.html) is a good link for instructions.

```sh
# Check branches
git branch

# Create a feature branch
git branch <feature_branch>

# Delete local branch
git branch -d <local_branch_name>

# Switch to the feature branch and work on it
git checkout <feature_branch>

# Commit the change to the feature branch
git add . 
git commit -m "adding a change from the feature branch"

# Show the changes have been made after "git add" and "git commit -m"  
Git show

# Discard changes made
git checkout -- <file>

# Switch back to the master branch
git checkout master

# Push the feature branch to Bitbucket
git push origin <feature_branch>

# git fetch vs git pull
# git pull = git fetch + git merge

# Already commited and pushed, but want to restore to master version for one file
# restore one file to master version
git checkout origin/master filename
```

### Clone a single branch

```
# Check branches
git branch -a

# Check the repo name
git config --get remote.origin.url

# Clone a remote branch
git clone -b jianhui/pickup_next_day --single-branch git@github.com:instacart/carrot.git

# Checkout to the cloned branch
git checkout -b jianhui/pickup_next_day origin/jianhui/pickup_next_day
```

### Use Git with RStudio

  - Follow this [link](https://jennybc.github.io/2014-05-12-ubc/ubc-r/session03_git.html).

### Rebase 

```sh
git fetch
git checkout my-new-feat
git rebase origin/master
```

### Check log for one user
```sh
git log --author=justincart
```

### Undo last push / revert last push
```sh
git revert commit_number_xxx
```


### Undo last commit
```sh
echo "some changes..." > file.html
git add file.html
git commit -m "wrong commit"

# I need to reset
git reset --hard HEAD~1 (cancel changes)
# OR
git reset --soft HEAD~1 # Back to staging
git reset HEAD file.html # back to working directory
git checkout -- file.html # cancel changes

# Rewind to the known good commit
git push -f origin last_known_good_commit:branch_name
```

### Git Pull Origin Master vs Git Pull Origin/Master

  - **git pull origin master** will pull changes from the origin remote, master branch and merge them to the local checked-out branch.

  - **git pull origin/master** will pull changes from the locally stored branch origin/master and merge that to the local checked-out branch. The origin/master branch is essentially a "cached copy" of what was last pulled from origin, which is why it's called a remote branch in git parlance. This might be somewhat confusing.

  - **git pull origin mybranch**, snyc up my local branch **mybranch** with the remote branch changes.

### [Git stash](https://git-scm.com/book/en/v1/Git-Tools-Stashing)

  - Often, when you’ve been working on part of your project, things are in a messy state and you want to switch branches for a bit to work on something else. The problem is, you don’t want to do a commit of half-done work just so you can get back to this point later. The answer to this issue is the git stash command.

  - Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged changes — and saves it on a stack of unfinished changes that you can reapply at any time.

```sh
# Add changes but do not commit
git add file_changed

# stash
git stash

# list stashes
git stash list

# restore
git stash apply
```

### Revert one commit and remove one file from staging

```sh
# Reset last commit
git reset --soft HEAD~1

# Remove score_per_user.py from staging
git reset HEAD score_per_user.py
```

### Adding new things into last commit
```sh
# Edit hello.py and main.py 
git add hello.py 
git commit -m 'something'

# Realize you forgot to add the changes from main.py 
git add main.py
git commit --amend --no-edit
```

### Unmodifying a Modified File / Undo a change
```
git checkout -- <file>
```

### Merge two commits into one

  - [This link explains it well](https://stackoverflow.com/questions/2563632/how-can-i-merge-two-commits-into-one-if-i-already-started-rebase)
```sh
# Check logs
git log --pretty=oneline

# Fire command 
git rebase --interactive HEAD~2

# Edit the popup file
# The commits are ordered by commit time, meaning the last commit is the last line.
# Change (last line) last commit one *pick* to *squash*
# Save and Exit

# Another file
# Save and Exit
```

### Add An Empty Folder

  - No empty folder allowed.
  - If you really want to have the empty folder:
    - Create an empty file called **.gitkeep** in the directory, and add that.

### Clone a remote branch

  - Command line

```sh 
git checkout -b <branch-name> <origin/branch_name>
```

  - My commands

```sh
git checkout -b hourly_demand_forecasts origin/hourly_demand_forecasts
    
Checking out files: 100% (4370/4370), done.
Branch 'hourly_demand_forecasts' set up to track remote branch 'hourly_demand_forecasts' from 'origin'.
Switched to a new branch 'hourly_demand_forecasts'
```

### Errors

#### git pull does not work

```sh
git remote prune origin
```
  - This will not affect your local branches and it will not change anything remote, but it will update the local references you have to remote branches.
