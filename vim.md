## Cheatsheet: VIM
#### Delete all characters after a comma
``` :%s/,.*$//g ```

#### Delete all blank lines
``` :g/^$/d ```

#### Delete x number of last characters (3 in example)
``` :%s/.\{3}$// ```

#### Search case sensitive/insensitive
```/mysearchstring\c``` -> case insensitive

```/mysearchstring\C``` -> case sensitive

```:vimgrep /mysearchstring\c/ &``` -> case insensitive with vimgrep

#### Append a character to the end of each line
``` :%s/$/a/g ```

#### Autoformat a script
``` gg=G ```

