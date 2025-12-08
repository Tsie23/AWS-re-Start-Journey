# Networking Lab: VPC Labs 

## Objective
- Analyze the customer scenario and troubleshoot the network connection issue.

## Steps Taken
1. Used an SSH client (PuTTY/Terminal) to connect directly to the replica EC2 instance to troubleshoot the server process internally.

2. Confirmed the Apache service was initially inactive and used sudo systemctl start httpd.service to get the web application running.

3. After the application started, we attempted to reach the public IP in a browser, which still failed, signaling that the issue was external to the EC2 server itself.

4. Investigated the Virtual Private Cloud (VPC) networking components, including Route Tables and the Internet Gateway, to confirm internet access was correctly configured.

5. Pinpointed the security configuration, eventually finding the problem in the Security Group associated with the EC2 instance.

6. Modified the Security Group to create a new Inbound Rule, specifically allows all inbound traffic on Port 80 (HTTP).

## Challenges
- I struggled with getting the Apache browser window to display, and had to retrace my steps in the troubleshooting process. I realised I needed to create another inbound rule that will establish connetion to port80 resulting in the display of the web browser. 

## Screenshot
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 200910.png>)

The terminal showed a successful SSH connection to the ec2-user@<public-ip> was established.

![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 200910.png>)

A console output confirmed the httpd.service was initially inactive before a start command was issued.

![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 201006.png>)

A second status check displayed the Apache service was now active (running) within the instance.

![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213730.png>)
A view of the EC2 Security Group Inbound Rules highlighted with all the Port access rule.

![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213807.png>)
The web browser successfully loaded the default Apache test page using the public IP, confirming the fix.

## Takeaways
When an EC2 instance isn't accessible, the first place to check after the application itself is the Security Group, as it acts as a virtual, stateful firewall for your server. This lab reinforced the critical concept that you have full control over your IaaS security and must explicitly open ports for your virtual server to be reachable by the world.
