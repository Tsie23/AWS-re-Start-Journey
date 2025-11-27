# Security Notes

## What is Security?

Security in the cloud is all about protecting your digital stuff, such as your data, applications, and your virtual computers from unauthorized access, theft, or damage. It simply means ensuring Confidentiality, Integrity, and Availability for everything you build.

- Confidentiality: keeping private data private, with only authorized people gaining access to it.
- Integrity: making sure the data is accurate, complete, and hasn't been tampered with.
- Availability: ensuring services and data are always accessible to the people who need them, even during an attack or disaster.

Cloud security uses technology, policies, and careful configurations to build string "digital walls" around your resources.

### Examples
Security in AWS follows the Shared Responsibility Model
- AWS Responsibility(Security *of* the Cloud)
AWS is responsible for protecting the infrastructure that runs all the cloud services, this includes the physiical facilities, hardware, the networking, and software that virtualizes the environment. They keep the data center secure and operating.

- Customer Responsibility(Security *in* the Cloud)
You, the user, are responsible for securing everything you put into the cloud, including encrypting your data before storing it(Encryption), managing who can log into your account and what they can do(IAM), as well as correctly setting up firewalls(Security Groups), and patching the operaating system of your virtual servers(EC2)

## Key Concepts
- IAM (Identity Access Management)
Is the gatekeeper for your AWS account. It lets you create Users and Roles, and then decide precisely whatservices and resources they are allowed to access, using policies/rules.

- Principle of Least Privilege
A critical rule stating that you should "always give users the minimum permissions they need to do their job, nothing more". This limits the potential damage if an account is compromised. 

- MFA(Multi-Factor Authentication)
Is requiring a second verification step, such as a code after putting in your password, in addition to the a password when logging in. You should always enable MFA on your root account. 

- Security Groups
Are virtual firewalls for EC2 instances(virtual computers), used to control traffic by allowing web traffic to come in from specific ports like Port 80 and block it from other ports.

- KMS(Key Management Service)
This managed service helps you create and manage encryption keys that protect your data. It simplifies the encryption process of the data stored in S3 and RDS.

- AWS WAF(Web Application Firewall)
This service protects your web applications from common web attacks, SQL injections or Cross-Site Scripting. It filters bad traffic before it reaches your application.

## Reflection
The most important part of being a cloud practitioner in AWS, is understanding security. It's not enough for AWS to be secure, I have to apply the correct security settings. My biggest takeaway is the Principle of Least Priviledge. I learned that it's safer to use an IAM Role with limited permissions for an application like an EC2 instance, to access a service like S3 than to assign the full administrator access.

Security is not a one-time setup, it needs constant checking. I need to make use of services like AWS Trusted Advisor to regularly check my configurations against AWS best practises to ensure my environment stays locked down and safe.