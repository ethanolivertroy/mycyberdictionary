# Reset A Git Repo to a Specific Commit

To reset a Git repository to a specific commit, you can use the `git reset` command. This command moves the branch pointer to a specified commit and updates the staging area and working directory accordingly. Here's how you can do it:

1. Open a terminal or command prompt and navigate to the directory of your Git repository.

2. Ensure you are on the branch you want to reset. You can use the command `git branch` to see the available branches and `git checkout <branch_name>` to switch to a specific branch.

3. Find the commit hash of the specific commit you want to reset to. You can use `git log` to see the commit history and find the commit hash associated with the desired commit.

4. Once you have the commit hash, use the following command to reset the repository to that commit:

   ```shell
   git reset --hard <commit_hash>
   ```

   Replace `<commit_hash>` with the actual hash of the commit you want to reset to. For example:

   ```shell
   git reset --hard abc1234
   ```

   This command will move the branch pointer to the specified commit, discarding any changes and making the repository match the state of that commit.

   **Note:** Be careful when using `git reset --hard` as it discards any changes and cannot be undone easily. Make sure you have a backup of any important changes before performing a hard reset.

After executing the `git reset` command, your repository should be reset to the specified commit.

After resetting your local Git repository to a specific commit, you can push the changes back to GitHub. However, note that you will need to force-push since you are rewriting the commit history. Here are the steps to follow:

1. Make sure you have the remote repository (GitHub repository) added as a remote in your local Git repository. You can check the existing remotes using the command `git remote -v`.

   If you haven't added the remote repository yet, you can add it using the following command:

   ```shell
   git remote add origin <remote_repository_url>
   ```

   Replace `<remote_repository_url>` with the URL of your GitHub repository.

2. Execute the force-push command to update the remote repository with the reset changes:

   ```shell
   git push --force origin <branch_name>
   ```

   Replace `<branch_name>` with the name of the branch you want to push. For example, if you want to push the changes to the "master" branch:

   ```shell
   git push --force origin master
   ```

   The `--force` option is necessary because you are rewriting the commit history. Keep in mind that force-pushing can be disruptive to other collaborators, so use it with caution.

After executing the push command, your changes will be pushed to the GitHub repository, and the branch will reflect the reset state you specified earlier.