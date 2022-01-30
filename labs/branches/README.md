## Branching

Branching means you diverge from the main line of development and continue to do work without messing with that main line.

Let's create a new git repository for this exercise
### On Windows (open Git Bash):
```shell
mkdir -p c:/git-repos/branches
cd c:/git-repos/branches
# setting main as the default branch name
git config --global init.defaultBranch main
git init
```
### On Linux & MacOS (open terminal):
```shell
cd $HOME
mkdir -p git-repos/branches
cd git-repos/branches
# setting main as the default branch name
git config --global init.defaultBranch main
git init
```

🎤 Let's start with this exercise:
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
# print the refs
ls -l  .git/refs/heads/
# print the contents of main file
cat .git/refs/heads/main
```

🎤 Discuss:

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
git commit -m "Adding the header for favourite books"

# create a new branch books.
git branch books

# print git log
git log

# print the contents of main file
ls -l .git/refs/heads/

# print the contents of main and books file
cat .git/refs/heads/main
cat .git/refs/heads/books
```

> A branch is simply a pointer (reference) to one specific commit.

🎤 Git stores the branch information inside the `.git` repository. Let's take a look inside the folder:

```shell
# list the contents inside the refs/heads folder
ls -l .git/refs/heads/

# There are two files, print the contents of both the files
cat .git/refs/heads/main
cat .git/refs/heads/books
```
