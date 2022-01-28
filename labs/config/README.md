## Git configuration - Mac, Windows or Linux

Git comes with a tool called `git config` that lets you get and set configuration variables that control all aspects of how Git looks and operates. These variables can be stored in three different places:

- `/etc/gitconfig` file: Contains values applied to every user on the system and all their repositories. If you pass the option `--system` to `git config`, it reads and writes from this file specifically. Because this is a system configuration file, you would need administrative or superuser privilege to make changes to it.

- `~/.gitconfig` or `~/.config/git/config` file: Values specific personally to you, the user. You can make Git read and write to this file specifically by passing the `--global` option, and this affects all of the repositories you work with on your system.

- config file in the Git directory (that is, `.git/config`) of whatever repository you’re currently using: Specific to that single repository. You can force Git to read from and write to this file with the `--local` option, but that is in fact the `default`. Unsurprisingly, you need to be located somewhere in a Git repository for this option to work properly.

Each level overrides values in the previous level, so values in `.git/config` trump those in `/etc/gitconfig`.

📋 View all of your `git config` settings and where they are coming from.

<details>
  <summary>Not sure how?</summary>

```
# list all local images:
git config --list --show-origin
```
</details>

## Configure your Identity in git

Every Git commit uses this information, and it’s immutably baked into the commits you start creating. You need to do this only once if you pass the `--global` option, because then Git will always use that information for anything you do on that system

```
git config --global user.name <Your name> # This 
git config --global user.email <Your email>
```

## Configure your editor
You can configure the default text editor that will be used when Git needs you to type in a message. If not configured, Git uses your system’s default editor.

```
git config --global core.editor pico
```

You can find the instructions to set up your favorite editor with Git in [git config core.editor commands](https://git-scm.com/book/en/v2/ch00/ch_core_editor)

## Your default branch name
By default Git will create a branch called master when you create a new repository with `git init`. From Git version 2.28 onwards, you can set a different name for the initial branch.

> For more background on this change, this statement from the [Software Freedom Conservancy](https://sfconservancy.org/news/2020/jun/23/gitbranchname/) is an excellent place to look

To set main as the default branch name do:

```
git config --global init.defaultBranch main
```

## Checking your settings

After making changes check your configuration settings

```
git config --list
```

You can also check a specific key’s value by typing
```
git config user.name
```