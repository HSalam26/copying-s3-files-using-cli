# Copying Files from One Amazon S3 Bucket to Another Using CLI

Copying files from one Amazon S3 bucket to another is a common task when working with AWS. This guide will walk you through the process using the AWS Command Line Interface (CLI). Before you begin, make sure you have the following prerequisites in place:

1. **Install AWS CLI**: If you haven't already, you need to install and configure the AWS CLI on your local machine. You can download and install it from [https://aws.amazon.com/cli/](https://aws.amazon.com/cli/).

2. **Create AWS S3 Buckets**: Ensure that you have two S3 buckets created in your AWS account. You should have at least one file in the source bucket that you want to copy.

Now, follow these steps to copy files from the source bucket to the destination bucket:

1. **Set Up AWS CLI**: Make sure you have the AWS CLI configured with your credentials. You can use `aws configure` to set up your Access Key ID, Secret Access Key, default region, and output format.

2. **Copy Files**: Use the `aws s3 cp` command to copy files between buckets. Here's the basic syntax:

   ```bash
   aws s3 cp s3://source-bucket-name/source-prefix s3://destination-bucket-name/destination-prefix --recursive
   ```

   - `source-bucket-name`: The name of the source S3 bucket.
   - `source-prefix`: (Optional) The folder or prefix within the source bucket. If you want to copy everything in the bucket, omit this.
   - `destination-bucket-name`: The name of the destination S3 bucket.
   - `destination-prefix`: (Optional) The folder or prefix within the destination bucket where you want to copy the files. If you want to copy to the root of the destination bucket, omit this.
   - `--recursive`: Use this flag if you want to copy all files and subfolders recursively.

   Example:
   ```bash
   aws s3 cp s3://my-source-bucket/data/ s3://my-destination-bucket/backups/ --recursive
   ```

3. **Verify the Copy**: After the copy operation is complete, you can verify that the files are in the destination bucket by listing its contents:

   ```bash
   aws s3 ls s3://destination-bucket-name/destination-prefix
   ```

   Replace `destination-bucket-name` and `destination-prefix` with your actual destination bucket and prefix.

That's it! You've successfully copied files from one S3 bucket to another using the AWS CLI. Remember to set the appropriate permissions on the buckets to allow the AWS CLI to access and copy files between them.
