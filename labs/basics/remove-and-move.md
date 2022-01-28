## Removing files

To remove a file from Git, you have to remove it from your tracked files (more accurately, remove it from your staging area) and then commit. The `git rm` command does that, and also removes the file from your working directory so you don’t see it as an untracked file the next time around.

If you simply remove the file from your working directory, it shows up under the "Changes not staged for commit" (that is, unstaged) area of your `git status` output:

```
rm movies.md
git status
```
`Output:`
```
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    movies.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Then, if you run `git rm`, it stages the file's removal:

```
git rm movies.md
git status
```
`Output:`
```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    movies.md
```
Finally commiting the delete:
```
git commit -m "removed movies.md"
```

## Moving files / Renaming

If you want to rename a file in Git, you can run something like:
```
git mv <file-from> <file-to>
```
`Example:`
```
git mv books.md fav-books.md
git status
```
`Output:`
```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    books.md -> fav-books.md
```
> Git considers it as a renamed file.

However, this is equivalent to running something like this:
```
$ mv books.md fav-books.md
$ git rm books.md
$ git add fav-books.md
```

> Git figures out that it’s a rename implicitly, so it doesn’t matter if you rename a file that way or with the mv command. The only real difference is that `git mv` is one command instead of three - it’s a convenience function.