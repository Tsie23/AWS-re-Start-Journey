# Compute Notes

## What is Compute?

Compute refers to cloud-based services that provide processing power, and infrastructure to run applications on-demand, without managing physical servers. Key services include Amazon EC2 for virtual servers, AWS S3 for cloud storage solutions, Lambda for serverless code execution, Compute is the processing power that lets your application run. In the cloud, this usually refers to virtual machines, containers, or serverless functions.

### Examples
- EC2 (virtual servers)
An EC2 is a computer in the cloud that you cant physically touch, and lives in Amazon's data centres. You get to choose and setup how strong it must be, how much storage it has, and which operating system it uses. An EC2 instance is similar to renting a computer and only pay for it for the duration you are using it.

- Lambda (serverless functions)
Is a serverless function that lets you run code without creating or managing a server. It works similar to a light with motion sensors that switches on only when someone wallks past then switches off immediately afterwards. Lambda works the same way, by running code only when triggered.

- S3 (storage solution)
Amazon S3(Amazon Simple Storage Service) is an online storage service similar to a folder on your desktop. S3 stores files like Images, Videos, PDF', Web Assets, and Backups. It is secure, cheap, and holds unlimited data. You could say that an S3 is a massive online warehouse where you're able to store boxes(aka files), and organise them in sections (aka buckets), and curate access permission according to who needs to do what with thw files in the bucket.

## Key Concepts
- Scaling (vertical vs horizontal)


- AMIs (Amazon Machine Images)
An AMI is a type of a template for making new EC2 servers. It contains the operating system, pre-installed software, customized settings and security configurations.

- Load Balancers
Acts like a traffic controller, it receives all incoming requests and spreads them across multiple servers so none of them gets overloaded. It improves speed, prevents crashes, and keeps the system stable. It is similar to a traffic officer directing traffic during loadshedding. 

## Reflection
I now understand that AWS compute is the processing power, memory, and infrastructure needed to run applications in the cloud instead of on physical hardware. EC2 is when a user rents virtual computers (called instances) and configures them with specific amounts of CPU, memory, and storage, whilst taking pricing into consideration. Resources can be scaled up or down based on demand, pay only for what you use, and have the infrastructure managed by AWS. Compute is not just about "running code"—it's about choosing the right type of resource for performance, cost, and maintenance.

 