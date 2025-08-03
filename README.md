# AWS-Educate-Simulation-Getting-Started-with-Amazon-S3
AWS S3 Static Website Simulation: Step-by-step guide to bucket creation, permissions, versioning, and presigned URL usage for hosting secure, scalable static sites

🚀 Getting Started with Amazon S3: Static Website Simulation
This simulation walks you through the process of setting up a static website using Amazon Simple Storage Service (Amazon S3). You'll configure the service, upload content, manage permissions, and secure access to your data.

🧠 Objectives
By the end of this simulation, you will be able to:

Create an S3 bucket

Configure static website hosting

Upload website content

Enable public access

Share objects securely with presigned URLs

Apply a bucket policy to protect content

Update website files

View object versions

⏳ Duration
Approximately 30 minutes

✅ Prerequisites
Completion of the Getting Started with Storage course

⚠️ Simulation Environment
This is a guided simulation in a non-live AWS environment. Only the instructed actions are permitted. Errors will prompt corrective guidance.

📋 Tasks Overview
Task 1: Create a Bucket
Navigate to Amazon S3 in AWS Console.

Click Create bucket, name it sim-website.

Set Object Ownership to ACLs enabled.

Disable Block all public access and acknowledge the warning.

Enable Bucket Versioning.

Add a tag:

Key: Department

Value: Marketing

Click Create bucket.

Task 2: Configure Static Website Hosting
Open the bucket sim-website.

Go to Properties → Static website hosting → Edit.

Enable hosting and configure:

Index document: index.html

Error document: error.html

Save changes.

Open the Bucket website endpoint (expect a 403 error for now).

Task 3: Upload Website Files
Go to the Objects tab.

Click Upload → Add files: index.html, script.js, style.css.

Click Upload, then Close.

Task 4: Enable Public Access to Files
Select all uploaded files.

Choose Actions → Make public using ACL.

Confirm and make them public.

Refresh the website endpoint to view your static site.

Task 5: Share Object Securely with Presigned URL
Upload new-report.png.

Select the file → Actions → Share with a presigned URL.

Set expiration to 2 minutes and generate the URL.

Open the URL in a new tab to access the file.

Refresh after 2 minutes to see access denied.

Task 6: Secure Bucket with a Policy
Apply the following policy to prevent file deletion:

json
Copy
Edit
{
  "Version": "2012-10-17",
  "Id": "MyBucketPolicy",
  "Statement": [
    {
      "Sid": "BucketPutDelete",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:DeleteObject",
      "Resource": [
        "arn:aws:s3:::sim-website/index.html",
        "arn:aws:s3:::sim-website/script.js",
        "arn:aws:s3:::sim-website/style.css"
      ]
    }
  ]
}
Navigate to Permissions → Bucket policy → Edit.

Paste and save the policy.

Try to delete index.html — it should fail.

Task 7: Update Website Content
Edit index.html and replace:

csharp
Copy
Edit
Served from Amazon S3
with:

csharp
Copy
Edit
Created by Jane
Re-upload the updated index.html.

Make the file public again via ACL.

Refresh your site to view the updated content.

Task 8: Explore File Versioning
Click Show versions.

Observe multiple versions of index.html.

Note: Versioning allows you to restore earlier file versions.

📌 Summary
You have:

Built and deployed a static website using Amazon S3

Shared and secured files using ACLs, presigned URLs, and bucket policies

Enabled versioning for content recovery

Your website is now globally accessible with high availability and no server infrastructure.
