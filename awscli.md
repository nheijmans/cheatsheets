## Cheatsheet: aws cli
#### Add pub key to profile & region
```aws --profile $profilename --region $regionname ec2 import-key-pair --key-name $keyname --public-key-material file://path/to/pub/key```

#### Change Route53 record sets via API. Useful for adding Alias records to the API Gateway
``` aws route53 change-resource-record-sets --hosted-zone-id $hostedzoneid --change-batch file://setup-dns-record.json ```

#### Additional reading
https://forums.aws.amazon.com/thread.jspa?threadID=269585&tstart=0
https://docs.aws.amazon.com/general/latest/gr/rande.html#apigateway_region
