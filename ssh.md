# Cheatsheet: SSH
#### Print fingerprint (md5) of keys
```ssh-keygen -l -E md5 -f yourkey.pub```

#### Print fingerprint (sha-1) of keys
```ssh-keygen -lf yourkey.pub```

#### Open SSH tunnel on port 4444
```ssh -D 4444 -p 22 user@system```

