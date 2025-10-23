# Lab 01 — IAM: least-privilege, KMS, MFA & auditing


## Objective


Learn and practice IAM least-privilege policies, create an IAM role for an EC2 instance, provision a KMS key and use it to encrypt an S3 object, enable MFA for an IAM user, and set up basic security auditing (CloudTrail + AWS Config).


## Prerequisites


- An AWS account you can use for labs (sandbox preferred). Do not run on production accounts.
- AWS CLI v2 configured (`aws configure`) with an admin profile (we'll call it `lab-admin`).
- jq installed (optional but helpful).
- Time: ~45–90 minutes depending on familiarity.


## What you will create


- `IAM policy` demonstrating least-privilege for S3 read-only on a single bucket.
- `IAM role` with EC2 trust and the above policy attached.
- `KMS key` (customer-managed) and alias.
- `S3 bucket` (lab-bucket) with server-side encryption using the KMS key.
- `CloudTrail` trail that delivers logs to an S3 bucket.
- `AWS Config` recorder and delivery channel (optional but recommended).
- (Optional) enable MFA for an IAM user and test `aws sts get-session-token` with MFA.


## Safety notes


- Do **not** hardcode credentials in any file. This lab avoids embedding secrets.
- Make sure you clean up resources after testing to avoid costs (see Cleanup section).


## Steps (copy-paste)


> Replace `lab-admin` with your admin CLI profile (or omit `--profile` if default). Replace `your-unique-string` with a short unique suffix to avoid name collisions.


1. Set variables


```bash
export AWS_PROFILE=lab-admin
export PREFIX=farahejaz-security-lab
export REGION=us-east-1
export LAB_BUCKET="$PREFIX-logs-$(date +%s)"
export KMS_ALIAS="alias/$PREFIX-kms"
export ROLE_NAME="$PREFIX-ec2-role"
export POLICY_NAME="$PREFIX-s3-readonly-policy"
export USER_NAME="$PREFIX-test-user"
