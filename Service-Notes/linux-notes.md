# Linux Notes

## What is Linux?
Linux is an operating system(OS) similar to Windows or MacOS, except it is completely free and open-source. In the cloud Linux is the industry standard. Most virtual servers and many AWS services run on some version of Linux because it is stable, secure, and very efficient. You interact with it through the use of a Command Line Interface(CLI) instead of a mouse and desktop.

### Examples
- Whenever you launch a virtual server(Amazon EC2 Instance), you choose an operating system. AWS offers their own optimized Linux version called Amazon Linux 2(or AL2023). This secure, high-performance environment is pre-configured to work with AWS services.

- Services like Amazon ECS(Elastic Container Service) and EKS(Elastic Kubernetes Service) run containers like Docker containers. These run on almost always on a very lightweight version of the Linux Distribution.

- AWS CLI runs on many operating systems, it is often installed and used directly on Linux EC2 instances for server-side management and scripting.

## Key Concepts
- Shell/Bash: is the program that accepts and executes your text commands. Bash is the most common shell.
- CLI(Command Line Interface): the text-based way of interacting with the computer. It is faster and more powerful for server administration than a graphical interface.
- SSH(Secure Shell): a secure protocol you use to connect remotely from your personal computer to a Linux EC2 instance running in the cloud.
- Package Manager(eg., yum or dnf in AL2023): is a tool used to easily install, update, and remove software on the Linux system.

## Reflection
Linux is the reliable foundation that keeps everything running, and mastering command line is essential for basic troubleshooting and configurations. My takeawy is that for me to move beyond just understanding the console and truly practice cloud engineerinng, I must become proficient in writing code to interact with the infrastructure. 