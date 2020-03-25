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

#### Sync existing local repository with a remote repository
```
git init
git add .
git commit -m "initial commit"
git pull origin master --allow-unrelated-histories
git push -u origin master
```
