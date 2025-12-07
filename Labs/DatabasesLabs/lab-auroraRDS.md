# Databases Lab: RDS & DynamoDB 

## Objective
1. Create an Aurora instance
2. Connect to a pre-created Amazon Elastic Compute Cloud(EC2)
3. Configure the Amazon EC2 instance to connect to Aurora
4. Query the Aurora instance

## Steps Taken
1. Create an Aurora instance
2. Connect to a pre-created Amazon Elastic Compute Cloud(EC2)
3. Configure the Amazon EC2 instance to connect to Aurora
4. Query the Aurora instance


## Challenges
- I kept getting the Syntax error because I had the aurora endpoint name in brackets<> when typing the query command in the terminal, remedied that by removing the brackets and running the SQL query again.

## Screenshot

![alt text](<images/Aurora RDS/CreateDatabase.png>)
![alt text](<images/Aurora RDS/CreateDatabase2.png>)
![alt text](<images/Aurora RDS/CreateDatabase3.png>)
![alt text](<images/Aurora RDS/CreateDatabase4.png>)
![alt text](<images/Aurora RDS/CreateDatabase5.png>)
![alt text](<images/Aurora RDS/CreateDatabase6.png>)
![alt text](<images/Aurora RDS/CreateDatabase7.png>)
![alt text](<images/Aurora RDS/CreateDatabase8.png>)
![alt text](<images/Aurora RDS/CreateDatabase9.png>)
![alt text](<images/Aurora RDS/CreateDatabase10.png>)

* Confirms the primary configuration settings used for launching the Aurora cluster.

![alt text](<images/Aurora RDS/DatabaseCreated.png>)
* Indicates the successful deployment and readiness of the database cluster.

![alt text](<images/Aurora RDS/PublicIP.png>)
* Highlights the specific URL used to establish a connection to the primary database instance.

![alt text](<images/Aurora RDS/MariaDBConnected.png>)
* Displays the connection to MariaDB message, confirming the EC2 instance can reach and log in to Aurora.

![alt text](<images/Aurora RDS/ComplexQueryOutput.png>)
* Illustrates the results of the complex query, returning only the two rows (Australia and Thailand) that met both criteria.

## Takeaways
When running query or commands syntax is very important, because simple things such as an extra space, missing parenthesis and even a semicolon when none is required could result in an error. 
