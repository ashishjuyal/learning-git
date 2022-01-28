## Making First Commit

Let's add the `README` file to the staging area and check the `git status`. You'll see `README` and `index.html` are staged for commit.

```
On branch master
No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README
        new file:   index.html
```

Let's make our first commit:

```shell
# The commit command performs a commit, and the -m "message" adds a message.
git commit -m "making my first commit"
```

check the status:
```
git status
```

## Skipping the staging area
The staging area is amazingly useful for crafting commits exactly how you want them, however, sometimes you have a lot of modified files and you don't want to add them all one-by-one in the staging area. Sometimes it feels a bit more complex than you need in your workflow.

To skip the staging area, Git provides a simple shortcut. Adding the `-a` option to the `git commit` command makes Git automatically stage every file **`that is already tracked`** before doing the commit, letting you skip the `git add` part:

Let's make changes to `README` and use `git commit -a` to commit it without staging (skipping `git add`).
```
echo "Adding a new line to test git commit -a" >> README
git status
git commit -a -m "skipping the staging area"
```

📋🎤 Create a new file with some content and name it as `NOTES`. Use the `git commit -a` and check if it allows you to skip the staging area:

<details>
  <summary>Not sure how?</summary>

```shell
# creating a new file
echo "this file will contain my notes" > NOTES
git status
# this will not commit
git commit -a -m "trying to skip the staging area for a newfile NOTES"
git status
```
You will see the NOTES file was not committed. New files have to be added using `git add`. The `git commit -a` works only with already tracked files.

</details>
<br>

## Summary
> In this section, we learned to make a commit and also learned to skip the staging area for already tracked files. In the next section we will learn to tell git, not to track certain files. Many times you will have a set of files which you don't want Git to track. This will be the topic of next section [Ignoring files](ignore.md).
