# AWS CLI Important Commands — Detailed Guide

A practical reference for commonly used **AWS Command Line Interface (CLI)** commands.

This README explains the command syntax, what each command does, important options, and practical examples.

> **Scope:** AWS CLI contains many services and thousands of operations. This guide focuses on the most important commands commonly used for cloud administration, DevOps, development, and daily AWS work.

---

## Table of Contents

1. [What is AWS CLI?](#what-is-aws-cli)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Configure AWS CLI](#configure-aws-cli)
5. [General AWS CLI Syntax](#general-aws-cli-syntax)
6. [Identity, Account, and Region](#identity-account-and-region)
7. [EC2 Commands](#ec2-commands)
8. [S3 Commands](#s3-commands)
9. [IAM Commands](#iam-commands)
10. [VPC and Networking Commands](#vpc-and-networking-commands)
11. [EBS and AMI Commands](#ebs-and-ami-commands)
12. [CloudWatch and CloudWatch Logs](#cloudwatch-and-cloudwatch-logs)
13. [Lambda Commands](#lambda-commands)
14. [DynamoDB Commands](#dynamodb-commands)
15. [ECR Commands](#ecr-commands)
16. [STS Commands](#sts-commands)
17. [SSM Commands](#ssm-commands)
18. [Useful AWS CLI Options](#useful-aws-cli-options)
19. [Output Formats and Querying](#output-formats-and-querying)
20. [Profiles](#profiles)
21. [Troubleshooting](#troubleshooting)
22. [Security Best Practices](#security-best-practices)

---

# What is AWS CLI?

**AWS CLI (Command Line Interface)** is a tool that allows you to manage AWS services from a terminal or command prompt.

Instead of opening the AWS Management Console and clicking buttons, you can execute commands such as:

```bash
aws s3 ls
```

or:

```bash
aws ec2 describe-instances
```

The general structure is:

```bash
aws <service> <operation> [options]
```

Example:

```bash
aws ec2 describe-instances --region ap-south-1
```

Explanation:

- `aws`: Starts the AWS CLI.
- `ec2`: Selects the EC2 service.
- `describe-instances`: Requests information about EC2 instances.
- `--region ap-south-1`: Executes the command in the Mumbai region.

---

# Prerequisites

Before using AWS CLI, you generally need:

1. An AWS account.
2. AWS CLI installed.
3. Credentials configured, or an IAM role attached to an EC2 instance.
4. Permission to perform the requested operation.
5. A valid AWS region.

Check whether AWS CLI is installed:

```bash
aws --version
```

Example output:

```text
aws-cli/2.x.x Python/3.x.x Windows/10 exe/AMD64
```

---

# Installation

## Windows

### Option 1: MSI Installer

Download and install AWS CLI v2 using the official AWS installer.

Official documentation:

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

After installation, open PowerShell or Windows Terminal:

```powershell
aws --version
```

### Option 2: Verify PATH

If the command is not recognized, close and reopen the terminal. If it still fails, check whether the AWS CLI installation directory is present in the system PATH.

---

## Linux

For AWS CLI v2, use the official installation package recommended by AWS.

After installation:

```bash
aws --version
```

On many Linux systems, package-manager installation may also be available, but the official AWS installer is generally preferred for the latest AWS CLI v2.

---

## macOS

AWS CLI v2 can be installed using the official macOS installer.

Verify:

```bash
aws --version
```

---

# Configure AWS CLI

## 1. Configure credentials interactively

```bash
aws configure
```

The CLI asks for:

```text
AWS Access Key ID:
AWS Secret Access Key:
Default region name:
Default output format:
```

Example:

```text
AWS Access Key ID: AKIAxxxxxxxxxxxx
AWS Secret Access Key: xxxxxxxxxxxxxxxxx
Default region name: ap-south-1
Default output format: json
```

### Meaning of each value

| Value | Meaning |
|---|---|
| Access Key ID | Public identifier for an access-key credential |
| Secret Access Key | Secret credential used for authentication |
| Default region | Region used when `--region` is not provided |
| Output format | Format such as `json`, `text`, or `table` |

> Never share your secret access key. Do not commit credentials to GitHub.

---

## 2. Configure a named profile

```bash
aws configure --profile dev
```

Use it:

```bash
aws s3 ls --profile dev
```

A profile lets you keep separate configurations for different accounts, environments, or roles.

---

## 3. Configure a region

Set a region in a command:

```bash
aws ec2 describe-instances --region ap-south-1
```

Common region examples:

```text
ap-south-1       Mumbai
us-east-1        N. Virginia
us-west-2        Oregon
eu-west-1        Ireland
ap-southeast-1   Singapore
```

The resource must exist in the region you query. For example, an EC2 instance in Mumbai will not appear in an EC2 command executed against `us-east-1`.

---

## 4. Check current configuration

```bash
aws configure list
```

This shows where the CLI is obtaining configuration values.

For a specific profile:

```bash
aws configure list --profile dev
```

---

## 5. Get configuration values

```bash
aws configure get region
```

For a profile:

```bash
aws configure get region --profile dev
```

---

# General AWS CLI Syntax

The standard structure is:

```bash
aws <service> <operation> [options]
```

Example:

```bash
aws s3 cp myfile.txt s3://my-bucket/
```

Breakdown:

- `aws`: CLI executable.
- `s3`: AWS S3 service.
- `cp`: Copy operation.
- `myfile.txt`: Local source file.
- `s3://my-bucket/`: Destination bucket path.

Another example:

```bash
aws ec2 stop-instances --instance-ids i-0123456789abcdef0
```

- `ec2`: EC2 service.
- `stop-instances`: Stops one or more instances.
- `--instance-ids`: Option used to specify instance IDs.
- `i-0123456789abcdef0`: The target instance ID.

---

# Identity, Account, and Region

## 1. Check the currently authenticated identity

```bash
aws sts get-caller-identity
```

Example output:

```json
{
  "UserId": "AIDAXXXXXXXXX",
  "Account": "123456789012",
  "Arn": "arn:aws:iam::123456789012:user/example-user"
}
```

### Why use it?

This is one of the most important troubleshooting commands. It tells you:

- Which AWS account you are using.
- Which IAM user or role is active.
- Whether your credentials are working.

Using a profile:

```bash
aws sts get-caller-identity --profile dev
```

---

## 2. List available regions

```bash
aws ec2 describe-regions
```

Only show region names:

```bash
aws ec2 describe-regions --query "Regions[].RegionName" --output text
```

### Explanation

- `describe-regions`: Retrieves AWS regions available to the account.
- `--query`: Filters the response.
- `Regions[].RegionName`: Extracts only region names.
- `--output text`: Displays the result as plain text.

---

## 3. Get AWS account alias

```bash
aws iam list-account-aliases
```

This displays the account alias, if one is configured.

---

# EC2 Commands

EC2 (Elastic Compute Cloud) provides virtual servers in AWS.

Before running EC2 commands, make sure you are using the correct region.

```bash
export AWS_DEFAULT_REGION=ap-south-1
```

For Windows PowerShell:

```powershell
$env:AWS_DEFAULT_REGION="ap-south-1"
```

Alternatively, add `--region ap-south-1` to individual commands.

---

## 1. List all EC2 instances

```bash
aws ec2 describe-instances
```

### What it does

Returns detailed information about EC2 instances, including:

- Instance ID
- Instance state
- Instance type
- Private IP
- Public IP
- AMI ID
- Security groups
- Subnet
- VPC
- Tags

---

## 2. List only running instances

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=running
```

For Windows PowerShell, use one line or PowerShell backticks carefully:

```powershell
aws ec2 describe-instances --filters "Name=instance-state-name,Values=running"
```

### Explanation

- `--filters`: Limits the returned resources.
- `Name=instance-state-name`: The field being filtered.
- `Values=running`: Only instances in the running state.

Possible instance states:

```text
pending
running
shutting-down
terminated
stopping
stopped
```

---

## 3. List stopped instances

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=stopped
```

---

## 4. Get details of one instance

```bash
aws ec2 describe-instances \
  --instance-ids i-0123456789abcdef0
```

Replace the example ID with your actual instance ID.

---

## 5. Display instance IDs only

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].InstanceId" \
  --output text
```

### Explanation

- `Reservations[]`: Loops through reservations.
- `Instances[]`: Loops through instances.
- `InstanceId`: Extracts each instance ID.
- `--output text`: Prints a compact text result.

---

## 6. Display instance ID, state, type, and IP

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].{ID:InstanceId,State:State.Name,Type:InstanceType,PrivateIP:PrivateIpAddress,PublicIP:PublicIpAddress}" \
  --output table
```

This is useful for quickly checking instance information in a readable table.

---

## 7. Start an EC2 instance

```bash
aws ec2 start-instances \
  --instance-ids i-0123456789abcdef0
```

### What it does

Starts a stopped EC2 instance.

### Important points

- It does not create a new instance.
- The instance must be in a stoppable state.
- You need permission such as `ec2:StartInstances`.
- Starting an instance may incur compute charges.

---

## 8. Stop an EC2 instance

```bash
aws ec2 stop-instances \
  --instance-ids i-0123456789abcdef0
```

### What it does

Shuts down the operating system and stops the instance.

### Important points

- EBS-backed instances can generally be stopped.
- Instance-store-backed instances may not support stopping.
- Stopping does not necessarily delete attached EBS volumes.
- Public IPv4 addresses may change after stop/start unless using an Elastic IP.

---

## 9. Reboot an EC2 instance

```bash
aws ec2 reboot-instances \
  --instance-ids i-0123456789abcdef0
```

### Difference between reboot and stop

| Operation | Meaning |
|---|---|
| Reboot | Restarts the operating system |
| Stop | Powers off the instance |
| Terminate | Permanently deletes the instance |

---

## 10. Terminate an EC2 instance

```bash
aws ec2 terminate-instances \
  --instance-ids i-0123456789abcdef0
```

### Warning

Termination is destructive. The instance cannot normally be recovered after termination.

Before executing it, verify:

- Instance ID
- Region
- Environment
- Whether important data is backed up
- Whether termination protection is enabled

---

## 11. Enable termination protection

```bash
aws ec2 modify-instance-attribute \
  --instance-id i-0123456789abcdef0 \
  --disable-api-termination
```

This helps prevent accidental API termination.

---

## 12. Disable termination protection

```bash
aws ec2 modify-instance-attribute \
  --instance-id i-0123456789abcdef0 \
  --no-disable-api-termination
```

---

## 13. List available AMIs owned by you

```bash
aws ec2 describe-images \
  --owners self
```

### What it does

Lists AMIs owned by your AWS account.

---

## 14. List public Amazon Linux AMIs

AMI IDs differ by region and can change over time. Instead of hardcoding an old AMI ID, query AWS Systems Manager public parameters when available.

Example for an Amazon Linux 2023 AMI parameter:

```bash
aws ssm get-parameter \
  --name /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 \
  --query "Parameter.Value" \
  --output text
```

### Explanation

- `ssm get-parameter`: Reads a parameter from Systems Manager Parameter Store.
- `--name`: Specifies the parameter path.
- `--query "Parameter.Value"`: Extracts only the AMI ID.
- `--output text`: Prints only the value.

---

## 15. Launch an EC2 instance

```bash
aws ec2 run-instances \
  --image-id ami-xxxxxxxxxxxxxxxxx \
  --instance-type t3.micro \
  --key-name my-key \
  --security-group-ids sg-xxxxxxxxxxxxxxxxx \
  --subnet-id subnet-xxxxxxxxxxxxxxxxx \
  --count 1
```

### Explanation

| Option | Meaning |
|---|---|
| `--image-id` | AMI used as the operating system image |
| `--instance-type` | Hardware size, such as `t3.micro` |
| `--key-name` | EC2 key pair used for access |
| `--security-group-ids` | Firewall/security group attached to the instance |
| `--subnet-id` | Subnet where the instance is launched |
| `--count` | Number of instances to launch |

### Important

The AMI, subnet, security group, and key pair must be compatible and available in the selected region.

---

## 16. Add tags to an EC2 instance

```bash
aws ec2 create-tags \
  --resources i-0123456789abcdef0 \
  --tags Key=Name,Value=MyServer
```

Add multiple tags:

```bash
aws ec2 create-tags \
  --resources i-0123456789abcdef0 \
  --tags Key=Name,Value=MyServer Key=Environment,Value=Development
```

### Why tags matter

Tags help with:

- Resource identification
- Cost allocation
- Automation
- Environment management
- Searching and filtering

---

## 17. List EC2 instances by tag

```bash
aws ec2 describe-instances \
  --filters "Name=tag:Name,Values=MyServer"
```

---

## 18. Get console output from an instance

```bash
aws ec2 get-console-output \
  --instance-id i-0123456789abcdef0
```

This can help diagnose boot issues, especially when SSH or RDP access is unavailable.

---

## 19. List key pairs

```bash
aws ec2 describe-key-pairs
```

Only key pair names:

```bash
aws ec2 describe-key-pairs \
  --query "KeyPairs[].KeyName" \
  --output text
```

---

## 20. Create a key pair

```bash
aws ec2 create-key-pair \
  --key-name my-key \
  --query "KeyMaterial" \
  --output text > my-key.pem
```

### Explanation

- `--key-name`: Name of the key pair in AWS.
- `--query "KeyMaterial"`: Extracts the private key material.
- `> my-key.pem`: Saves the private key to a local file.

### Security warning

Protect the `.pem` file. Do not upload it to GitHub or share it.

On Linux/macOS:

```bash
chmod 400 my-key.pem
```

---

## 21. Delete a key pair

```bash
aws ec2 delete-key-pair \
  --key-name my-key
```

Deleting the key pair from AWS does not automatically delete an already-downloaded private key file.

---

## 22. List security groups

```bash
aws ec2 describe-security-groups
```

---

## 23. Create a security group

```bash
aws ec2 create-security-group \
  --group-name my-security-group \
  --description "Security group for my server" \
  --vpc-id vpc-xxxxxxxxxxxxxxxxx
```

The command returns a security group ID.

---

## 24. Add an inbound SSH rule

```bash
aws ec2 authorize-security-group-ingress \
  --group-id sg-xxxxxxxxxxxxxxxxx \
  --protocol tcp \
  --port 22 \
  --cidr YOUR_PUBLIC_IP/32
```

### Explanation

- `--group-id`: Target security group.
- `--protocol tcp`: Network protocol.
- `--port 22`: SSH port.
- `--cidr YOUR_PUBLIC_IP/32`: Allows only one IPv4 address.

### Security warning

Avoid this in production:

```bash
--cidr 0.0.0.0/0
```

That opens SSH to the entire internet. Prefer your own public IP or a controlled VPN/bastion host.

---

## 25. Add an inbound HTTP rule

```bash
aws ec2 authorize-security-group-ingress \
  --group-id sg-xxxxxxxxxxxxxxxxx \
  --protocol tcp \
  --port 80 \
  --cidr 0.0.0.0/0
```

HTTP is commonly public, but your application and architecture should determine whether it should be exposed.

---

## 26. Add an inbound HTTPS rule

```bash
aws ec2 authorize-security-group-ingress \
  --group-id sg-xxxxxxxxxxxxxxxxx \
  --protocol tcp \
  --port 443 \
  --cidr 0.0.0.0/0
```

---

## 27. Remove an inbound rule

```bash
aws ec2 revoke-security-group-ingress \
  --group-id sg-xxxxxxxxxxxxxxxxx \
  --protocol tcp \
  --port 22 \
  --cidr YOUR_PUBLIC_IP/32
```

---

## 28. Describe instance status checks

```bash
aws ec2 describe-instance-status \
  --instance-ids i-0123456789abcdef0
```

This returns system and instance status checks.

---

# S3 Commands

S3 (Simple Storage Service) is AWS object storage.

S3 commands are commonly used for:

- Creating buckets
- Uploading files
- Downloading files
- Synchronizing directories
- Listing objects
- Deleting objects
- Sharing objects temporarily

There are two commonly used command groups:

- `aws s3`: High-level, convenient file operations.
- `aws s3api`: Low-level API operations with more detailed control.

---

## 1. List all buckets

```bash
aws s3 ls
```

This lists buckets accessible to your current identity.

---

## 2. Create an S3 bucket

### Mumbai and most regions

```bash
aws s3api create-bucket \
  --bucket my-unique-bucket-name \
  --region ap-south-1 \
  --create-bucket-configuration LocationConstraint=ap-south-1
```

### Important note about us-east-1

For `us-east-1`, omit `--create-bucket-configuration`:

```bash
aws s3api create-bucket \
  --bucket my-unique-bucket-name \
  --region us-east-1
```

### Bucket naming rules

- Bucket names must be globally unique.
- Use lowercase letters, numbers, hyphens, and periods where allowed.
- Avoid sensitive information in bucket names.
- Choose a name that identifies the purpose without exposing secrets.

---

## 3. List objects in a bucket

```bash
aws s3 ls s3://my-unique-bucket-name
```

List recursively:

```bash
aws s3 ls s3://my-unique-bucket-name --recursive
```

Show human-readable sizes and totals:

```bash
aws s3 ls s3://my-unique-bucket-name --recursive --human-readable --summarize
```

---

## 4. Create a folder-like prefix

S3 does not use real folders in the same way as a traditional filesystem. A folder-like path is created by using an object key prefix.

Upload a file into a prefix:

```bash
aws s3 cp myfile.txt s3://my-unique-bucket-name/documents/
```

This creates an object key similar to:

```text
documents/myfile.txt
```

---

## 5. Upload one file

```bash
aws s3 cp myfile.txt s3://my-unique-bucket-name/
```

Upload to a specific path:

```bash
aws s3 cp myfile.txt s3://my-unique-bucket-name/uploads/myfile.txt
```

### Explanation

- `cp`: Copy operation.
- First path: Local source.
- Second path: S3 destination.

---

## 6. Upload an entire directory

```bash
aws s3 cp ./my-folder s3://my-unique-bucket-name/my-folder/ --recursive
```

### Explanation

- `./my-folder`: Local directory.
- `s3://.../my-folder/`: Destination prefix.
- `--recursive`: Includes files and subdirectories.

---

## 7. Download one file

```bash
aws s3 cp s3://my-unique-bucket-name/myfile.txt ./myfile.txt
```

---

## 8. Download an entire prefix

```bash
aws s3 cp s3://my-unique-bucket-name/uploads/ ./downloads/ --recursive
```

---

## 9. Copy an object inside S3

```bash
aws s3 cp \
  s3://source-bucket/file.txt \
  s3://destination-bucket/file.txt
```

This copies an object without first downloading it to your computer.

---

## 10. Move a file

Local to S3:

```bash
aws s3 mv myfile.txt s3://my-unique-bucket-name/
```

S3 to local:

```bash
aws s3 mv s3://my-unique-bucket-name/myfile.txt ./myfile.txt
```

S3 to S3:

```bash
aws s3 mv \
  s3://source-bucket/file.txt \
  s3://destination-bucket/file.txt
```

> A move is implemented as a copy followed by deletion. Use it carefully.

---

## 11. Sync a local directory to S3

```bash
aws s3 sync ./website s3://my-unique-bucket-name/website/
```

### What it does

Synchronizes files from the local directory to the S3 destination. It generally copies new or changed files.

---

## 12. Sync S3 to a local directory

```bash
aws s3 sync s3://my-unique-bucket-name/website/ ./website/
```

---

## 13. Sync one S3 bucket to another

```bash
aws s3 sync \
  s3://source-bucket/ \
  s3://destination-bucket/
```

---

## 14. Exclude files during sync

```bash
aws s3 sync ./website s3://my-unique-bucket-name/ \
  --exclude "*.log"
```

Exclude a directory:

```bash
aws s3 sync ./website s3://my-unique-bucket-name/ \
  --exclude "node_modules/*"
```

---

## 15. Include only selected files

```bash
aws s3 sync ./data s3://my-unique-bucket-name/ \
  --exclude "*" \
  --include "*.csv"
```

The order of include/exclude filters matters. AWS CLI evaluates the filters in order.

---

## 16. Delete one object

```bash
aws s3 rm s3://my-unique-bucket-name/myfile.txt
```

---

## 17. Delete all objects under a prefix

```bash
aws s3 rm s3://my-unique-bucket-name/uploads/ --recursive
```

---

## 18. Delete all objects in a bucket

```bash
aws s3 rm s3://my-unique-bucket-name/ --recursive
```

### Warning

This deletes objects, not necessarily the bucket itself. Verify the target bucket carefully.

---

## 19. Delete an empty bucket

```bash
aws s3 rb s3://my-unique-bucket-name
```

If the bucket contains objects:

```bash
aws s3 rb s3://my-unique-bucket-name --force
```

### Warning

`--force` deletes objects before removing the bucket. Use it only when you are certain.

---

## 20. Check whether a bucket exists or is accessible

```bash
aws s3api head-bucket \
  --bucket my-unique-bucket-name
```

A successful response generally means the bucket exists and is accessible, although error details can vary based on permissions and ownership.

---

## 21. Get bucket location

```bash
aws s3api get-bucket-location \
  --bucket my-unique-bucket-name
```

---

## 22. Get object metadata

```bash
aws s3api head-object \
  --bucket my-unique-bucket-name \
  --key myfile.txt
```

This can show:

- Content length
- Content type
- ETag
- Last modified time
- Metadata
- Storage class

---

## 23. Download an object using s3api

```bash
aws s3api get-object \
  --bucket my-unique-bucket-name \
  --key myfile.txt \
  ./myfile.txt
```

---

## 24. Upload an object using s3api

```bash
aws s3api put-object \
  --bucket my-unique-bucket-name \
  --key myfile.txt \
  --body ./myfile.txt
```

---

## 25. Generate a pre-signed URL

```bash
aws s3 presign \
  s3://my-unique-bucket-name/myfile.txt \
  --expires-in 3600
```

### Explanation

- `presign`: Creates a temporary signed URL.
- `--expires-in 3600`: URL remains valid for approximately 3600 seconds.

Anyone possessing the URL may be able to access the object during its validity period, depending on the signing and bucket configuration.

---

## 26. Check bucket versioning

```bash
aws s3api get-bucket-versioning \
  --bucket my-unique-bucket-name
```

Enable versioning:

```bash
aws s3api put-bucket-versioning \
  --bucket my-unique-bucket-name \
  --versioning-configuration Status=Enabled
```

Versioning helps protect against accidental overwrites and deletions, but it can increase storage costs.

---

## 27. Check bucket encryption

```bash
aws s3api get-bucket-encryption \
  --bucket my-unique-bucket-name
```

Not every bucket necessarily has an explicit bucket encryption configuration, and AWS S3 provides default encryption for new uploads. Your organization may require a specific encryption policy.

---

## 28. Set object storage class

```bash
aws s3 cp myfile.txt s3://my-unique-bucket-name/ \
  --storage-class STANDARD_IA
```

Common storage classes include:

```text
STANDARD
STANDARD_IA
ONEZONE_IA
INTELLIGENT_TIERING
GLACIER_IR
GLACIER
DEEP_ARCHIVE
```

Choose based on access frequency, retrieval time, and cost.

---

# IAM Commands

IAM (Identity and Access Management) controls authentication and authorization.

IAM resources include:

- Users
- Groups
- Roles
- Policies
- Access keys
- MFA devices

> Prefer IAM roles and temporary credentials over long-lived access keys whenever possible.

---

## 1. List IAM users

```bash
aws iam list-users
```

---

## 2. Create an IAM user

```bash
aws iam create-user \
  --user-name developer1
```

This creates an IAM identity. It does not automatically grant permissions.

---

## 3. Get IAM user details

```bash
aws iam get-user \
  --user-name developer1
```

---

## 4. Delete an IAM user

```bash
aws iam delete-user \
  --user-name developer1
```

Before deletion, check for attached policies, access keys, group membership, and other dependencies.

---

## 5. List IAM groups

```bash
aws iam list-groups
```

---

## 6. Create an IAM group

```bash
aws iam create-group \
  --group-name Developers
```

---

## 7. Add a user to a group

```bash
aws iam add-user-to-group \
  --user-name developer1 \
  --group-name Developers
```

---

## 8. List users in a group

```bash
aws iam get-group \
  --group-name Developers
```

---

## 9. Remove a user from a group

```bash
aws iam remove-user-from-group \
  --user-name developer1 \
  --group-name Developers
```

---

## 10. Delete an IAM group

```bash
aws iam delete-group \
  --group-name Developers
```

The group must generally be empty and have its attached policies removed first.

---

## 11. List IAM roles

```bash
aws iam list-roles
```

---

## 12. Get a role

```bash
aws iam get-role \
  --role-name MyEC2Role
```

---

## 13. Create an IAM role

```bash
aws iam create-role \
  --role-name MyEC2Role \
  --assume-role-policy-document file://trust-policy.json
```

Example `trust-policy.json` for EC2:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

### Explanation

The trust policy defines who is allowed to assume the role. It is different from a permissions policy.

---

## 14. Attach an AWS-managed policy to a role

```bash
aws iam attach-role-policy \
  --role-name MyEC2Role \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

### Warning

Use the least-privilege policy required. Avoid broad administrator policies for everyday workloads.

---

## 15. List policies attached to a role

```bash
aws iam list-attached-role-policies \
  --role-name MyEC2Role
```

---

## 16. List inline policies for a role

```bash
aws iam list-role-policies \
  --role-name MyEC2Role
```

---

## 17. Detach a policy from a role

```bash
aws iam detach-role-policy \
  --role-name MyEC2Role \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

## 18. Delete an IAM role

```bash
aws iam delete-role \
  --role-name MyEC2Role
```

Detach policies and remove dependencies before deleting.

---

## 19. Create an instance profile

```bash
aws iam create-instance-profile \
  --instance-profile-name MyEC2InstanceProfile
```

An instance profile is a container for an IAM role that can be attached to an EC2 instance.

---

## 20. Add a role to an instance profile

```bash
aws iam add-role-to-instance-profile \
  --instance-profile-name MyEC2InstanceProfile \
  --role-name MyEC2Role
```

---

## 21. Attach an instance profile to EC2

```bash
aws ec2 associate-iam-instance-profile \
  --instance-id i-0123456789abcdef0 \
  --iam-instance-profile Name=MyEC2InstanceProfile
```

This allows applications running on the EC2 instance to obtain temporary credentials through the instance role.

---

## 22. Create an access key

```bash
aws iam create-access-key \
  --user-name developer1
```

### Warning

The secret access key is shown only at creation time. Store it securely.

Do not create long-lived access keys unless there is a justified need. Prefer IAM Identity Center, role-based access, or workload roles.

---

## 23. List access keys

```bash
aws iam list-access-keys \
  --user-name developer1
```

---

## 24. Delete an access key

```bash
aws iam delete-access-key \
  --user-name developer1 \
  --access-key-id AKIAxxxxxxxxxxxx
```

---

## 25. List attached user policies

```bash
aws iam list-attached-user-policies \
  --user-name developer1
```

---

## 26. Simulate policy permissions

```bash
aws iam simulate-principal-policy \
  --policy-source-arn arn:aws:iam::123456789012:user/developer1 \
  --action-names s3:ListBucket s3:GetObject
```

This helps test whether a principal is allowed or denied specific actions.

---

# VPC and Networking Commands

VPC (Virtual Private Cloud) provides isolated networking for AWS resources.

Important resources include:

- VPCs
- Subnets
- Route tables
- Internet gateways
- NAT gateways
- Security groups
- Network ACLs
- Elastic IPs

---

## 1. List VPCs

```bash
aws ec2 describe-vpcs
```

---

## 2. Create a VPC

```bash
aws ec2 create-vpc \
  --cidr-block 10.0.0.0/16
```

Example CIDR:

```text
10.0.0.0/16
```

This provides a private IPv4 address range for the VPC.

---

## 3. Add a Name tag to a VPC

```bash
aws ec2 create-tags \
  --resources vpc-xxxxxxxxxxxxxxxxx \
  --tags Key=Name,Value=MyVPC
```

---

## 4. List subnets

```bash
aws ec2 describe-subnets
```

---

## 5. Create a subnet

```bash
aws ec2 create-subnet \
  --vpc-id vpc-xxxxxxxxxxxxxxxxx \
  --cidr-block 10.0.1.0/24 \
  --availability-zone ap-south-1a
```

### Explanation

- `--vpc-id`: VPC that owns the subnet.
- `--cidr-block`: IP range for the subnet.
- `--availability-zone`: Availability Zone where the subnet is created.

---

## 6. List route tables

```bash
aws ec2 describe-route-tables
```

---

## 7. Create a route table

```bash
aws ec2 create-route-table \
  --vpc-id vpc-xxxxxxxxxxxxxxxxx
```

---

## 8. Associate a route table with a subnet

```bash
aws ec2 associate-route-table \
  --route-table-id rtb-xxxxxxxxxxxxxxxxx \
  --subnet-id subnet-xxxxxxxxxxxxxxxxx
```

---

## 9. Create an internet gateway

```bash
aws ec2 create-internet-gateway
```

---

## 10. Attach an internet gateway to a VPC

```bash
aws ec2 attach-internet-gateway \
  --internet-gateway-id igw-xxxxxxxxxxxxxxxxx \
  --vpc-id vpc-xxxxxxxxxxxxxxxxx
```

---

## 11. Create a default route to the internet

```bash
aws ec2 create-route \
  --route-table-id rtb-xxxxxxxxxxxxxxxxx \
  --destination-cidr-block 0.0.0.0/0 \
  --gateway-id igw-xxxxxxxxxxxxxxxxx
```

### Explanation

This adds a default route for IPv4 internet traffic through the internet gateway.

A subnet also needs suitable public IP behavior and other configuration to provide public internet access to instances.

---

## 12. Enable public IPv4 assignment on a subnet

```bash
aws ec2 modify-subnet-attribute \
  --subnet-id subnet-xxxxxxxxxxxxxxxxx \
  --map-public-ip-on-launch
```

This causes instances launched into the subnet to receive public IPv4 addresses by default, subject to launch configuration and account settings.

---

## 13. List network interfaces

```bash
aws ec2 describe-network-interfaces
```

---

## 14. Allocate an Elastic IP

For a VPC:

```bash
aws ec2 allocate-address \
  --domain vpc
```

---

## 15. Associate an Elastic IP with an instance

```bash
aws ec2 associate-address \
  --instance-id i-0123456789abcdef0 \
  --allocation-id eipalloc-xxxxxxxxxxxxxxxxx
```

---

## 16. Release an Elastic IP

```bash
aws ec2 release-address \
  --allocation-id eipalloc-xxxxxxxxxxxxxxxxx
```

Release only addresses that are no longer needed. Public IPv4 addresses may incur charges depending on AWS pricing and usage conditions.

---

## 17. List NAT gateways

```bash
aws ec2 describe-nat-gateways
```

---

## 18. List network ACLs

```bash
aws ec2 describe-network-acls
```

---

# EBS and AMI Commands

EBS (Elastic Block Store) provides persistent block storage for EC2.

AMI (Amazon Machine Image) is a template used to launch EC2 instances.

---

## 1. List EBS volumes

```bash
aws ec2 describe-volumes
```

---

## 2. List volumes attached to an instance

```bash
aws ec2 describe-volumes \
  --filters Name=attachment.instance-id,Values=i-0123456789abcdef0
```

---

## 3. Create an EBS volume

```bash
aws ec2 create-volume \
  --availability-zone ap-south-1a \
  --size 20 \
  --volume-type gp3
```

### Explanation

- `--availability-zone`: Volume and instance must generally be in the same Availability Zone for direct attachment.
- `--size 20`: Size in GiB.
- `--volume-type gp3`: General-purpose SSD volume type.

---

## 4. Attach an EBS volume

```bash
aws ec2 attach-volume \
  --volume-id vol-xxxxxxxxxxxxxxxxx \
  --instance-id i-0123456789abcdef0 \
  --device /dev/sdf
```

The device name seen inside Linux may differ depending on the virtualization type and operating system.

---

## 5. Detach an EBS volume

```bash
aws ec2 detach-volume \
  --volume-id vol-xxxxxxxxxxxxxxxxx
```

Forcing detachment can cause data loss or filesystem corruption. Prefer graceful unmounting and normal detachment.

---

## 6. Create a snapshot

```bash
aws ec2 create-snapshot \
  --volume-id vol-xxxxxxxxxxxxxxxxx \
  --description "Backup before maintenance"
```

---

## 7. List snapshots owned by your account

```bash
aws ec2 describe-snapshots \
  --owner-ids self
```

---

## 8. Copy a snapshot

```bash
aws ec2 copy-snapshot \
  --source-region ap-south-1 \
  --source-snapshot-id snap-xxxxxxxxxxxxxxxxx \
  --description "Copied backup"
```

For cross-region copies, specify the destination region with `--region`.

---

## 9. Delete a snapshot

```bash
aws ec2 delete-snapshot \
  --snapshot-id snap-xxxxxxxxxxxxxxxxx
```

Verify that the snapshot is not needed before deletion.

---

## 10. Create an AMI from an instance

```bash
aws ec2 create-image \
  --instance-id i-0123456789abcdef0 \
  --name "my-server-ami" \
  --description "AMI backup of my server"
```

This creates an AMI from the instance and its associated EBS-backed volumes according to the operation's behavior.

---

## 11. Deregister an AMI

```bash
aws ec2 deregister-image \
  --image-id ami-xxxxxxxxxxxxxxxxx
```

Deregistering an AMI does not automatically delete all associated snapshots. Review and clean up unused snapshots separately.

---

# CloudWatch and CloudWatch Logs

CloudWatch monitors AWS resources and applications.

CloudWatch Logs stores and retrieves application and system logs.

---

## 1. List CloudWatch alarms

```bash
aws cloudwatch describe-alarms
```

---

## 2. List alarm names only

```bash
aws cloudwatch describe-alarms \
  --query "MetricAlarms[].AlarmName" \
  --output text
```

---

## 3. Get metric statistics

Example: CPU utilization for an EC2 instance.

```bash
aws cloudwatch get-metric-statistics \
  --namespace AWS/EC2 \
  --metric-name CPUUtilization \
  --dimensions Name=InstanceId,Value=i-0123456789abcdef0 \
  --statistics Average \
  --period 300 \
  --start-time 2026-09-14T00:00:00Z \
  --end-time 2026-09-14T01:00:00Z
```

### Explanation

| Option | Meaning |
|---|---|
| `--namespace` | CloudWatch metric namespace |
| `--metric-name` | Name of the metric |
| `--dimensions` | Identifies the resource |
| `--statistics` | Statistic such as Average, Sum, Minimum, Maximum |
| `--period` | Metric aggregation period in seconds |
| `--start-time` | Beginning of the time range in UTC |
| `--end-time` | End of the time range in UTC |

---

## 4. List log groups

```bash
aws logs describe-log-groups
```

---

## 5. List log streams in a log group

```bash
aws logs describe-log-streams \
  --log-group-name /aws/lambda/my-function
```

---

## 6. Get log events

```bash
aws logs get-log-events \
  --log-group-name /my/application \
  --log-stream-name my-stream
```

The log stream must exist, and its name must be exact.

---

## 7. Filter log events

```bash
aws logs filter-log-events \
  --log-group-name /my/application \
  --filter-pattern "ERROR"
```

This searches matching log events in a log group.

---

## 8. Tail logs from a log group

```bash
aws logs tail /my/application --follow
```

### Explanation

- `tail`: Displays recent log events.
- `--follow`: Continues polling for new events.

This is useful during application debugging.

---

## 9. Create a log group

```bash
aws logs create-log-group \
  --log-group-name /my/application
```

---

## 10. Delete a log group

```bash
aws logs delete-log-group \
  --log-group-name /my/application
```

This deletes the log group and its stored log data. Use carefully.

---

# Lambda Commands

AWS Lambda runs code without managing servers directly.

---

## 1. List Lambda functions

```bash
aws lambda list-functions
```

---

## 2. Get function details

```bash
aws lambda get-function \
  --function-name my-function
```

---

## 3. Create a deployment package

For a simple Python Lambda:

```bash
zip function.zip lambda_function.py
```

On Windows PowerShell, use a ZIP utility or PowerShell's `Compress-Archive`:

```powershell
Compress-Archive -Path lambda_function.py -DestinationPath function.zip
```

---

## 4. Create a Lambda function

```bash
aws lambda create-function \
  --function-name my-function \
  --runtime python3.12 \
  --role arn:aws:iam::123456789012:role/MyLambdaRole \
  --handler lambda_function.lambda_handler \
  --zip-file fileb://function.zip
```

### Explanation

| Option | Meaning |
|---|---|
| `--function-name` | Name of the Lambda function |
| `--runtime` | Language runtime |
| `--role` | IAM execution role ARN |
| `--handler` | File and function entry point |
| `--zip-file` | Deployment package |

The runtime must be supported in the selected region and account.

---

## 5. Invoke a Lambda function

```bash
aws lambda invoke \
  --function-name my-function \
  response.json
```

The function response is saved to `response.json`.

---

## 6. Invoke a function with a JSON payload

```bash
aws lambda invoke \
  --function-name my-function \
  --payload '{"name":"Pratik"}' \
  response.json
```

Depending on AWS CLI version and invocation settings, binary format handling may require:

```bash
--cli-binary-format raw-in-base64-out
```

Example:

```bash
aws lambda invoke \
  --function-name my-function \
  --cli-binary-format raw-in-base64-out \
  --payload '{"name":"Pratik"}' \
  response.json
```

---

## 7. Update Lambda code

```bash
aws lambda update-function-code \
  --function-name my-function \
  --zip-file fileb://function.zip
```

---

## 8. Update Lambda configuration

```bash
aws lambda update-function-configuration \
  --function-name my-function \
  --timeout 30 \
  --memory-size 512
```

### Explanation

- `--timeout 30`: Maximum execution time in seconds.
- `--memory-size 512`: Memory allocation in MB.

---

## 9. Publish a Lambda version

```bash
aws lambda publish-version \
  --function-name my-function
```

---

## 10. Delete a Lambda function

```bash
aws lambda delete-function \
  --function-name my-function
```

---

# DynamoDB Commands

DynamoDB is a managed NoSQL database.

---

## 1. List tables

```bash
aws dynamodb list-tables
```

---

## 2. Describe a table

```bash
aws dynamodb describe-table \
  --table-name Users
```

---

## 3. Create a table

```bash
aws dynamodb create-table \
  --table-name Users \
  --attribute-definitions AttributeName=UserId,AttributeType=S \
  --key-schema AttributeName=UserId,KeyType=HASH \
  --billing-mode PAY_PER_REQUEST
```

### Explanation

| Option | Meaning |
|---|---|
| `--table-name` | Table name |
| `--attribute-definitions` | Key attributes and their types |
| `S` | String |
| `N` | Number |
| `B` | Binary |
| `--key-schema` | Partition key and optional sort key |
| `HASH` | Partition key |
| `RANGE` | Sort key |
| `--billing-mode PAY_PER_REQUEST` | On-demand billing |

---

## 4. Put an item

```bash
aws dynamodb put-item \
  --table-name Users \
  --item '{"UserId":{"S":"u001"},"Name":{"S":"Pratik"},"Age":{"N":"22"}}'
```

DynamoDB uses typed attribute values such as:

```json
{
  "S": "text",
  "N": "123",
  "BOOL": true
}
```

---

## 5. Get an item

```bash
aws dynamodb get-item \
  --table-name Users \
  --key '{"UserId":{"S":"u001"}}'
```

---

## 6. Update an item

```bash
aws dynamodb update-item \
  --table-name Users \
  --key '{"UserId":{"S":"u001"}}' \
  --update-expression "SET #n = :name" \
  --expression-attribute-names '{"#n":"Name"}' \
  --expression-attribute-values '{":name":{"S":"New Name"}}'
```

---

## 7. Delete an item

```bash
aws dynamodb delete-item \
  --table-name Users \
  --key '{"UserId":{"S":"u001"}}'
```

---

## 8. Scan a table

```bash
aws dynamodb scan \
  --table-name Users
```

A scan reads items across the table and can be expensive for large tables.

---

## 9. Query a table

```bash
aws dynamodb query \
  --table-name Users \
  --key-condition-expression "UserId = :id" \
  --expression-attribute-values '{":id":{"S":"u001"}}'
```

A query is generally more efficient than a scan when using the table's key structure.

---

## 10. Delete a table

```bash
aws dynamodb delete-table \
  --table-name Users
```

---

# ECR Commands

Amazon ECR (Elastic Container Registry) stores container images.

---

## 1. List repositories

```bash
aws ecr describe-repositories
```

---

## 2. Create a repository

```bash
aws ecr create-repository \
  --repository-name my-app
```

---

## 3. Get an ECR login password

```bash
aws ecr get-login-password --region ap-south-1
```

This outputs a temporary authentication password. It is normally piped into Docker.

---

## 4. Authenticate Docker to ECR

```bash
aws ecr get-login-password --region ap-south-1 | \
docker login \
  --username AWS \
  --password-stdin 123456789012.dkr.ecr.ap-south-1.amazonaws.com
```

### Explanation

- `get-login-password`: Gets a temporary registry password.
- `docker login`: Authenticates Docker.
- `--password-stdin`: Avoids putting the password directly in the command arguments.

---

## 5. List images in a repository

```bash
aws ecr list-images \
  --repository-name my-app
```

---

## 6. Describe images

```bash
aws ecr describe-images \
  --repository-name my-app
```

---

## 7. Tag a local Docker image

```bash
docker tag my-app:latest \
  123456789012.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```

---

## 8. Push a Docker image

```bash
docker push \
  123456789012.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```

---

## 9. Delete an image

```bash
aws ecr batch-delete-image \
  --repository-name my-app \
  --image-ids imageTag=latest
```

---

## 10. Delete a repository

```bash
aws ecr delete-repository \
  --repository-name my-app
```

Delete repository and all images:

```bash
aws ecr delete-repository \
  --repository-name my-app \
  --force
```

---

# STS Commands

STS (Security Token Service) provides temporary security credentials and identity information.

---

## 1. Check current identity

```bash
aws sts get-caller-identity
```

This is the most useful STS command for checking which user or role is active.

---

## 2. Assume a role

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123456789012:role/CrossAccountRole \
  --role-session-name MySession
```

The response contains temporary credentials:

- Access key ID
- Secret access key
- Session token
- Expiration time

These credentials should be handled securely and are typically exported into environment variables or used by an AWS SDK/profile workflow.

---

## 3. Decode an authorization message

```bash
aws sts decode-authorization-message \
  --encoded-message "ENCODED_MESSAGE"
```

This is useful when AWS returns an encoded authorization failure message and your identity has permission to decode it.

---

# SSM Commands

AWS Systems Manager (SSM) helps manage instances, parameters, patches, and remote sessions.

---

## 1. List managed instances

```bash
aws ssm describe-instance-information
```

This lists instances registered with Systems Manager and reporting information.

---

## 2. Send a command to an EC2 instance

```bash
aws ssm send-command \
  --instance-ids i-0123456789abcdef0 \
  --document-name "AWS-RunShellScript" \
  --parameters commands="sudo systemctl status nginx"
```

### Explanation

- `--instance-ids`: Target managed instance.
- `--document-name`: SSM document to execute.
- `--parameters`: Parameters passed to the document.
- `AWS-RunShellScript`: Runs shell commands on Linux.

For Windows, use:

```bash
aws ssm send-command \
  --instance-ids i-0123456789abcdef0 \
  --document-name "AWS-RunPowerShellScript" \
  --parameters commands="Get-Service"
```

---

## 3. Get command invocation details

```bash
aws ssm get-command-invocation \
  --command-id COMMAND_ID \
  --instance-id i-0123456789abcdef0
```

---

## 4. Get a parameter

```bash
aws ssm get-parameter \
  --name /my-app/database-url
```

For an encrypted SecureString:

```bash
aws ssm get-parameter \
  --name /my-app/secret \
  --with-decryption
```

---

## 5. Put a parameter

```bash
aws ssm put-parameter \
  --name /my-app/config \
  --type String \
  --value "production" \
  --overwrite
```

For a secret:

```bash
aws ssm put-parameter \
  --name /my-app/secret \
  --type SecureString \
  --value "my-secret-value"
```

> Avoid putting secrets directly into shell history. For sensitive secrets, AWS Secrets Manager may be more appropriate.

---

## 6. Delete a parameter

```bash
aws ssm delete-parameter \
  --name /my-app/config
```

---

## 7. Start an SSM session

```bash
aws ssm start-session \
  --target i-0123456789abcdef0
```

This requires SSM Agent, IAM permissions, and network connectivity/configuration that supports Systems Manager.

---

# Useful AWS CLI Options

## 1. `--region`

Runs the command in a specific AWS region.

```bash
aws s3 ls --region ap-south-1
```

---

## 2. `--profile`

Uses a specific credentials profile.

```bash
aws sts get-caller-identity --profile dev
```

---

## 3. `--output`

Controls the response format.

```bash
aws ec2 describe-instances --output json
```

Available common formats:

```text
json
text
table
yaml
yaml-stream
```

Example:

```bash
aws ec2 describe-instances --output table
```

---

## 4. `--query`

Filters or reshapes the response using JMESPath.

Example:

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].InstanceId"
```

Example with multiple fields:

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].{ID:InstanceId,Type:InstanceType,State:State.Name}" \
  --output table
```

---

## 5. `--filters`

Filters AWS resources on supported operations.

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=running
```

---

## 6. `--dry-run`

Some EC2 operations support `--dry-run`.

```bash
aws ec2 run-instances \
  --image-id ami-xxxxxxxxxxxxxxxxx \
  --instance-type t3.micro \
  --dry-run
```

This checks whether the request is authorized without actually performing the operation, where supported.

---

## 7. `--debug`

Shows detailed debugging information.

```bash
aws sts get-caller-identity --debug
```

Use this for troubleshooting, but avoid sharing debug output publicly because it may contain sensitive information.

---

## 8. `--no-paginate`

Prevents automatic pagination for supported operations.

```bash
aws ec2 describe-instances --no-paginate
```

Use carefully because you may receive only part of a large result.

---

## 9. `--page-size`

Controls the page size for paginated operations.

```bash
aws ec2 describe-instances --page-size 50
```

This can help with timeouts or large responses.

---

## 10. `--max-items`

Limits the total number of returned items.

```bash
aws ec2 describe-instances --max-items 10
```

---

## 11. `--starting-token`

Continues a paginated operation from a previously returned token.

```bash
aws ec2 describe-instances \
  --starting-token "TOKEN"
```

Use the token returned by the AWS CLI rather than inventing one.

---

## 12. `--cli-input-json`

Passes parameters using a JSON file.

Example:

```bash
aws ec2 run-instances \
  --cli-input-json file://run-instance.json
```

Example JSON:

```json
{
  "ImageId": "ami-xxxxxxxxxxxxxxxxx",
  "InstanceType": "t3.micro",
  "MinCount": 1,
  "MaxCount": 1
}
```

This is useful for repeatable automation.

---

## 13. `--generate-cli-skeleton`

Generates an input or output skeleton for supported commands.

```bash
aws ec2 run-instances --generate-cli-skeleton input
```

This helps discover the JSON structure expected by an operation.

---

# Output Formats and Querying

## JSON output

```bash
aws ec2 describe-instances --output json
```

Best for:

- Scripts
- APIs
- Automation
- Processing with `jq`

---

## Text output

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].InstanceId" \
  --output text
```

Best for:

- Shell scripts
- Simple values
- Piping to other commands

---

## Table output

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].{ID:InstanceId,State:State.Name}" \
  --output table
```

Best for:

- Human-readable terminal output
- Quick inspection

---

## YAML output

```bash
aws ec2 describe-instances --output yaml
```

---

## JMESPath examples

### Extract all instance IDs

```bash
--query "Reservations[].Instances[].InstanceId"
```

### Extract public IPs

```bash
--query "Reservations[].Instances[].PublicIpAddress"
```

### Filter running instances and extract IDs

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=running \
  --query "Reservations[].Instances[].InstanceId" \
  --output text
```

### Sort by instance type

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].{ID:InstanceId,Type:InstanceType} | sort_by(@, &Type)" \
  --output table
```

---

# Profiles

Profiles allow multiple AWS configurations on one machine.

## Create a profile

```bash
aws configure --profile production
```

## Use a profile

```bash
aws s3 ls --profile production
```

## List profiles

```bash
aws configure list-profiles
```

## Set profile temporarily in Linux/macOS

```bash
export AWS_PROFILE=production
```

## Set profile temporarily in Windows PowerShell

```powershell
$env:AWS_PROFILE="production"
```

## Remove the environment variable

Linux/macOS:

```bash
unset AWS_PROFILE
```

PowerShell:

```powershell
Remove-Item Env:AWS_PROFILE
```

---

# Troubleshooting

## 1. `aws: command not found`

### Possible causes

- AWS CLI is not installed.
- AWS CLI is not in PATH.
- Terminal was opened before installation.

### Fix

```bash
aws --version
```

Reinstall AWS CLI or update the PATH, then reopen the terminal.

---

## 2. `Unable to locate credentials`

### Meaning

The CLI cannot find valid credentials.

### Checks

```bash
aws configure list
```

```bash
aws sts get-caller-identity
```

Possible solutions:

- Run `aws configure`.
- Use the correct profile.
- Set `AWS_PROFILE`.
- Attach an IAM role to an EC2 instance.
- Use IAM Identity Center or another supported credential provider.

---

## 3. `AccessDenied`

### Meaning

Your identity is authenticated, but it does not have permission to perform the operation.

### Check identity

```bash
aws sts get-caller-identity
```

### Things to verify

- IAM identity
- Attached policies
- Resource policy
- Permission boundaries
- Service control policies
- Region
- Resource ownership
- Explicit deny statements

---

## 4. `InvalidInstanceID.NotFound`

### Common causes

- Wrong instance ID.
- Wrong AWS region.
- Instance was terminated.
- Wrong AWS account/profile.

### Verify

```bash
aws sts get-caller-identity
```

```bash
aws ec2 describe-instances \
  --instance-ids i-0123456789abcdef0 \
  --region ap-south-1
```

---

## 5. `BucketAlreadyExists`

### Meaning

S3 bucket names are globally unique. Someone else may already own the name.

### Fix

Choose a more unique bucket name.

Example:

```text
pratik-demo-assets-2026-unique
```

---

## 6. `BucketRegionError`

### Meaning

The bucket exists in another region.

### Fix

Find its location:

```bash
aws s3api get-bucket-location \
  --bucket my-unique-bucket-name
```

Then use the correct region.

---

## 7. `Permission denied` on an EC2 shell script

This is usually a Linux file-permission issue.

Check permissions:

```bash
ls -l script.sh
```

Make the script executable:

```bash
chmod +x script.sh
```

Run it:

```bash
./script.sh
```

If the script requires administrative privileges:

```bash
sudo ./script.sh
```

> `sudo` should be used only when necessary. It does not fix every permission issue.

---

## 8. SSH permission error for a key file

On Linux/macOS:

```bash
chmod 400 my-key.pem
```

Then connect:

```bash
ssh -i my-key.pem ec2-user@PUBLIC_IP
```

For Ubuntu AMIs, the username is commonly:

```text
ubuntu
```

For Amazon Linux, it is commonly:

```text
ec2-user
```

The correct username depends on the AMI.

---

# Security Best Practices

## 1. Never expose credentials

Do not share:

- Secret access keys
- Session tokens
- Private key files
- `.aws/credentials`
- `.env` files containing secrets

---

## 2. Prefer IAM roles

For EC2:

- Attach an IAM role to the instance.
- Let applications use temporary credentials.
- Avoid storing access keys on the server.

For Lambda, ECS, and other AWS services, use execution/task roles whenever possible.

---

## 3. Use least privilege

Grant only the actions and resources required.

Avoid giving every user:

```text
AdministratorAccess
```

unless there is a justified administrative requirement.

---

## 4. Restrict SSH access

Avoid opening port 22 to the entire internet:

```text
0.0.0.0/0
```

Prefer:

- Your public IP
- VPN
- AWS Systems Manager Session Manager
- A controlled bastion host

---

## 5. Confirm region and account before destructive commands

Before stopping, terminating, deleting, or modifying resources:

```bash
aws sts get-caller-identity
```

```bash
aws configure get region
```

For critical operations, explicitly provide the region:

```bash
aws ec2 terminate-instances \
  --instance-ids i-0123456789abcdef0 \
  --region ap-south-1
```

---

## 6. Use tags consistently

Recommended tags:

```text
Name
Environment
Project
Owner
CostCenter
ManagedBy
```

Example:

```bash
aws ec2 create-tags \
  --resources i-0123456789abcdef0 \
  --tags Key=Environment,Value=Development Key=Project,Value=Demo
```

---

## 7. Use version control carefully

You can store command scripts and JSON input files in Git, but never commit:

- Access keys
- Secret keys
- Passwords
- Tokens
- Private SSH keys
- Production secrets

---

# Quick Command Cheat Sheet

## AWS Identity

```bash
aws sts get-caller-identity
aws configure list
aws configure list-profiles
```

## EC2

```bash
aws ec2 describe-instances
aws ec2 start-instances --instance-ids INSTANCE_ID
aws ec2 stop-instances --instance-ids INSTANCE_ID
aws ec2 reboot-instances --instance-ids INSTANCE_ID
aws ec2 terminate-instances --instance-ids INSTANCE_ID
```

## S3

```bash
aws s3 ls
aws s3 mb s3://BUCKET_NAME
aws s3 cp FILE s3://BUCKET_NAME/
aws s3 cp s3://BUCKET_NAME/FILE .
aws s3 sync ./folder s3://BUCKET_NAME/folder/
aws s3 rm s3://BUCKET_NAME/FILE
aws s3 rb s3://BUCKET_NAME
```

## IAM

```bash
aws iam list-users
aws iam list-roles
aws iam get-role --role-name ROLE_NAME
aws iam list-attached-role-policies --role-name ROLE_NAME
```

## VPC

```bash
aws ec2 describe-vpcs
aws ec2 describe-subnets
aws ec2 describe-route-tables
aws ec2 describe-security-groups
```

## CloudWatch Logs

```bash
aws logs describe-log-groups
aws logs describe-log-streams --log-group-name LOG_GROUP
aws logs tail LOG_GROUP --follow
```

## Lambda

```bash
aws lambda list-functions
aws lambda get-function --function-name FUNCTION_NAME
aws lambda invoke --function-name FUNCTION_NAME response.json
```

## SSM

```bash
aws ssm describe-instance-information
aws ssm start-session --target INSTANCE_ID
aws ssm get-parameter --name PARAMETER_NAME
```

---

# Official Documentation

- AWS CLI User Guide: https://docs.aws.amazon.com/cli/latest/userguide/
- AWS CLI Command Reference: https://docs.aws.amazon.com/cli/latest/reference/
- AWS CLI Installation: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
- AWS CLI Configuration: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
- EC2 CLI Reference: https://docs.aws.amazon.com/cli/latest/reference/ec2/
- S3 CLI Reference: https://docs.aws.amazon.com/cli/latest/reference/s3/
- IAM CLI Reference: https://docs.aws.amazon.com/cli/latest/reference/iam/
- CloudWatch Logs CLI Reference: https://docs.aws.amazon.com/cli/latest/reference/logs/

---

# Final Notes

1. Replace placeholders such as `INSTANCE_ID`, `BUCKET_NAME`, `ROLE_NAME`, and `ACCOUNT_ID` with your actual values.
2. Always verify the AWS region before running a command.
3. Read the command's help page when you need advanced options:

```bash
aws <service> <operation> help
```

Example:

```bash
aws ec2 run-instances help
```

4. For service-level help:

```bash
aws s3 help
```

5. For general AWS CLI help:

```bash
aws help
```

This README is intended as a practical reference. Always check the current AWS CLI documentation for newly introduced options, supported runtimes, pricing, service limits, and behavior that may change over time.
