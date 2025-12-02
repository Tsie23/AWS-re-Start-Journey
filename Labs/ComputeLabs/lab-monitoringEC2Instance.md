# Compute Lab: Monitoring your EC2 Instance

## Objective
- Create an Amazon SNS notification
- Configure a CloudWatch alarm
- Stress test an EC2 instance
- Confirm that an Amazon SNS email was sent
- Create a CloudWatch dashboard

## Steps Taken
The lab was completed in three main parts with steps inside each part.

#### Part 1: Configure the Notification Channel (Amazon SNS)

1. Created a *Standard* Amazon SNS topic named `MyCwAlarm`.
2. Created a subscription for the new topic using the **Email** protocol and a valid, accessible email address as the endpoint.
3. Opened the AWS notification email and chose **Confirm subscription** to activate the email endpoint. 
4. The subscription status was verified as *Confirmed* in the AWS console.
![Configure Key Pair Login](images/Launch%20EC2%20Instance/3.%20Enter%20'Bastion%20host'%20in%20Name&Tags%20section.png "Fill in Names and Tags field") In the Key Pay Login section select "Proceed without Key Pair" from the *Key Pair Name - Required" drop-down list.

#### Part 2: Create the Monitoring Alarm (CloudWatch)

1. Accessed CloudWatch on the console manager and viewed *Per-Instance Metrics* under the EC2 service to locate the `CPUUtilization` metric for the *Stress Test* EC2 instance.
2. Initiated the creation of a new metric alarm.
3. Selected the `CPUUtilization` metric for the *Stress Test* instance, setting the **Statistic** to *Average* over a **Period** of *1 minute*.
4.  **Set the Threshold:** Defined the alarm condition to trigger when `CPUUtilization` is **Greater** than a threshold value of **60** (percent).
5.  **Configure the Action:** Set the **Alarm state trigger** to *In alarm* and linked it to send a notification to the newly created **MyCwAlarm** SNS topic.
6.  **Name and Create:** Named the alarm `LabCPUUtilizationAlarm` and finalized the creation.
![Configure Key Pair Login](images/Launch%20EC2%20Instance/3.%20Enter%20'Bastion%20host'%20in%20Name&Tags%20section.png "Fill in Names and Tags field") In the Key Pay Login section select "Proceed without Key Pair" from the *Key Pair Name - Required" drop-down list.

#### Part 3: Test the Alarm and Create a Dashboard**

1. Logged into the *Stress Test* EC2 instance using the provided link and ran the command `sudo stress --cpu 10 -v --timeout 400s` to force the CPU load to *100%*.
2. Observed the CloudWatch Alarms page and refreshed until the `LabCPUUtilizationAlarm` status changed to *In alarm*. The graph visually confirmed the CPU spike above the 60% threshold.
3. Checked the linked email inbox for the expected **AWS Notifications** email, confirming the alarm successfully triggered the SNS notification.
4. Created a CloudWatch dashboard named `LabEC2Dashboard` and added a line widget displaying the `CPUUtilization` metric for the *Stress Test* instance for quick access to monitoring data.


## Challenges
- I quite enjoyed doing this lab, i did not encounter any notable challenges. The guide was clear and easy to follow along.

## Screenshot
![Configure Key Pair Login](images/Monitor%20EC2%20Instance/Screenshot%202025-11-26%20081606.png "Fill in Names and Tags field") In the Key Pay Login section select "Proceed without Key Pair" from the *Key Pair Name - Required" drop-down list.

## Takeaways
This lab focused on the essential practices of logging and monitoring to ensure system performance and security. The core task was to establish an automated alert system using AWS services. This system needed to detect when the EC2 instance's central processing unit (CPU) usage spiked—simulating a critical event like a malware attack or unauthorized resource misuse. By setting up a CloudWatch alarm and integrating it with an SNS email notification, the goal was to instantly alert an administrator when the system was under stress. 

The setup showed that monitoring isn't just about reviewing historical data; it's about being instantly notified when performance baselines are breached (like a 60% CPU threshold). This is vital for detecting and responding to potential threats like malware or unauthorized resource usage quickly.

The stress test provided a tangible, hands-on way to understand how a real-world event—a sharp, sustained spike in resource usage—translates into a measurable metric that then crosses a defined threshold to initiate a defined action.