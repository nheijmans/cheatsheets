# Cheatsheet: aws SAM (serverless application model)
## How to ZIP your files for packaging and deploying
If you want to ZIP the packages yourself, you can do the following commands

### Zip a single Lambda function folder 
``` zip -j your_lambda_code.zip your_lambda_code/* ```

### Zip all Lambda functions in a folder  (code/ in example)
``` for i in $(find code/* -type d -d 0); do zip -jr "${i%/}.zip" "$i"; done ```

## Packaging and deploying
### Package the template and files to upload to s3 for deployment
```sam package --profile *yourprofile* --region *yourregion* --template-file template.yaml --s3-bucket *yourbucket* --output-template packaged.yaml```

### deploy with cloudformation
``` sam deploy --profile yourprofile --template-file packaged.yaml --region yourregion --capabilities CAPABILITY_IAM --stack-name name_of_your_stack```

## Build the application
With the -u command the functions will be build with a docker similar to the AWS 
```
sam build -u
```

Now we can also invoke the functions locally

## Local invoke
### Create event payload
```
sam local generate-event sqs receive-message > SqsEvent.json
```

### Invoke function
```
sam local invoke SubmitVerdictFunction -e SqsEvent.json
```

### Start local API 
```
sam local start-api
```

## SAM layers
#### Make a layer for SAM to deploy
The folder structure needs to look like this
```
.
└── yourlayer/
    └── python/
        └── script_to_import.py
```

In the SAM template: **Reference the FOLDER, not the zip**
Define the layer in your SAM template

```
 MyLayer:
    Type: AWS::Serverless::LayerVersion
    Properties:
        LayerName: layerExample
        Description: Layer to do cool stuff
        ContentUri: my_layer_folder/
        CompatibleRuntimes:
            - python3.6
            - python2.7
        LicenseInfo: MIT
        RetentionPolicy: retain
```
This can be referenced in a function with (YAML style) in your Function:
``` 
Layers:
    - !Ref layerExample
```

### If the layer needs to be packaged and uploaded seperately
Put it in a ZIP file, while in the layer/ folder with the python sub directory

```
zip -r myname_layer.zip ./python/
```

## Custom policies
### Add a custom policy to a Function, example with SSM
```
Policies:
  - Statement:
    - Sid: SSMDescribeParametersPolicy
      Effect: Allow
      Action:
      - ssm:DescribeParameters
      Resource: '*'
    - Sid: SSMGetParameterPolicy
      Effect: Allow
      Action:
      - ssm:GetParameters
      - ssm:GetParameter
      Resource: '*'
```
