# Networking Lab: VPC Labs 

## Objective
- Analyze the customer scenario and troubleshoot the network connection issue.

## Steps Taken
1. Used an SSH client (PuTTY/Terminal) to connect directly to the replica EC2 instance to troubleshoot the server process internally.
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 200910.png>)

2. Confirmed the Apache service was initially inactive and used sudo systemctl start httpd.service to get the web application running.
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 201006.png>)

3. After the application started, we attempted to reach the public IP in a browser, which still failed, signaling that the issue was external to the EC2 server itself.
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213745.png>)

4. Investigated the Virtual Private Cloud (VPC) networking components, including Route Tables and the Internet Gateway, to confirm internet access was correctly configured. Pinpointed the security configuration, eventually finding the problem in the Security Group associated with the EC2 instance.
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213706.png>) 

5. Modified the Security Group to create a new Inbound Rule, specifically allows all inbound traffic on Port 80 (HTTP).
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213455.png>) 
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213526.png>) 

6. Confirmed the Apache test window in browser is reachable using public IP, signaling the issue is resolved.
![alt text](<images/Troubleshooting Netwrork Issue/Screenshot 2025-11-30 213807.png>)

## Challenges
- I struggled with getting the Apache browser window to display, and had to retrace my steps in the troubleshooting process. I realised I needed to create another inbound rule that will establish connetion to port80 resulting in the display of the web browser. 

## Takeaways
When an EC2 instance isn't accessible, the first place to check after the application itself is the Security Group, as it acts as a virtual, stateful firewall for your server. This lab reinforced the critical concept that you have full control over your IaaS security and must explicitly open ports for your virtual server to be reachable by the world.
