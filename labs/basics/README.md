## Git Basics

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
This will create a new subdirectory named .git that contains all your necessary repository files. This is the local Git database. In Linux and MacOS this folder will not be visible because it starts with a dot that means a hidden folder. To view use `ls -la` command on the terminal.

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
You can see the new `index.html` file is untracked. Untracked basically means that Git sees a file you didn’t have in the previous snapshot (commit), and which hasn’t yet been staged.

Files in your Git repository folder can be in one of 2 states:

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

# Short status
While `git status` output is pretty comprehensive. Git also has a short status flag to see the changes in a more compact way.

```
git status -s
```
Output:
```
A  README
A  index.html
```
New files that aren’t tracked have a `??` next to them, new files that have been added to the staging area have an `A`, modified files have an `M` and so on.


## First Commit

As you have seen in the last `git status`, README and index.html are staged for commit.

```
On branch master
No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README
        new file:   index.html
```

Let's make our first commit

```
git commit -m "making my first commit"
```
check the status:
```
git status
```
