# Storage Lab: Creating a Website on Amazon S3

## Objective
- Run AWS CLI commands that use IAM and Amazon S3 services.
- Deploy a static website to an S3 bucket.
- Create a script that uses the AWS CLI to copy files in a local directory to Amazon S3.

## Steps Taken
1. CLI Setup and S3 Bucket Creation
* Configured the AWS CLI on the CLI Host instance with provided AccessKey and SecretKey and set the region to us-west-2.
* Created a unique S3 bucket named s3://ksennelo238 using the command aws s3 mb.
* Uploaded initial image files to the bucket under the /images prefix using aws s3 sync.
* Verified the file upload using the aws s3 ls command.

## Task 1: Connect to Your Amazon Linux EC2 Instance via SSM
1. First I use AWS Systems Manager (SSM) Session Manager for a secure, browser-based connection.
2. Choose the Details button at the top of your lab screen, then choose Show.
3. Copy the InstanceSessionUrl value.
4. Pasted that URL into a new web browser tab. A console connection will be made, and a prompt for the ssm-user will be displayed.
5. Run the following commands to switch to the working user and confirm your location: 
`sudo su -l ec2-user`
`pwd`

## Task 2: Configure the AWS CLI
6. In your SSH terminal window, run the configure command:
`aws configure`
7. At the prompts, I input the following details (grab the Key and Secret Key from the left pane):
 * AWS Access Key ID: Copy and paste the AccessKey value.
 * AWS Secret Access Key: Copy and paste the SecretKey value.
 * Default region name: Enter *us-west-2*
 * Default output format: Enter *json*

## Task 3: Create an S3 Bucket Using the AWS CLI
8. Used the aws s3api create-bucket command, making sure to replace <your-unique-bucket-name> with your chosen, unique name:
`aws s3api create-bucket --bucket <your-unique-bucket-name> --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2`
9. If successful, you'll see a JSON response that includes the Location of your shiny new bucket!
{
        "Location": "http://<your-unique-bucket-name>.s3.amazonaws.com/"
}

## Task 4: Create a New IAM User with S3 Full Access
10. Create the IAM User: `aws iam create-user --user-name awsS3user`
11. Create a Login Profile for the new user: `aws iam create-login-profile --user-name awsS3user --password Training123!`
12. Located the Account ID and Logged In as the New User:
 * In the AWS Management Console, click the account dropdown at the top right (it usually says VocLabsUser...)
 * Copied the 12-digit Account ID number
 * Chose Sign Out from the dropdown
 * On the sign-in screen, choose the IAM user radio button
 * Pasted the Account ID (no dashes) and choose Next
 * For IAM user name, I entered awsS3user
 * For Password, enter Training123!
 * Clicked the Sign In button
13. Searched for and chose S3 in the new console session, and got an error because awsS3user doesn't have permissions yet. 

14. Attach the Full S3 Access Policy: `
 * Back in your terminal, find the S3 policy name (optional, but good practice):`aws iam list-policies --query "Policies[?contains(PolicyName,'S3')]"`
 * Now, attach the AmazonS3FullAccess policy to your new user: `aws iam attach-user-policy --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess --user-name awsS3user`
 15. Return to the AWS Management Console and refresh the S3 browser tab. Your access should now be granted!

## Task 5: Adjust S3 Bucket Permissions
16. On the Amazon S3 console, select your bucket name.
17. Go to the Permissions tab.
18. Under Block public access (bucket settings), choose Edit.
 * Unselect/Deselect the option Block all public access.
 * Choose Save changes (confirm on the prompt).
19. While still on the Permissions tab, under Object Ownership, choose Edit.
 * Choose ACLs enabled.
 * Check the I acknowledge that ACLs will be restored box.
 * Choose Save changes.

## Task 6: Extract the Website Files
The static website content is packaged up; let's get it ready for deployment.

20. In my SSH terminal, I ran the following commands to navigate to the files, extract the archive, and then enter the website directory: `cd ~/sysops-activity-files`
`tar xvzf static-website-v2.tar.gz`
 `cd static-website`
21. Run `ls` to confirm you see index.html and the css and images directories.

## Task 7: Upload Files to Amazon S3 and Enable Hosting
22. Set the Index Document: This command tells S3 which file to load when someone visits the site's root URL. (Remember to replace <your-unique-bucket-name>.)aws s3 website s3://<your-unique-bucket-name>/ --index-document index.html
23. 

## Challenges
- Logging into the Management Console as awsS3user, presented a bit of a challenge due to permission restrictions. These were overcome by adjusting permissions using the AWS CLI.

## Takeaways
Automation is the most effective way to run a directory, as opposed to hardcoding. A misplaced parenthesis can drastically change the script output.
