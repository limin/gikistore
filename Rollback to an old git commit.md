```sh
git checkout [revision] .
```

where [revision] is the commit hash (for example: 12345678901234567890123456789012345678ab).

Don't forget the . at the end, very important. This will apply changes to the whole tree. Then commit and you should be good.

You can undo this by

```
git reset --hard; 
```

that will delete all modifications from the working directory and staging area.


[reference](https://stackoverflow.com/questions/2007662/rollback-to-an-old-git-commit-in-a-public-repo)