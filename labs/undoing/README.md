## Undoing things

The commands in this section should be **run with caution**. There are times when we want to undo things we did but you can't always undo some of these undos. This is one of the few areas in Git where you may lose some work if you do it wrong.

One of the common undos takes place when you commit too early and possibly forget to add some files, or you mess up your commit message. If you want to redo that commit, make the additional changes you forgot, stage them, and commit again using the `--amend` option:

This command takes your staging area and uses it for the commit. If you've made no changes since your last commit (for instance, you run this command immediately after your previous commit), then your snapshot will look exactly the same, and all you'll change is your commit message.

The same commit-message editor fires up, but it already contains the message of your previous commit. You can edit the message the same as always, but it overwrites your previous commit.

> Let's create two files, we will commit only the first one and later we will add the second one in the same commit using `--amend` option:

```shell
# adding movies
echo $'movie1\nmovie2\nmovie3\n' > movies.md
# updating books
echo "book6" >> fav-books.md

git add movies.md
git commit -m "adding movies"
```

Let's check the commit history:
```
git log --stat -n 1
```
It shows only one file is comitted. Now let's stage another file and make a commit using `amend`.

```shell
git add fav-books.md

# below command will open the editor with the last commit message. If you want, you can amend the commit message and exit the editor.
git commit --amend
```

Let's check the commit history once again:
```
git log --stat -n 2
```
`Output:` Now it will show two files in the last commit
```
commit e4eabb7d40a5fda0810ec2222553903b979d0cc3 (HEAD -> master)
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Fri Jan 28 18:19:58 2022 +0530

    adding movies

 fav-books.md | 1 +
 movies.md    | 4 ++++
 2 files changed, 5 insertions(+)
```

> `Only amend commits that are still local and have not been pushed`. Amending previously pushed commits and force pushing the branch will cause problems for your collaborators.

## Unstaging a Staged File
Let's say you've changed two files and want to commit them as two separate changes, but you accidentally type `git add *` and stage them both. How can you unstage one of the two? 
The nice part is that the command you use to determine the state of those two areas also reminds you how to undo changes to them. 

Let's make changes to two files:

```shell
echo "new book" >> fav-books.md
echo "new movie" >> movies.md

git add *
# The git status command reminds you
git status
```
`Output:`
```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   fav-books.md
        modified:   movies.md
```
Right below the "Changes to be committed" text, it says use `git restore --staged <file>...` to unstage. So, let's use that advice to unstage the `movies.md` file:

```
git restore --staged movies.md
git status
```

## Unmodifying a Modified File
What if you realize that you don't want to keep your changes to the `movies.md` file? How can you easily revert it to what it looked like when you last committed? Luckily, `git status` tells you how to do that, too. In the last example output, the unstaged area looks like this:

```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   movies.md
```
It tells you pretty explicitly how to discard the changes you've made. Let's do what it says:

```
git restore movies.md
git status
```
`Output:`
```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   fav-books.md
```
> It's important to understand that `git restore <file>` is a dangerous command. Any local changes you made to that file are gone - Git just replaced that file with the last staged or committed version. Don't ever use this command unless you absolutely know that you don't want those unsaved local changes.

📋 In this exercise you have to:
1. Unmodify the `fav-books.md` file. That means the last entry "new books" should get removed and the file should be in its last state.
2. delete `movies.md` file and restore the file

<details>
  <summary>Not sure how?</summary>

```shell
# restoring the file from staged state
git restore --staged fav-books.md
# restoring the file to its previous state
git restore fav-books.md
# delete movies.md
rm movies.md
git status
git restore movies.md
```  
</details>
<br>

## Removing the last commit
Let's suppose you have made the last commit by mistake and you want to remove the last commit. You can use `git reset` command to do that. Remember, this is a dangerous command and you should absolutely be sure of what you are doing before running this command:

```shell
# prints the SHA1 of all the commits, take a note of last commit (from the top)
git log --pretty=oneline
# removes the last commit and resets the head to the second-last commit
git reset --hard HEAD~1
# verify the output
git log --pretty=oneline
```