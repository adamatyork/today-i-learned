# Friday 18th November 2022

**Today I Learned**
<br>

`Git` cli commands can be used to perform common git actions. <br>

## Branching

### Switching Branches
To switch between branches in your local repository, you can use a couple of commands. <br>
`git checkout branch-name` or `git switch branch-name`. <br>
Both of these commands will switch your HEAD branch to the specified branch. <br>

### Creating New Branches
To create a new branch, you can use `git branch branch-name`. 
This will make a new branch based on the currently checkedout commit. <br>
To branch off a different commit, you can specify the hashId of that commit. `git branch branch-name 0fa98f7` <br>


Instead of creating and then switching to your new branch, you can also create and switch to a branch in one command. 
`git checkout` has a `-b` argument that tells git to create the branch. <br>
`git switch` has a `-c` argument that does the same thing. <br>

`git checkout -b my-branch | git switch -c my-branch`

<br>

### Modifying Branches
You can rename branches after you've created them. <br>
`git branch` takes an `-m` argument that modifies the branch. <br>
`git branch -m new-name` will rename the current HEAD branch to the specified name. <br>

You can also rename branches that are not checked out. <br>
`git branch -m other-branch new-name` will rename other-branch to the specified name. <br>

<br>

---
<br>

## Tracking Changes
### Set Tracking
You can set a local branch to track a remote branch. <br>
This means that any changes made to the remote branch will be tracked and you can check the status and difference between the two branches at any time. <br>

To set a local branch to track a remote branch, use `git branch --track my-branch origin/my-branch` <br>
This sets a tracking relationship between the local branch 'my-branch' and the remote branch of the same name. <br>

If a branch exists remotely but not in your local repository, you can use the `--track` argument of `git checkout` to create the branch locally and also set up tracking in one command. <br>
`git checkout --track origin/my-branch` <br>
This will automatically use the same branch name as the remote branch for your local branch. <br>

You can also establish a tracking relationship when pushing a local branch to the remote repository for the first time. <br>
When you use `git push` on a local branch that doesn't yet exist in remote, you'll be prompted to specify a remote branch name to push to and track. <br>
Use `-u` or `--set-upstream` to specify the remote branch name. <br>
If the branch doesn't exit, it wil be created on remote. <br>
`git push -u origin/my-branch | git push --set-upstream origin/mybranch`

<br>

---

<br>

## Reviewing Commits
### Viewing Previous Commits
You can see a list of previous commits on your current HEAD branch with `git log`. <br>
You can also specify a branch name to view the commit log of a different branch. `git log other-branch`. <br>


`git last` will show you the latest commit log entry for your current branch.


### Comparing Commit Logs
You can see a log showing commits that exist in one branch but not the other, by using `git log my-branch..other-branch` <br>
To see a log that shows a full comparison of missing commits from both branches, use three dots in the same command. <br>
`git log my-branch...other-branch`. <br>

<br>



## Ref. Links. Etc.
[Youtube Tutorial](https://www.youtube.com/watch?v=e2IbNHi4uCI) <br>
[Git Docs](https://git-scm.com/docs) <br>
[Basic Git Overview](https://www.atlassian.com/git) <br>

