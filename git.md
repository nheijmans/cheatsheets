## Cheatsheet: Git
#### List the source repository
```git remote show origin```

#### get the origin repository url
``` git config --get remote.origin.url ```

#### sync a fork
``` git fetch upstream ```

``` git merge upstream/master ```

#### one line readable git log
``` git log --pretty=format:"%h %s" --graph ```
