## Cheatsheet: aws cli
#### Add pub key to profile & region
```aws --profile $profilename --region $regionname ec2 import-key-pair --key-name $keyname --public-key-material file://path/to/pub/key```
