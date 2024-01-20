<!-- git rebase -->
You're on a feature branch named feature-branch.
Meanwhile, changes have been made to the main branch.
Here are the steps to perform a rebase:

Make sure you are on the feature branch:
git checkout feature-branch

Fetch the latest changes from the main branch:
git fetch origin main

Rebase your feature branch onto the latest commit of the main branch:
git rebase main

This will apply each commit from your feature-branch one by one on top of the latest commit in the main branch.

<!-- git merge -->

Checkout the Main Branch:
git checkout main

Pull the Latest Changes from the Remote Main Branch:
It's a good practice to ensure that you have the latest changes from the remote main branch before merging your feature branch:
git pull origin main

Merge the Feature Branch into Main:
git merge feature-branch


