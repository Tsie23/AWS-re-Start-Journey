# Networking Notes

## What is Networking?

Networking is a way that computing devices like computers, servers, phones and databases connect and talk to each other to share data and resources. This happens over wires like Ethernet Cables, or wirelessly like Wi-fi. AWS uses software to create connections instead of setting up physical cables.

### Examples
- VPC (Virtual Private Cloud)
A VPC is your private network inside AWS. You control who enters/has access, which systems can talk to each other, and what stays public or private. 

- Internet Gateway


- Route Tables

## Key Concepts
- AZ Scaling (Availability Zone)
- CIDR Block (Classless Inter-Domain Routing Block)
- NACL(Network Access Control List)
- Security Groups
- Route 53

## Reflection
Networking is the foundation of everything built in AWS. Without a properly configured VPC, the servers can't talk to the databases, and user's cant reach the application. A critical step is learning how to define Subnets and use Security Groups, to enusre that you securely launch applications; Web Servers go in a Public Subnet with permission from a Security Group foor web traffic(Port 80/443), and databases go in a private subnet with a highly restricted Security Group. This structure keeps the sensitive data completely isolated from public internet. Networking relies on Protocols such as TCP/ip to make sure data is sent in small chunks called Packets and arrives at the right destination correctly.