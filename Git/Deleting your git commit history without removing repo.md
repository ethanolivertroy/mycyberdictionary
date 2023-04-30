# Deleting your git commit history without removing repo on Github/Bitbucket


- brute-force approach
- also removes the configuration of the repository

**Note**: This does NOT work if the repository has submodules! If you are using submodules, you should use e.g. [interactive rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase-i "interactive rebase")

Step 1: remove all history (**Make sure you have a backup, this cannot be reverted**)

```
cat .git/config  # save your <github-uri> somewhere
rm -rf .git
```

Step 2: reconstruct the Git repo with only the current content

Before step 2 if you have not set up `init.defaultBranch` configuration then, please do it via `git config --global init.defaultBranch <branch-name>` you may choose `main` as `<branch-name>` in the current example

```
git init
git add .
git commit -m "Initial commit"
```

Step 3: push to GitHub.

```
git remote add origin <github-uri>
git push -u --force origin main
```