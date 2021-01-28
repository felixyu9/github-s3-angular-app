# GithubS3AngularApp

This project is for my YouTube video on how to automatically update file contents on an AWS S3 bucket using github and CodeBuild (https://www.youtube.com/watch?v=AMSdM2dj_eI). In the video, I use an angular app deployment (build the project and upload build files to S3) as an example. This approach can be used for other applications as well. 


Bucket Policy for Website Hosting on AWS S3 (replace "bucket-name" with your actual s3 bucket name):

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::bucket-name/*"
        }
    ]
}
```

IAM policy statement to add to the IAM role used by CodeBuild (replace "bucket-name" with your actual s3 bucket name):

```
{
    "Effect": "Allow",
    "Action": [
        "s3:PutObject",
        "s3:GetObjectAcl",
        "s3:GetObject",
        "s3:DeleteObjectVersion",
        "s3:GetObjectVersionAcl",
        "s3:ListBucket",
        "s3:DeleteObject",
        "s3:PutObjectAcl",
        "s3:GetObjectVersion",
        "s3:ListObject*"
    ],
    "Resource": [
        "arn:aws:s3:::bucket-name/*",
        "arn:aws:s3:::bucket-name"
    ]
}
```
