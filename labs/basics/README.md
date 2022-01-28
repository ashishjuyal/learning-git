## Getting a Git repository

There are two ways to obtain a Git repository:

1. Create a local directory and turn it in a git repository using `git init`
2. You can `git clone <url>` an existing Git repository from (GitHub, GitLab, Bitbucket, etc.)

We will start with the first option:

### On Windows (open Git Bash):
```
mkdir c:/learn-git
cd c:/learn-git
git init
```
### On Linux & MacOS (open terminal):
```
cd $HOME
mkdir learn-git
cd learn-git
git init
```
> This will create a new subdirectory named `.git` that contains all your necessary repository files. This is the local Git database. In Linux and MacOS this folder will not be visible because it starts with a `dot` that means a hidden folder. To view use `ls -la` command on the terminal.

## Cloning an existing repository
To copy an existing repository in a new folder you need to use `git clone`. Git receives a full copy of nearly all data that the server has. Every version of every file for the history of the project is pulled down by default when you run `git clone`

### On Windows (open Git Bash):
```
mkdir c:/git-repos
cd c:/git-repos
git clone https://github.com/ashishjuyal/learning-git
```
### On Linux & MacOS (open terminal):
```
cd $HOME
mkdir git-repos
cd git-repos
git clone https://github.com/ashishjuyal/learning-git
```

## Checking status of your files
The main tool to determine the state of files inside the repository is the `git status` command. Run this command inside the folder where you have your git repository (the folder with `.git` subfolder)

```
git status
```
You should see similar output as below:
```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```

## Adding new files to git repository

You will start adding new files in your repository. Open the `learn-git` folder in your favourite editor and create a new file called index.html and copy the below contents to the file.

```html
<!DOCTYPE html>
<html>
<head>
<title>Hello Git!</title>
</head>
<body>

<h1>Hello Git!</h1>
<p>This is the first file in my new Git Repo.</p>

</body>
</html>
```

Go back to the terminal and check the `git status` inside the  `learn-git` folder

```
git status
```

```
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.html

nothing added to commit but untracked files present (use "git add" to track)
```
You can see the new `index.html` file is untracked. Untracked basically means that Git sees a file you didn't have in the previous snapshot (commit), and which hasn't yet been staged.

> Files in your Git repository folder can be in one of 2 states:
 - Tracked - files that Git knows about and are added to the repository
 - Untracked - files that are in your working directory, but not added to the repository

## Tracking new files
In order to begin tracking a new file, you use the command `git add`. To begin tracking the `index.html` file, you have to run this:

```
git add index.html
```

📋 Check the status of the `index.html` file in the repository.

<details>
  <summary>Not sure how?</summary>

```
git status
```
</details>
<br>

📋 Create a new `README` file with the below contents:
1. check the status
2. stage it 
3. again check the status.

Observe the changes in the `git status` output before and after staging the file

```
# learning-git
Repository for learning git
This is an example repository for the Git tutoial

This repository is built step by step in the tutorial.
```

<details>
  <summary>Not sure how?</summary>

```
git status
git add README
git status
```
</details>
<br>

## Making changes to an already staged file
Let's change the `README` file. This file is already getting tracked and staged, you have checked that using `git status`.
Append a new line to the `README` with below command:

```
echo "Appending a new line to know what happens when we make changes to an already staged file." >> README
```

Check the `git status`:
```
On branch master
No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README
        new file:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README
```
Now `README` is listed as both `staged` and `unstaged`. How is that possible?

<details>
  <summary>🎤 Discuss?</summary><br>

It turns out that Git stages a file exactly as it is when you run the `git add` command. If you commit now, the version of `README` as it was when you last ran the `git add` command is how it will go into the commit, not the version of the file as it looks in your working directory when you run `git commit`. If you modify a file after you run `git add`, you have to run `git add` again to stage the latest version of the file.
</details>
<br>

## Short status
While `git status` output is pretty comprehensive. Git also has a short status flag to see the changes in a more compact way.

```
git status -s
```
Output:
```
AM  README
A  index.html
```

**Note:** Stort status flags
- `??` New files that aren't tracked 
- `A`  New files that have been added to the staging area
- `M`  Modified files
- `D`  Deleted files

## Viewing Your Staged and Unstaged Changes
The `git status` command just tells which files were changed but what you want to know is the "what you changed". `git diff` comes in handy to find the differences.

To see what you've changed but not yet staged, type git diff with no other arguments:

```
git diff
```
output:
```
diff --git a/README b/README
index 31335b8..d046718 100644
--- a/README
+++ b/README
@@ -3,3 +3,4 @@ Repository for learning git
 This is an example repository for the Git tutoial

 This repository is built step by step in the tutorial.
+Appending a new line to know what happens when we make changes to an already staged file.
```
> `git diff` command compares what is in your working directory with what is in your staging area. The result tells you the changes you've made that you haven't yet staged.

## Summary
> In this section, we had learned to create a new git repository, adding files to git, tracking new files and explored what happens when we make changes to already staged files. We also learned to see the status of the repository at any time using `git status`. Now it's time to make a commit to your files. This will be the topic of next section [Making a commit](commit.md).
