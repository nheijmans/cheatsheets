# Cheatsheet: aws SAM (serverless application model)
## How to ZIP your files for packaging and deploying

### Zip a single Lambda function folder 
``` zip -j your_lambda_code.zip your_lambda_code/* ```

### Zip all Lambda functions in a folder  (code/ in example)
``` for i in $(find code/* -type d -d 0); do zip -jr "${i%/}.zip" "$i"; done ```

## Packaging and deploying
### Package the template and files to upload to s3 for deployment
SAM package --profile *yourprofile* --region *yourregion* --template-file template.yaml --s3-bucket *yourbucket* --output-template packaged.yaml

### deploy with cloudformation
``` sam deploy --profile yourprofile --template-file packaged.yaml --region yourregion --capabilities CAPABILITY_IAM --stack-name name_of_your_stack```

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
``` Layers:
        - !Ref layerExample
```
