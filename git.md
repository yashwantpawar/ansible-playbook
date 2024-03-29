# git rebase
You're on a feature branch named feature-branch.
Meanwhile, changes have been made to the main branch.
Here are the steps to perform a rebase:

1. Make sure you are on the feature branch:
```
git checkout feature-branch
```

2. Fetch the latest changes from the main branch:
```
git fetch origin main
```

3. Rebase your feature branch onto the latest commit of the main branch:
```
git rebase main
```

This will apply each commit from your feature-branch one by one on top of the latest commit in the main branch.

# git merge

1. Checkout the Main Branch:
```
git checkout main
```

2. Pull the Latest Changes from the Remote Main Branch:
It's a good practice to ensure that you have the latest changes from the remote main branch before merging your feature branch:
```
git pull origin main
```

3. Merge the Feature Branch into Main:
```
git merge feature-branch
```

# git commands

### list branches in git: 

list local branches: 
```
git branch
```

list remote branches: 
```
git branch -r
```
### create branch in git: 

create new local branch
```
git branch branch_name
```
Switch to the new branch
```
git checkout branch_name
```
create a new branch named branch_name and switch to it
```
git checkout -b branch_name
```
push the local branch to a remote repository and create a remote branch with the same name
```
git push origin branch_name
```

### delete branch in git: 

To delete a local branch in Git, you can use the following command: 
```
git branch -d branch_name
```

If the branch has unmerged changes, Git will prevent you from deleting it unless you force the deletion using -D: 
```
git branch -D branch_name
```

To delete a remote branch, you can use the git push command with the --delete option: 
```
git push origin --delete branch_name
```

### Deleting the Last Commit (Not Pushed Yet):
If the commit you want to delete is the latest commit and hasn't been pushed to the remote repository, you can use the git reset command. This command will remove the last commit and leave the changes in your working directory.

```
git reset --hard HEAD^
```

This command moves the HEAD pointer and the branch pointer back one commit (^ means the previous commit). The --hard option discards the changes introduced by the last commit.

### Deleting a Commit (Already Pushed):
If the commit has been pushed to a remote repository, it's not recommended to use git reset because it modifies history, and force-pushing can disrupt collaboration.

Instead, use git revert to create a new commit that undoes the changes introduced by the commit you want to delete:

```
git revert <commit-hash>
```

Replace commit-hash with the hash of the commit you want to delete. This command creates a new commit that undoes the changes introduced by the specified commit.

### Force Push (If Necessary):
After using git reset --hard or git revert, if you made changes to your local branch, you might need to force-push your changes to the remote repository. Be cautious with force pushes, especially on shared branches, as it rewrites history.

```
git push origin <branch-name> --force
```

Replace branch-name with the name of your branch.

### git cherry-pick
Find the Commit to Cherry-Pick: First, identify the commit you want to apply to your current branch. You can find the commit hash using git log.
```
git log
```
Switch to the Target Branch: Make sure you are on the branch where you want to apply the changes.
```
git checkout target_branch
```
Cherry-Pick the Commit: Use the git cherry-pick command followed by the commit hash you want to apply.
```
git cherry-pick <commit_hash>
```
This applies the changes from the specified commit to your current branch.


### git squash
Git squash is a technique used to combine multiple commits into a single commit. This is often done to create a cleaner, more concise commit history, especially before merging changes into a main or master branch. Squashing commits is helpful for making the commit history more readable and easier to understand.

Here's an example of how to use git squash:

Suppose you have the following commit history on a feature branch:
```
* commit A: Implement feature X
* commit B: Fix bug in feature X
* commit C: Refactor code in feature X
```
If you want to squash these three commits into a single commit, you can follow these steps:

1. Start an interactive rebase:
```
git rebase -i HEAD~<number-of-commits>
```
2. Mark commits for squash:
Change the word "pick" to "squash" (or just "s") for the commits you want to squash. Your rebase file might look like this:
```
pick A Implement feature X
squash B Fix bug in feature X
squash C Refactor code in feature X
```
Save and close the file.

3. Edit the commit message:
Another window will open, allowing you to edit the commit message for the squashed commit. You can keep the existing messages or create a new one. Save and close the file.

4. Force-push the changes:
Since the commit history has been rewritten, you'll need to force-push the changes to update the remote branch:
```
git push origin <branch-name> --force
```
