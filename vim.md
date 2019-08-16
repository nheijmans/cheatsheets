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

#### Format JSON file
``` :%!python -m json.tool ```

#### Select all text
``` ggVG ```

#### Make something lowercase or uppercase
``` select all and press: u or U ```

### How to use macros
Start recording a macro by pressing ```q``` followed by the keyboard key you want to link it to, e.g. ```a``` and stop recording your commands to be repeated with ```q``` again. 

Macro's are triggered with the syntax ```@a``` where a is of course the keyboard you assigned. 

```
Run macro 5 times
8@a
```

```
Execute the macro stored in register a on lines 5 through 10.
:5,10norm! @a
```

```
Execute the macro stored in register a on lines 5 through the end of the file.
:5,$norm! @a
```

```
Execute the macro stored in register a on all lines.
:%norm! @a
```

```
Execute the macro store in register a on all lines matching pattern.
:g/pattern/norm! @a
```

```
To execute the macro on visually selected lines, press V and the j or k until the desired region is selected. Then type :norm! @a and observe the that following input line is shown.
:'<,'>norm! @a
```
