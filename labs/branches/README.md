## Branching & Merging

Branching means you diverge from the main line of development and continue to do work without messing with that main line. The way Git branches is incredibly lightweight, making branching operations nearly instantaneous, and switching back and forth between branches generally just as fast. Unlike many other VCSs, Git encourages workflows that branch and merge often, even multiple times in a day. Understanding and mastering this feature gives you a powerful and unique tool and can entirely change the way that you develop.


## Branches in a Nutshell
To really understand the way Git does branching, we need to take a step back and examine how Git stores its data.

As you may remember from What is Git?, Git doesn’t store data as a series of changesets or differences, but instead as a series of snapshots.

When you make a commit, Git stores a commit object that contains a pointer to the snapshot of the content you staged. This object also contains the author’s name and email address, the message that you typed, and pointers to the commit or commits that directly came before this commit (its parent or parents): zero parents for the initial commit, one parent for a normal commit, and multiple parents for a commit that results from a merge of two or more branches.

Let's create a new git repository to visualize this:

### On Windows (open Git Bash):
```shell
mkdir -p c:/git-repos/books
cd c:/git-repos/books
# setting main as the default branch name
git config --global init.defaultBranch main
git init
```
### On Linux & MacOS (open terminal):
```shell
cd $HOME
mkdir -p git-repos/books
cd git-repos/books
# setting main as the default branch name
git config --global init.defaultBranch main
git init
```

📋🎤 Let's start with this exercise:
```shell
# check the output of these three commands
git status
# print the current branch name
git branch
# print the refs
ls -l  .git/refs/heads/
```

Let's add a `README` to our new project and make a new commit.

```shell
echo "This project will track my favourite books" > README
git add README
git commit -m "adding README"

# print the current branch name
git branch
# print the log
git log
```
> A branch is simply a pointer (reference) to one specific commit.

🎤 Git stores the branch information inside the `.git` repository. Let's take a look inside the folder:

```shell
# list the contents inside the refs/heads folder
ls -l .git/refs/heads/

# Print the contents of main file
cat .git/refs/heads/main
```

We will be storing a list of favourite books in `books.md`. Let's start with adding a header for it. Run the commands one-by-one and observe the output:

```shell
# Adding the header to `books.md` file
echo $'List of favourite books
-----------------------' > books.md

# display the contents of books.md
cat books.md

# stage books.md
git add books.md

# make a commit
git commit -m "adding header"

# create a new branch books.
git branch books

# print git log
git log

# print the contents of main file
ls -l .git/refs/heads/

# print the contents of main and books file
cat .git/refs/heads/main
cat .git/refs/heads/books
cat .git/HEAD
```

Adding a list of books:

```shell
echo $'List of favourite books
-----------------------
Lord of the rings
Harry potter
Hamlet
The Odyssey
The Adventures of Huckleberry Finn' > books.md

# skipping the staging area as the file is already being tracked
git commit -am "first set"
```

Switching to books branch. You can also use `git checkout <branchname>`.
```
git switch books
cat books.md

cat .git/HEAD
```

Open your favourite editor and copy the below content in `books.md`. If you observe closely, you will see most of the books are same but it also has some more with their order changed:
```
List of favourite books
-----------------------
To Kill a Mocking bird
Lord of the rings
Harry potter
Hamlet
The Odyssey
The Adventures of Huckleberry Finn
Alice's Adventures in Wonderland
Catch-22
```

Make a commit:
```
git commit -am "another set"
```

Switching to main and merging with the main branch:
```
git switch main
git merge books
```

You will get:
```
Auto-merging books.md
CONFLICT (content): Merge conflict in books.md
Automatic merge failed; fix conflicts and then commit the result.
```

Print the status:
```shell
git status
```
`Output:`
```
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   books.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Resolve the conflict and print the status:
```
# resolve the conflict manually
git add books.md
# print the status again
git status
```
`Output:`
```
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   books.md
```

Commit the changes and conclude the merging:
```
git commit -m "merged"
git status
```
`Output:`
```
On branch main
nothing to commit, working tree clean
```