# Storage Notes

## What is Storage
Storage is where you keep your digital stuff, like putting files on your laptop or phone. When talking about the cloud, storage refers to the way we securely keep our data accessible and safe. The most popular way data is stored on AWS is through an object storage service, which is different from the file system used on phones and laptops.

## Types of Storage
- Amazon S3(Simple Storage Service): is an object storage service known for its scalability, security, availability, and performance. You can store and Protect any amount of data for a number of use cases.It stores data as objects inside containers called buckets.

- EBS(Elastic Block Store): acts as a dedicated, persistent hard drive for a single cloud server. It is a Block storage, which means the data is stored in individual, unformatted blocks, just like a traditional hard disk. I can be attached to only one EC2 instance at a time. The data reamins even if the EC2 instance is stopped or terminated, making it a persistent storage.

- EFS(Elastic File System): is a file storage that acts as a traditional shared file system, allowing you to organize data into folders and files similar to a network-attached storage or NAS.

## Use Cases
- Amazon S3 uses cases include data lakes, static websites, application hosting, backup/disaster recovery. 
- Amazon EBS used for *Boot Volumes* for "C: Drive" of your server, *Databases* like MySQL or PostgreSQL, and *Single_Server Applications* that need fast, dedicated storage.
- Amazon EFS used for web applications that need to share the same files such a website images or logs, development environments where multiple delopers need access to the same codebase, and Content Management Systems.

## Reflection
My biggest takeaway from this is how flexible and powerful AWS storage is. It is not just about one simple hard drive in the cloud;they designed a whole system to cater for different needs. Understanding the difference between object and block storage helped me figure out when best to utilise each service.


ebs/ ef/ s3