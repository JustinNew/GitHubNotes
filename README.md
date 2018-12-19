GitHub Notes
==========

### One Computer Two Git Accounts
  - Link: https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574
  - Differences for the second Git:
    - git push git@github-JustinNew:JustinNew/GitHubNotes.git
    - git pull git@github-JustinNew:JustinNew/GitHubNote.git

### Create a branch 

[This](https://confluence.atlassian.com/bitbucket/branching-a-repository-223217999.html) is a goog link for insturction.

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

# Discard changes made
git checkout -- <file>

# Switch back to the master branch
git checkout master

# Push the feature branch to Bitbucket
git push origin <feature_branch>

# git fetch vs git pull
# git pull = git fetch + git merge
```

### Use Git with RStudio

  - Follow this [link](https://jennybc.github.io/2014-05-12-ubc/ubc-r/session03_git.html).

### Rebase 

```sh
git fetch
git checkout my-new-feat
git rebase origin/master
```
