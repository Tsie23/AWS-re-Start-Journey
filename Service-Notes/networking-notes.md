# Networking Notes

## What is Networking?

Networking is a way that computing devices like computers, servers, phones and databases connect and talk to each other to share data and resources. This happens over wires like Ethernet Cables, or wirelessly like Wi-fi. AWS uses software to create connections instead of setting up physical cables.

### Examples
- VPC (Virtual Private Cloud)
A VPC is your private network inside AWS. You control who enters/has access, which systems can talk to each other, and what stays public or private. 

## Core VPC Components
- Subnets
Are smaller sections you create inside your VPC. A subnet must live enirely within one AZ(Availability Zone), which is a physically separate data center. Subnets are broken into Public and Private Subnets.

* Public Subnets resources like a web server, can connet directly to the public internet.
* Private Subnets resources such as a database server, are isolated and cannot be reached from the public internet, which keeps them secure.

- Internet Gateway(IGW)
Is a component that allows communication between resources in your VPC, and the internet. You attach this to your VPC to make it "public".

- Route Tables
Are like a map or a set of driving directions. They contain rules that tell network traffic(the data packets) where to go inside the VPC and where to go to leave the VPC(like routing traffic to the IGW).

## Key Concepts
- AZ Scaling (Availability Zone)
This is a separate and isolated data center in an AWS Region. Subnets must be created in a single AZ to ensure high availability so that should one AZ fail, your resources in another AZ are kept running.

- CIDR Block (Classless Inter-Domain Routing Block)
CIDR stands for Classless Inter-Domain Routing. This is the way you define the range of private IP addresses for your entire Virtual Private Cloud(VPC) e.g., 10.0.0.0/16

- Elastic IP (EIP)
This is a fixed/static public IP address that you can reserve and associate with an EC2 instance. Unlike the default public IP, the EIP remains the same even if you stop then restart the instance.

- Security Groups(SG)
This is a virtual firewall that controls inbound(in) and outbound(out) traffic for one specific resource such as one EC2 server. They act at the instance level.

- Route 53
Is AWS's Domain Name System(DNS) WEB SERVICE. It translates human-readable domain names like google.com into a computer's numerical IP address (e.g., 192.0.2.1)

- NACL(Network Access Control List)
This is another type of firewall that controls traffic for an entire Subnet. It is an optional, yet powerful layer of security that acts before the traffic even reaches the security group.

- Load Balancer
Is a service that automatically distributes incoming application traffic accross multiple EC2 instances, to increase the capacity and fault tolerance of the application.

## Reflection
Networking is the foundation of everything built in AWS. Without a properly configured VPC, the servers can't talk to the databases, and user's cant reach the application. A critical step is learning how to define Subnets and use Security Groups, to enusre that you securely launch applications; Web Servers go in a Public Subnet with permission from a Security Group foor web traffic(Port 80/443), and databases go in a private subnet with a highly restricted Security Group. This structure keeps the sensitive data completely isolated from public internet. Networking relies on Protocols such as TCP/IP to make sure data is sent in small chunks called Packets and arrives at the right destination correctly.