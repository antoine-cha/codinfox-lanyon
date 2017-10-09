---
layout: post
title: AWS S3 policy generator
author: antoine-cha
tags: [amazon]
---

## The tool
http://awspolicygen.s3.amazonaws.com/policygen.html

### What for ?

> The AWS Policy Generator is a tool that enables you to create policies that control access to Amazon Web Services (AWS) products and resources. "

Enables to specify fine-grained rules for all the actions to be performed on resources.

### How ?

1. Specify your rules
2. Click `Add statement`
3. Repeat 1 + 2 until satisfaction
4. Click `Generate policy`
5. Copy-paste the JSON to your bucket authorization strategy ( MY-BUCKET > Authorizations > Bucket Strategy )
6. Save, and voilà !

## Examples

Note that the Sid can be changed but needs to be unique. This can be useful to describe a policy

### Denying bucket deletion to everyone
```
{
  "Id": "Policy1507xxxxxxx",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt150xxxxxxx", 
      "Action": [
        "s3:DeleteBucket"
      ],
      "Effect": "Deny",
      "Resource": "arn:aws:s3:::MY-BUCKET/",
      "Principal": "*"
    }
  ]
}
```

### Static hosting without public listing

```
{
  "Id": "Policy1507xxxxx",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt150xxxxxxxx",
      "Action": [
        "s3:GetObject"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::MY-BUCKET/",
      "Principal": "*"
    }
  ]
}
```


