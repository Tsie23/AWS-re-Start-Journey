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

![Search for SNS](images/Monitor%20EC2%20Instance/1.%20Navigate%20to%20Simple%20Notification%20Service%20on%20Amazon%20Console%20Manager.png "Navigate to SNS on Management Console") 
In the Amazon Management Console, enter *Simple Notification Service(SNS)* in the search bar.

![Select Topic on left panel](images/Monitor%20EC2%20Instance/2.%20Select%20Topics%20on%20left%20panel.png "Select "Topics" on left pane") 
On the SNS page, select *Topics* on the left panel.

2. Created a subscription for the new topic using the **Email** protocol and a valid, accessible email address as the endpoint.
![alt text](<images/Monitor EC2 Instance/6.1.png>) 
![alt text](<images/Monitor EC2 Instance/6.2.png>)

3. Opened the AWS notification email and chose **Confirm subscription** to activate the email endpoint. 
![alt text](<images/Monitor EC2 Instance/10. Subscription confirmed.png>)

4. The subscription status was verified as *Confirmed* in the AWS console.
![alt text](<images/Monitor EC2 Instance/11. Subscription status confirmed.png>)

#### Part 2: Create the Monitoring Alarm (CloudWatch)

1. Accessed CloudWatch on the console manager and viewed *Per-Instance Metrics* under the EC2 service to locate the `CPUUtilization` metric for the *Stress Test* EC2 instance.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 084553.png>)

2. Initiated the creation of a new metric alarm.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 084626.png>)

3. Selected the `CPUUtilization` metric for the *Stress Test* instance, setting the **Statistic** to *Average* over a **Period** of *1 minute*.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 084859.png>)

4.  **Set the Threshold:** Defined the alarm condition to trigger when `CPUUtilization` is **Greater** than a threshold value of **60** (percent).
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 085046.png>)

5.  **Configure the Action:** Set the **Alarm state trigger** to *In alarm* and linked it to send a notification to the newly created **MyCwAlarm** SNS topic.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 085206.png>)

6.  **Name and Create:** Named the alarm `LabCPUUtilizationAlarm` and finalized the creation.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 085623.png>)
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 085803.png>)

#### Part 3: Test the Alarm and Create a Dashboard**

1. Logged into the *Stress Test* EC2 instance using the provided link and ran the command `sudo stress --cpu 10 -v --timeout 400s` to force the CPU load to *100%*.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 093312.png>)

2. Observed the CloudWatch Alarms page and refreshed until the `LabCPUUtilizationAlarm` status changed to *In alarm*. The graph visually confirmed the CPU spike above the 60% threshold.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 093617.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 094151.png>)

3. Checked the linked email inbox for the expected **AWS Notifications** email, confirming the alarm successfully triggered the SNS notification.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 094348.png>)

4. Created a CloudWatch dashboard named `LabEC2Dashboard` and added a line widget displaying the `CPUUtilization` metric for the *Stress Test* instance for quick access to monitoring data.
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 094816.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 094848.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 094943.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 095019.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 095059.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 095132.png>) 
![alt text](<images/Monitor EC2 Instance/Screenshot 2025-11-26 095213.png>)

## Challenges
- I quite enjoyed doing this lab, i did not encounter any notable challenges. The guide was clear and easy to follow along.

## Takeaways
This lab focused on the essential practices of logging and monitoring to ensure system performance and security. The core task was to establish an automated alert system using AWS services. This system needed to detect when the EC2 instance's central processing unit (CPU) usage spiked—simulating a critical event like a malware attack or unauthorized resource misuse. By setting up a CloudWatch alarm and integrating it with an SNS email notification, the goal was to instantly alert an administrator when the system was under stress. 

The setup showed that monitoring isn't just about reviewing historical data; it's about being instantly notified when performance baselines are breached (like a 60% CPU threshold). This is vital for detecting and responding to potential threats like malware or unauthorized resource usage quickly.

The stress test provided a tangible, hands-on way to understand how a real-world event—a sharp, sustained spike in resource usage—translates into a measurable metric that then crosses a defined threshold to initiate a defined action.