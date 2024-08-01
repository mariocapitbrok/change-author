# Description

The change-author.sh script is used to rewrite the commit history of a Git repository to update the author and committer information for all past commits. This can be useful if you need to correct the name and email address associated with your commits.

The script works by:

1. Making the Script Executable:
   The script is made executable to allow it to be run.

2. Running the Script:
   The script is executed, and it uses git filter-branch to iterate through the entire commit history of the repository. For each commit, it checks if the author or committer email matches a specified old email address. If it does, the script updates the author and committer name and email to the new specified values.

3. Force Pushing the Changes:
   After the script finishes running, the updated commit history is force-pushed to the remote repository. This overwrites the existing history on the remote repository with the new corrected history.

4. Verifying the Changes:
   After force-pushing, the repository's commit history is checked to ensure that the author information has been updated correctly.

## Make the Script Executable and Run It:

```bash
chmod +x change-author.sh
./change-author.sh
```

## Force Push the Changes:

After the script has finished running, you need to force push the changes to the remote repository. Be very careful with this step, as it will overwrite the remote history:

```bash
git push --force --tags origin 'refs/heads/*'
```

## Verify the Changes:

Check the repository to ensure that the author information has been updated correctly. You can use the `git log` command to inspect the commit history.

```bash
git log --format='%h %an <%ae>' --abbrev-commit
```
