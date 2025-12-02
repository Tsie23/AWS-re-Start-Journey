# Compute Lab: Launching an EC2 Instance / Working with AWS Lambda

## Objective
Create a directory

## Steps Taken
1. Launched EC2 Instance
2. Choose an AMI(Amazon Machine Image) 
3. Choose Instance type
4. Configure a Key Pair
5. Configure Network Settings
6. Add Storage
7. Configure Advanced details
8. Launch Instance

## Challenges
- Struggled with the touch command, getting the right code to get the desired script output
- Solved by consulting AI for assistance with the touch command and automation

## Screenshot
* Step 1
![Open EC2 Instance](images/Launch%20EC2%20Instance/1.%20Open%20EC2%20instance%20in%20management%20console.png "Open EC2 Instance in Management Console")
Search for EC2 in the search bar on the Management console, and then select to open.

![Launch Instance Window](images/Launch%20EC2%20Instance/2.%20Open%20launch%20instance%20menu.png "Open Launch instance window")
Click on launch instance button, and open the launch instance window.

![Populate Names and Tags](images/Launch%20EC2%20Instance/3.%20Enter%20'Bastion%20host'%20in%20Name&Tags%20section.png "Fill in Names and Tags field")

* Step 2
![Choose AMI](images/Launch%20EC2%20Instance/4.%20Choose%20AMI.png "Confirm 'Amazon Linux' is selected in Quick Start") In the Quick Start section, select "Amazon Linux".

* Step 3
![Choose Instance Type](images/Launch%20EC2%20Instance/3.%20Enter%20'Bastion%20host'%20in%20Name&Tags%20section.png "Select Instance type") In the Instance type Section, click on the drop down menu and select t3.micro

* Step 4
![Configure Key Pair Login](images/Launch%20EC2%20Instance/3.%20Enter%20'Bastion%20host'%20in%20Name&Tags%20section.png "Fill in Names and Tags field") In the Key Pay Login section select "Proceed without Key Pair" from the *Key Pair Name - Required" drop-down list.

* Step 5 - in the Network Settings section choose "Edit"
![Configure Network Settings](images/Launch%20EC2%20Instance/7.%20VPC%20required%20'LabVPC.png "Set up network settings")

* Step 6
![Configure Key Pair Login](images/Launch%20EC2%20Instance/6.%20Key%20Pair%20login.png "Fill in Names and Tags field")

* Step 7
![Configure Advanced Details](images/Launch%20EC2%20Instance/10.%20Advanced%20details.png "Fill in Names and Tags field")

* Step 8
![Launch Instance](images/Launch%20EC2%20Instance/11.%20Launch%20instance.png "A Launch Instance  success message")

## Takeaways
Automation is the most effective way to run a directory, as opposed to hardcoding. A misplaced parenthesis can drastically change the script output.
