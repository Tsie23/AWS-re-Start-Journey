# Storage Lab: EBS or S3

## Objective
- Run AWS CLI commands that use IAM and Amazon S3 services.
- Deploy a static website to an S3 bucket.
- Create a script that uses the AWS CLI to copy files in a local directory to Amazon S3.

## Steps Taken
1. CLI Setup and S3 Bucket Creation
* Configured the AWS CLI on the CLI Host instance with provided AccessKey and SecretKey and set the region to us-west-2.
* Created a unique S3 bucket named s3://<cafe-xxxnnn> using the command aws s3 mb.
* Uploaded initial image files to the bucket under the /images prefix using aws s3 sync.
* Verified the file upload using the aws s3 ls command.

2. IAM Permission Review and Testing
* Reviewed the existing IAM group (mediaco) and IAM user (mediacouser) policies to understand their permissions.
  - The policies explicitly permitted the user to list buckets, list objects at the root level, and perform read, write, and delete actions (GetObject, PutObject, DeleteObject) only within the cafe-*/images/* folder.
* Signed in to the Console as mediacouser to test the permissions:
  - View Test: Successfully opened a .jpg file from the /images folder.
  - Upload Test: Successfully uploaded a file from the local machine to the /images folder.
  - Delete Test: Successfully deleted a file from the /images folder.
  - Unauthorized Test: Attempted to view the Bucket Permissions tab and upload a file to the bucket root, which both correctly displayed an "Insufficient permissions" error.

3. S3 Event Notification Configuration
* Created an SNS Topic named s3NotificationTopic in the SNS console.
* Granted S3 permission to publish to the topic by modifying the Topic Access Policy, ensuring the policy specified the S3 service principal and the correct Source ARN (the S3 bucket).
* Created an email subscription to the s3NotificationTopic and confirmed the subscription via email.
* Created a JSON configuration file (s3EventNotification.json) to specify:
  - The destination TopicArn.
  - The events to watch for: s3:ObjectCreated:* and s3:ObjectRemoved:*.
  - A prefix filter of images/ so notifications only trigger for files in that folder.
* Applied the configuration to the S3 bucket using the aws s3api put-bucket-notification-configuration command.
* Verified the initial setup by receiving an automated s3:TestEvent email notification.

4. Notification System Testing
* Reconfigured the CLI to use the mediacouser credentials.
* Tested Object Creation: Used aws s3api put-object to upload a new image.
  - Verified successful notification via an email with eventName: ObjectCreated:Put and the image key.
* Tested Object Deletion: Used aws s3api delete-object to remove an existing image.
  - Verified successful notification via an email with eventName: ObjectRemoved:Delete and the image key.
* Tested Object Read: Ran aws s3api get-object and confirmed no email notification was sent (as expected, since get events were not configured).
* Tested Unauthorized API Action: Ran aws s3api put-object-acl to try and change the file's permissions, which correctly resulted in an AccessDenied error.

## Challenges
- Struggled with the touch command, getting the right code to get the desired script output
- Solved by consulting AI for assistance with the touch command and automation

## Screenshot
![Challenge Instructions](images/Linux%20Lab%20Challenge%20Instructions.png "Instructions")
After launching the Linux terminal with SSH, you log into terminal as EC2-User, and proceed to running commands.
* Shows the successful setup of the access credentials and the confirmation message for the created S3 bucket.

* Displays the policy statements clearly defining read, write, and delete permissions restricted to the cafe-*/images/* path.

* Illustrates the successful execution of the unauthorized use case where the user is blocked from accessing bucket permissions.

* Highlights the JSON that grants the s3.amazonaws.com service principal permission to publish messages.

* Shows the aws s3api put-bucket-notification-configuration command being run, followed by the received email containing the s3:TestEvent payload.

## Takeaways
Automation is the most effective way to run a directory, as opposed to hardcoding. A misplaced parenthesis can drastically change the script output.
