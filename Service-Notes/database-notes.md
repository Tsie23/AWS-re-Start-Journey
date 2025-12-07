# Database Design Notes

## What is a Database?

A database is a cloud-based offering that helps you store, manage, and retrieve data efficiently without you having to manage any physical server. Simply put, it is an organized place on a computer where information is stored.

## Examples
- Amazon RDS(Relational Database Service)
- Amazon Aurora: a relational database
- Amazon DynamoDB: a NoSQL database
- Amazon ElastiCache: a data warehouse
- Amazon Redshift: an in-memory cache

## Key Concepts
- Relational vs. NoSQL
*Relational*: uses a strict tables with defined relationships between them, and is ideal for complex structured data. 
*NoSQL*: is flexible and uses formats like key-value pairs or documents, and is ideal for rapid reading/writing and handling changing data structures.
- Managed Services: a fully managed database is when aws handles the setting up of the operating system, patching, backups, and fault tolerances; you just focus on using the data. 
- Severless: is for services such as DynamoDB. Severless means you dont have to worry about provisioning sever capacity, AWS automatically handles scaling up and down based on your usage. 
- High Availability & Multi-AZ: ensuring that should one part of an AWS region fail your database data is safely replicated in another Availability Zone(AZ) and quickly recovered, keeping your application online.
- Read Replicas: are read-only copies of your main database, that help improve performance by offloading read traffic(ie. searches) from the main database instance.

## Reflection
I understand that AWS offers different database services specialized for different needs. Database design is about reducing duplication and organizing data to match real-world relationships. Amazon offers both traditional or highly-structured database such as Amazon Aurora and serverless database like DynamoDB, with a Pay-as-you-go option.
