# Networking Lab: Configuring a VPC

## Objective
- Create a VPC with a private and public subnet, an internet gateway, and a NAT gateway.
- Configure route tables associated with subnets to local and internet-bound traffic by using an internet gateway and a NAT gateway.
- Launch a bastion server in a public subnet.
- Use a bastion server to log in to an instance in a private subnet.

## Steps Taken
### Task 1: Creating a VPC
1. Go to the VPC Management Console.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134059.png>)

2. Choose Your VPCs, then Create VPC.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134202.png>)

3. Configure the following options:
 * Resources to create: VPC only.
 * Name tag: Enter Lab VPC.
 * IPv4 CIDR block: Choose IPv4 CIDR manual input.
 * IPv4 CIDR: Enter 10.0.0.0/16.
 * IPv6 CIDR block: Choose No IPv6 CIDR block.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134456.png>)

 * Tenancy: Choose Default.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134550.png>)

4. Choose Create VPC.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134610.png>)

5. Select the new Lab VPC.

6. Choose Actions, then Edit VPC settings.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134648.png>)

7. In the DNS settings section, select Enable DNS hostnames.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134732.png>)

8. Choose Save.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 134921.png>)

### Task 2: Creating Subnets
#### Task 2.1: Creating a Public Subnet
9. In the left navigation pane, choose Subnets.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135111.png>)

10. Choose Create subnet and configure the following options:
* VPC ID: Choose Lab VPC.
 * Subnet name: Enter Public Subnet.
 * Availability Zone: Choose the first Availability Zone in the list.
 * IPv4 CIDR block: Enter 10.0.0.0/24.
 * Choose Create subnet.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135158.png>) 
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135324.png>)
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135357.png>)

11. Select Public Subnet, and *Click* Actions, then Edit subnet settings.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135632.png>)

12. In the Auto-assign IP settings section, select Enable auto-assign public IPv4 address.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135719.png>)

13. Choose Save.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135753.png>) 
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135808.png>)

#### Task 2.2: Creating a Private Subnet
14. Choose Create subnet and configure the following options:
 * VPC ID: Choose Lab VPC.
 * Subnet name: Enter Private Subnet.
 * Availability Zone: Choose the first Availability Zone in the list.
 * IPv4 CIDR block: Enter 10.0.2.0/23.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 135930.png>) 
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140034.png>) 
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140057.png>)

15. Choose Create subnet.

### Task 3: Creating an Internet Gateway (IGW)
16. In the left navigation pane, choose Internet gateways. Then select *Create internet gateway*.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140253.png>)

17. For Name tag, enter Lab IGW.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140329.png>)

18. Choose Create internet gateway.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140344.png>)

19. Choose Actions, then choose Attach to a VPC.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140411.png>)

20. Choose Lab VPC and select Attach internet gateway.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140702.png>)
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 140544.png>)

### Task 4: Configuring Route Tables
21. In the left navigation pane, choose Route tables.
22. Select the existing route table for Lab VPC.
23. In the Name column, choose the edit icon, enter Private Route Table, and choose Save.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141120.png>)
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141247.png>)

24. Choose Create route table and configure the following options:
 * Name - optional: Enter Public Route Table.
 * VPC: Choose Lab VPC.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141349.png>) 

25. Choose Create route table.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141418.png>)

26. Select Public Route Table, and go to the Routes tab.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141502.png>)

27. Choose Edit routes.![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141515.png>)

28. Choose Add route and configure:
 * Destination: Enter 0.0.0.0/0.
 * Target: Choose Internet Gateway, then choose Lab IGW.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141555.png>)

29. Choose Save changes.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141612.png>)

30. Choose the Subnet associations tab.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141711.png>)

31. Choose Edit subnet associations and select *Public Subnet*.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 141746.png>)

32. Choose Save associations.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 142151.png>)

### Task 5: Launching a Bastion Server
33. Go to the EC2 Management Console. Choose Instances, then Launch instances.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 142519.png>)

34. Configure the following options:
 * Name and tags: Enter Bastion Server.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 142620.png>)

 * Application and OS Images: Choose Amazon Linux 2023 AMI.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 142712.png>)

 * Instance type: Choose t3.micro.
 * Key pair (login): Choose Proceed without a key pair (Not recommended).
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 142754.png>)

 * Network settings (Choose Edit):
   * VPC - required: Choose Lab VPC.
   * Subnet: Choose Public Subnet.
   * Auto-assign public IP: Choose Enable.
   * Firewall (security groups): Choose Create security group.
   * Security group name - required: Enter Bastion Security Group.
   ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 143004.png>)

   * Description - required: Enter Allow SSH.
   * Inbound security groups rules: Type: SSH, Source type: Anywhere.
   ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 143103.png>)

35. Choose Launch instance.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 143229.png>)

### Task 6: Creating a NAT Gateway (NAT GW)
36. Go to the NAT gateways section.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 143542.png>)

37. Choose Create NAT gateway and configure the following options:
 * Name: Enter Lab NAT gateway.
 * Subnet: Choose Public Subnet.
 ![alt text](<images/Configuring VPC/Screenshot 2025-12-11 144552.png>)

 * Choose Allocate Elastic IP.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 144621.png>)

38. Choose Create a NAT gateway.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 144640.png>)
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 144656.png>)

39. Go to Route tables, and select Private Route Table.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 144844.png>)

40. Choose the Routes tab, then Edit routes.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 145022.png>)

41. Choose Add route and configure:
 * Destination: Enter 0.0.0.0/0.
 * Target: Choose NAT Gateway, then choose the nat- (Lab NAT gateway) from the list.
42. Choose Save changes.
![alt text](<images/Configuring VPC/Screenshot 2025-12-11 145127.png>)

## Challenges
- After creating the VPC and subnets, the network had no internet access, creating a NAT Gateway remedied the error.

## Takeaways
I have learned that creating a VPC gives you a logically isolated network, but you have to explicitly connect it to the internet using an IGW(Internet Gateway). The Route Table dictates whether a subnet is public or private. If a route table sends *0.0.0.0/0* traffic to an IGW, it's public, and if it sends it to a NAT Gateway, it's private. The secure access method is always Public $\rightarrow$ Bastion host $\rightarrow$ Private Instance. This is a critical security pattern for production environments.
