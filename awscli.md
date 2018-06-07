## Cheatsheet: aws cli
#### Add pub key to profile & region
```aws --profile $profilename --region $regionname ec2 import-key-pair --key-name $keyname --public-key-material file://path/to/pub/key```

### EC2
#### List security groups per instance ID
```aws --output text ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,NetworkInterfaces[*].Groups[*]]' ```

#### Show the console output from a specific instance
```aws ec2 get-console-output --instance-id $instanceid```

### Route53
#### Change Route53 record sets for API gateway
``` aws route53 change-resource-record-sets --hosted-zone-id $yourdomainhostedzoneid --change-batch file://setup-dns-record.json ```

example dns record
```
{
  "Comment": "alias api gateway to custom domain",
  "Changes": [
    {
      "Action": "UPSERT",
      "ResourceRecordSet": {
        "Name": "api.example.com",
        "Type": "A",
        "AliasTarget": {
          "HostedZoneId": "$apigatewayhostedzoneid",
          "DNSName": "yourapigateway.execute-api.us-west-1.amazonaws.com",
          "EvaluateTargetHealth": false
        }
      }
    }
  ]
}

```

#### Additional reading
https://forums.aws.amazon.com/thread.jspa?threadID=269585&tstart=0
https://docs.aws.amazon.com/general/latest/gr/rande.html#apigateway_region
https://blyx.com/2016/03/11/forensics-in-aws-an-introduction/
