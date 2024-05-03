---
title: "AWS Dispatch"
permalink: /pages/tutorials/aws_data_dispatch/
layout: single
---

# Instructions for efficient data dispatch via AWS S3 bucket 
 
The most efficient way for us to dispatch your sequencing data to you would be for you to provide us with access to an S3 bucket in your AWS account. 
This may be familiar to you, or your IT team can help you in this regard. 
Here is a brief procedure (with our preferred bucket name and username)
 
Steps to set up an AWS shared bucket and keys pair for sequencing data dispatch to you:
 
## Step 0 

If you don't have an aws account, setup one at [aws.amazon.com](https://aws.amazon.com/)
 
## Step 1 

create a new S3 bucket named "scrippsresearchngscore-lab" 

You can follow [this](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html) procedure 

## Step 2 

create a user "scrippsresearchngscore" with a pair of keys for programmatic access 

You can follow [this](https://objectivefs.com/howto/how-to-get-amazon-s3-keys) procedure
 
## Step 3 

grant the new user full access to just the new bucket

You can follow [this](https://objectivefs.com/howto/how-to-restrict-s3-bucket-policy-to-only-one-aws-s3-bucket) procedure


## Step 4 

By default, ‘S3 Block Public Access feature’  blocked every public access. Please allow for access permissions so we could write into the AWS S3 bucket you have created for us. 

Please see this [link](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html) for more information


## Step 5 

Please let us know:

* the aws account id (12 digits)

* the new bucket name

* the region it is in

* the new user username

* the new user password

* the new access_key_id

* the new secret_access_key


Please email us at [ccbb](mailto:ccbb@scripps.edu) if you have any questions. We can arrange for a zoom meeting if necessary.

