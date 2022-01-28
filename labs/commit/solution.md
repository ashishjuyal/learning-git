## Lab Solution

```shell
# adding movies and books to file
echo $'movie1\nmovie2\nmovie3\n' > movies.md
echo $'book1\nbook2\nbook3\n' > books.md

# printing short status
git status -s

# stage the file and commit the changes.
git add movies.md books.md
git commit -m "adding my favourite movies and books"

# edit the files again and add one more movie and book name to it.
echo "movie4" >> movies.md
echo "book4" >> books.md

# again print the repository short status.
git status -s

# make a commit skipping the staging area.
git commit -a -m "adding one more movies and books"

```
> Back to exercise [Exercise](README.md#lab).