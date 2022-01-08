# How to migrate a repository

```
AUTHOR: Samuel M.H.
DATE: 24-SEP-2021
LICENCE: all rights reserved.
```



## The problem
I have a repo on GitHub, and I want to migrate it to Bitbucket.

### On the original repo.
1. Save your work on the current repo and push all.
2. Add the new remote.
```bash
git remote add <NAME_REMOTE> <URL>
```
3. Checks.
```bash
git remote -v
```
4. Push what you want to a migration branch.
```bash
git push upstream migration
```

### On the new repo
1. Get the branch
```bash
git pull migration
```
2. Merge allowing unrelated histories
```bash
git checkout master
git merge migration  --allow-unrelated-histories
```
3. Remove the migration branch
```bash
git push origin --delete -d migration
```

## References
* [1] [How to Migrate a Git Repository from Github to Bitbucket](https://www.bluelabellabs.com/blog/how-to-migrate-git-repository-from-github-to-bitbucket/?nab=2)
* [2] [How can I delete branches in Git?](https://www.git-tower.com/learn/git/faq/delete-remote-branch/)
* [3] [Working with Git remotes and pushing to multiple Git repositories](https://jigarius.com/blog/multiple-git-remote-repositories)
* [4] [Pushing commits to a remote repository](https://docs.github.com/es/get-started/using-git/pushing-commits-to-a-remote-repository)
