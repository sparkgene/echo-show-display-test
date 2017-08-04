# Echo Show display test

This is a useful project to test the screen of Echo Show

This sample is not tested with Echo Show device.
(because i don't have it yet)

![sample image](https://github.com/sparkgene/echo-show-display-test/raw/master/BodyTemplate1.png)

## How to use

### Create s3 bucket

Put the bucket policy for public access.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadForGetBucketObjets",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::{your bucket name}/*"
        }
    ]
}
```

Copy all media files includes in `media` to the bucket.
Verify you can access the image from the browser.

### Create Lambda Function

1. Create lambda function in us-east-1(or eu-west-1) region.
2. Copy `src/lambda_function.py` into lambda source.

fill Environment variables

|key|value|
|---|-----|
|MEDIA_BUCKET|your public bucket|
|REGION|For us-east-1 set "s3". For other regions set "s3-{region>}. example: set `s3-eu-west-1` if you using EU (Ireland) region."|

### create alexa custom Skill

1. Chose "yes" at "Skill Information > Global Feilds > Render Template and Video App".
2. Copy `model/intentSchema.json` into "Interaction Model > Intent Schema".
3. Copy `modle/SampleUtterances.txt` into "Interaction Model > Sample Utterances".


### Test the Skill

Say `Alexa, ask <invocation name> body template number 1` to test.
Or you can test this from test console.
