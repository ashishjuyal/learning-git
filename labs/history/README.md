## Viewing the commit history

To look back into the commit history you can use the `git log` command. It's the most basic and powerful tool.

```
git log
```
`Output:`

```
commit df436213eb18d9bf4b3783077fcee4426f3fe57e (HEAD -> master)
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:58:20 2022 +0530

    renamed books.md to fav-books.md

commit 5e6178cc3eec9b2e577180eb3f54678e210e3289
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:58:00 2022 +0530

    removed movies.md

commit eb889893e7d4ca7e0282cd6ee7e6dccf1da2e196
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:56:42 2022 +0530

    adding .gitignore

commit 25755bfdffb2ca7d574a2e2e1ebcad253406d283
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:55:59 2022 +0530

    adding one more movies and books

commit 50b43aedfa8ec3680efbac28037c126e7250cc06
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:55:37 2022 +0530

    adding my favourite movies and books

commit 8a9f3488528f43690b11621300cf45df56823d66
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:54:16 2022 +0530

    skipping the staging area

commit 7941f658a5b009db260b74c194fb98e392f3e486
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Sat Jan 29 12:53:49 2022 +0530

    making my first commit
```

> By default, with no arguments, `git log` lists the commits made in that repository in reverse chronological order; that is, the most recent commits show up first. As you can see, this command lists each commit with its SHA-1 checksum, the author's name and email, the date written, and the commit message.

Git log has a huge number of options, lets take a look at some of the most popular:

- If you want to see some abbreviated stats for each commit.
    ```
    git log --stat
    ```

- To change the default log output you can use few prebuilt option values. The `oneline` value for this option prints each commit on a single line, which is useful if you're looking at a lot of commits. In addition, the `short`, `full`, and `fuller` values show the output in roughly the same format but with less or more information, respectively.
    ```
    git log --pretty=oneline
    ```

📋 Run the `git log` with `short`, `full`, and `fuller` and observe the differences.

- To specify your own log output format, you can use the `format` value.
```
git log --pretty=format:"%h - %an, %ar : %s"
```


|Specifier |	Description of Output
|:---------|:-----------------------------
|%H | Commit hash
|%h | Abbreviated commit hash
|%T |Tree hash
|%t |Abbreviated tree hash
|%P |Parent hashes
|%p |Abbreviated parent hashes
|%an| Author name
|%ae| Author email
|%ad| Author date (format respects the --date=option)
|%ar| Author date, relative
|%cn| Committer name
|%ce| Committer email
|%cd| Committer date
|%cr| Committer date, relative
|%s |Subject
------------------------------------