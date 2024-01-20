# git rebase
You're on a feature branch named feature-branch.
Meanwhile, changes have been made to the main branch.
Here are the steps to perform a rebase:

1. Make sure you are on the feature branch:
git checkout feature-branch

2. Fetch the latest changes from the main branch:
git fetch origin main

3. Rebase your feature branch onto the latest commit of the main branch:
git rebase main

This will apply each commit from your feature-branch one by one on top of the latest commit in the main branch.

# git merge

1. Checkout the Main Branch:
git checkout main

2. Pull the Latest Changes from the Remote Main Branch:
It's a good practice to ensure that you have the latest changes from the remote main branch before merging your feature branch:
git pull origin main

3. Merge the Feature Branch into Main:
git merge feature-branch


