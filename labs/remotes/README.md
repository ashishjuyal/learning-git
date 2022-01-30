## Working with Remotes
To be able to collaborate on any Git project, you need to know how to manage your remote repositories. Remote repositories are versions of your project that are hosted on the Internet or network somewhere. You can have several of them, each of which generally is either read-only or read/write for you. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.

### Remote repositories can be on your local machine.
It is entirely possible that you can be working with a "remote" repository that is, in fact, on the same host you are. The word "remote" does not necessarily imply that the repository is somewhere else on the network or Internet, only that it is elsewhere. Working with such a remote repository would still involve all the standard pushing, pulling and fetching operations as with any other remote.

## Showing your remotes
To see which remote servers you have configured, you can run the `git remote` command. It lists the shortnames of each remote handle you've specified. If you've cloned your repository, you should at least see `origin` - that is the default name Git gives to the server you cloned from.
We don't have any remotes configured at the moment. We were just working using the local repositories. Let's try printing the remotes for out `books` repository.

```
git remote -v
```

## Adding remote repositories
Before you add a remote repository you should have a remote server available. GitHub is one of the services that provides remote Git service. If you don't have a GitHub account, you need to [create one](https://github.com/signup) and then create a new repository. Follow the presentation for the steps:

![](/img/git-new-repo.png)

You will create a new repository names as `books` and we will `push` our local git repository to GitHub.

![](/img/git-quick-setup.png)

> Once you have created the repository, it will give you option to `...push an existing repository from the command line`. Follow the below steps to configure the remote for your local repository and pushing changes to GitHub.

```shell
# The remote URL will look like this:
git remote add origin git@github.com:<repo-owner-name>/books.git
```

```shell
# For me, the GitHub repo URL is as below, you will have a different URL. Copy that from the Quick setup page on GitHub:
git remote add origin git@github.com:ashishjuyal/books.git

# after adding the remote you can print the remote using
git remote -v
```

```shell
# below command will rename your branch name to main (incase if it was master)
git branch -M main

# pushing the changes and setting the upstream to origin main
git push -u origin main
```

If your SSH keys are not already configured with your GitHub account (we still have to do this step), the `git push` will result in an error: 

`Output:`
```
The authenticity of host 'github.com (13.234.176.102)' can't be established.
ECDSA key fingerprint is SHA256:y2FACasdINAlw82N8SOttrVc/RITBDXz3/FubKgUfMS.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,13.234.176.102' (ECDSA) to the list of known hosts.
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

## Generating a new SSH key
1. Open Terminal.

2. Paste the text below, substituting in your GitHub email address.

```
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

This creates a new SSH key, using the provided email as a label.
```
> Generating public/private algorithm key pair.
```

1. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.
```
> Enter a file in which to save the key (/home/you/.ssh/algorithm): [Press enter]
```
2. At the prompt, type a secure passphrase.
```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

> For more information, see [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)


## Adding a new SSH key to GitHub
Follow [Adding a new SSH key to gitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) and add the newly generated SSH key to your GitHub account.


Once the SSH key is set in your account, trying pushing again:
```
git push -u origin main
```
`Output:`
```
Warning: Permanently added the ECDSA host key for IP address '13.234.210.38' to the list of known hosts.
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 8 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (13/13), 1.21 KiB | 34.00 KiB/s, done.
Total 13 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To github.com:ashishjuyal/books.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

## Verify and Push your books branch
Go to your repository on GitHub:
Change the repository name in the example URL: [https://github.com/ashishjuyal/books](https://github.com/ashishjuyal/books)

GitHub has only your `main` branch. To make the `books` branch available on GitHub, you also need to push that.
Inside your local repository:
```
git switch books
git push
```
`Output:`
```
fatal: The current branch books has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin books
```
Git provides the help in the response, set the upstream:
```
git push --set-upstream origin books
```
`Output:`
```
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'books' on GitHub by visiting:
remote:      https://github.com/ashishjuyal/books/pull/new/books
remote:
To github.com:ashishjuyal/books.git
 * [new branch]      books -> books
branch 'books' set up to track 'origin/books'.
```
Books branch is now available on your GitHub repository.