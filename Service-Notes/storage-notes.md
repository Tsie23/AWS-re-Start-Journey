# Storage Notes

## What is Storage
Storage is where you keep your digital stuff, like putting files on your laptop or phone. When talking about the cloud, storage refers to the way we securely keep our data accessible and safe. The most popular way data is stored on AWS is through an object storage service, which is different from the file system used on phones and laptops.

## Types of Storage
- Amazon S3(Simple Storage Service): is an object storage service known for its scalability, security, availability, and performance. You can store and Protect any amount of data for a number of use cases.It stores data as objects inside containers called buckets.

- EBS: Block storage for EC2
- EFS: Network file system

## Use Cases
- S3 uses cases include data lakes, static websites, application hosting, backup/disaster recovery. 
- EBS for app data (like databases)
- EFS for shared file access across instances

## Reflection
My biggest takeaway from this is how flexible and powerful AWS storage is. It is not just about one simple hard drive in the cloud;they designed a whole system to cater for different needs. Understanding the difference between object and block storage helped me figure out when best to utilise each service.


ebs/ ef/ s3