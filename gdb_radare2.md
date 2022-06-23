# GDB
Set assembly flavor to intel for better readability
```
set disassembly-flavor intel
```

List all functions
```
info functions

```

Show disassembled code for a function
```
disass <function>
```

## Breakpoints
Set breakpoint on function or memory address
```
b <function>
b *<memaddress>
```

List breakpoints
```
info breaks
```

Delete breakpoint 2
```
delete 2
```

## Registers
Check registers
```
info registers
```

get string value from RDX register
```
x/s $rdx
```

## Dynamic analysis
Set a breakpoint on main func
```
break main
```

Show current position in the execution
```
disass
```

output:
```
Dump of assembler code for function main:
   0x0000000000400716 <+0>:	push   %rbp
   0x0000000000400717 <+1>:	mov    %rsp,%rbp
=> 0x000000000040071a <+4>:	sub    $0x10,%rsp
   0x000000000040071e <+8>:	mov    %edi,-0x4(%rbp)
   0x0000000000400721 <+11>:	mov    %rsi,-0x10(%rbp)
```


## references
**overview of x command (memory contents)**
https://visualgdb.com/gdbreference/commands/x

# Radare2
Load binary with debug mode and argument
```
radare2 -d binary args
```

aaa --> analysis of binary
iz  --> show strings
s <function> --> go to the function
pdf --> print function disassembly code
pdb --> print block of assembly code where the app stands
db 0x0000 --> add breakpoint on address
dc --> run application
dr --> show registers

Get value of register. The int is nr of bytes
```
px 32 @rax
```

Stepping in radare2
```
ds?
|Usage: ds Step commands
| ds               Step one instruction
| ds <num>         Step <num> instructions
| dsb              Step back one instruction
| dsf              Step until end of frame
| dsi <cond>       Continue until condition matches
| dsl              Step one source line
| dsl <num>        Step <num> source lines
| dso <num>        Step over <num> instructions
| dsp              Step into program (skip libs)
| dss <num>        Skip <num> step instructions
| dsu[?]<address>  Step until address
| dsui[r] <instr>  Step until an instruction that matches `instr`, use dsuir for regex match
| dsue <esil>      Step until esil expression matches
| dsuf <flag>      Step until pc == flag matching name
```
## References
https://scoding.de/uploads/r2_cs.pdf

# Other references
https://0x00sec.org/t/dissecting-and-exploiting-elf-files/7267 -> intro in ELF analysis
