## Viewing the commit history

To look back into the commit history you can use the `git log` command. It's the most basic and powerful tool.

```
git log
```
`Output:`

```
commit 303c44a995b3ea084d3047b07fa114637a94fa09 (HEAD -> master)
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Fri Jan 28 16:26:53 2022 +0530

    books  renamed

commit 858cb90a147dce759807ad12fd76fbf62603a7fb
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Fri Jan 28 14:24:43 2022 +0530

    removed movies.md

commit 7844a83d1ae301f4ca4f6c7dc4782f7c0b24c778
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Fri Jan 28 13:03:49 2022 +0530

    adding one more movies and books

commit ae903fdf7af5ccb6a78069b6879e55bd95900e0e
Author: Ashish Juyal <ashish.juyal@gmail.com>
Date:   Fri Jan 28 13:02:32 2022 +0530

    adding my favourite movies and books

...............
...............
...............
```

> By default, with no arguments, `git log` lists the commits made in that repository in reverse chronological order; that is, the most recent commits show up first. As you can see, this command lists each commit with its SHA-1 checksum, the author’s name and email, the date written, and the commit message.

Git log has a huge number of options, lets take a look at some of the most popular:

- If you want to see some abbreviated stats for each commit.
    ```
    git log --stat
    ```

- To change the default log output you can use few prebuilt option values. The `oneline` value for this option prints each commit on a single line, which is useful if you’re looking at a lot of commits. In addition, the `short`, `full`, and `fuller` values show the output in roughly the same format but with less or more information, respectively.
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