# Servers Notes

## What is Servers?
- Before the cloud, a "server" was a physical machine you bought, placed in a data center, and managed entirely yourself from from the wiring to the operating system updates.
- When we talk about servers in AWS, we're refering to the Amazon Elastic Compute Cloud (EC2) instances that is basically a virtual computer that AWS lets you rent on their infrastructure.

### Examples
* **Amazon EC2 (Elastic Compute Cloud)**: It provides resizable compute capacity in the cloud, acting as a virtual machine where you choose the operating system, manage the software, and have full administrative control, just like a dedicated physical server.

* **Amazon Lightsail**: This service offers Virtual Private Servers (VPS), which are simplified, bundled EC2 instances designed to be an easy-to-use alternative for hosting simple websites or applications.

## Key Concepts
- *Amazon Machine Image (AMI)*: This is the pre-configured template, or blueprint, for your instance. It determines the operating system (e.g., Windows, Linux) and any pre-installed software. It's how you launch a ready-to-go server without manually installing the OS.

- *Instance Type*: This is the hardware specification. It defines the amount of CPU and Memory (RAM) your virtual server gets. The t2.micro or t3.micro are classic Burstable types we start with, designed for general-purpose, low-traffic workloads.

- *Security Groups*: This is the virtual firewall for your instance. It controls all inbound and outbound network traffic. You absolutely must configure rules (like allowing SSH on port 22 or HTTP on port 80) to let people connect, but you only allow the traffic you need.

- *Key Pairs*: This is the secure credential used to log in to a Linux instance via SSH (Secure Shell). You generate a public/private key pair: AWS stores the public key, and you keep the private .pem file safe.

- *Elastic Block Store (EBS)*: This is the permanent block storage volume that attaches to your EC2 instance. It’s essentially the hard drive, and its data persists even if the instance stops or fails.

## Reflection
A service like Amazon EC2 provides instant, powerful virtual servers that you can launch in minutes instead of waiting weeks for physical hardware. With the advantage being it's on-demand scalability, allowing you to quickly setup up new resources when needed, and shut them down just as fast to meet fluctuating demand. Paying only for the exact compute time used/consumed, making this powerful computing resources accessible to everyone.