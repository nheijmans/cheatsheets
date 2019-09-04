# Cheatsheet: SSH
#### Print fingerprint (md5) of keys
```ssh-keygen -l -E md5 -f yourkey.pub```

#### Print fingerprint (sha-1) of keys
```ssh-keygen -lf yourkey.pub```

#### Print fingerprint of key for verification in AWS keypairs
```openssl rsa -in path_to_private_key -pubout -outform DER | openssl md5 -c```

#### Open SSH tunnel on port 4444
```ssh -D 4444 -p 22 user@system```

