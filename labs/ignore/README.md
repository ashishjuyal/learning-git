## Ignoring files
Often, you will have a set of files that you don't want to commit and don't want Git to automatically add or even show you as being untracked. These are generally automatically generated files such as log files or artifacts produced by your build process. For such cases, git provides a mechanism to ignore such files. You can create a file listing patterns to match them named `.gitignore`.

> `.gitignore` also support wildcards and regular expressions. For example:

```shell
# ignore all files having .log extension
*.log

# ignore any files ending in ".o" or ".a"
*.[oa] 

*~ # ignore all files whose names end with a tilde (~)

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

📋 In this exercise you will ignore files from getting tracked:
- create a file called `.gitignore` in the root of your project folder and add `NOTES` inside it. 
- check the status
- commit the `.gitignore` file to the repository.

<details>
  <summary>Not sure how? </summary>

```shell
# adding NOTES to .gitignore
echo "NOTES" > .gitignore
# check git status
git status
# staging .gitignore
git add .gitignore
# commiting
git commit -m "adding .gitignore"
```
</details>
<br>

