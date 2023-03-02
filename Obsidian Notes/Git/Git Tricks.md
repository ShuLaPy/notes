
### Show changes in commited files wrt dev branch

- push that branch to github/gitlab and just start creating the MR for dev branch
- It will show files changes and commites
- you can now check all the changes that you made in that branch highlighted
- when your work done just abort the MR creation process

### How do I undo the most recent local commits in Git?

```bash
git reset --soft HEAD~1
```

### Add Changes to last commit

```bash
git add the_left_out_file
git commit --amend --no-edit
```
 
>Note: This will only work if you haven't pushed the last commit.