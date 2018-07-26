## Cheatsheet: VIM
#### Delete all characters after a comma
``` :%s/,.*$//g ```

#### Delete all blank lines
``` :g/^$/d ```

#### Search case sensitive/insensitive
```/mysearchstring\c``` -> case insensitive

```/mysearchstring\C``` -> case sensitive

```:vimgrep /mysearchstring\c/ &``` -> case insensitive with vimgrep

#### Append a character to the end of each line
``` :%s/$/a/g ```
