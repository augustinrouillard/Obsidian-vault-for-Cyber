---
share: true
---
```markdown
# Note: Basic AWS CLI Commands

## 1. Configure AWS CLI

To set up your AWS CLI credentials and default settings:

```bash
aws configure
```

- You will be prompted for:
  - AWS Access Key ID
  - AWS Secret Access Key
  - Default region name
  - Default output format

## 2. List All S3 Buckets

To list all S3 buckets in your AWS account:

```bash
aws s3 ls
```

- This will display the names and creation dates of all your S3 buckets.

## Tips

- Make sure you have the AWS CLI installed (`sudo apt install awscli` or `pip install awscli`).
- Your credentials are stored in `~/.aws/credentials` and config in `~/.aws/config`.
- You can use other AWS CLI commands to interact with different AWS services.

---

**Summary:**  
- Use `aws configure` to set up your AWS CLI.
- Use `aws s3 ls` to list all S3 buckets in your account.