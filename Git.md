## master branch and 'origin/master' have diverged, how to 'undiverge' branches'?
```
$ git merge origin/master
```
```
... o ---- o ---- A ---- B  origin/master (upstream work)
                   \      \
                    C ---- M  master (your work)
```
<https://stackoverflow.com/questions/2452226/master-branch-and-origin-master-have-diverged-how-to-undiverge-branches >

## Trying to pull files from my Github repository: “refusing to merge unrelated histories”
```
$git merge origin/master --allow-unrelated-histories
```