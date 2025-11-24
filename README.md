☁️ Charting My Course: From Designer to Cloud Practitioner

## Opening Salvo: The New Horizon

Hello, and welcome to my space! I’m Kebaabetswe A. Sennelo, and if you’re reading this, you’re catching me at the most exhilarating part of my professional life: the beginning. My passions have always centered around creation and protection. For years, I found creative expression in digital aesthetics, shaping user experiences and making things look good. Yet, beneath that surface interest, a deeper curiosity always simmered—the fascination with what makes things tick, how systems communicate, and critically, how to keep them safe.

This is where cloud computing steps in. It’s not just about servers and scalability; it’s the foundational infrastructure of the modern digital world. My interest is in building robust, high-performing, and secure architectures. My ultimate goal is to evolve from an emerging Backend Engineer, focused on the logic and data powering applications, into a seasoned Cybersecurity Professional—the person who ensures those systems are impermeable, reliable, and trusted. I see the cloud as the essential training ground for mastering both architecture and defense.

## About Me: The Road to the Cloud

My journey into technology wasn't conventional; it was a slow, deliberate ascent driven by relentless curiosity. I started by tinkering, teaching myself basic web design using drag-and-drop platforms. While those tools were fantastic for rapid prototyping and visual design, they soon felt limiting. I needed to understand the code, the why, and the how.

This led me to an intensive, self-paced online course, which provided the first taste of structured learning. Earning a place in a competitive scholarship program validated my commitment, but it was stepping into the AWS re/Start Cloud Practitioner learnership/program that felt like finding my true north.

AWS re/Start isn't just a certification path; it’s an immersive deep dive that has transformed my understanding of IT infrastructure. Suddenly, I wasn't just reading about the cloud—I was operating in it.

Cloud Compute & EC2: Learning to provision and manage EC2 instances taught me the fundamentals of computing resources, understanding how to select the right instance type for the job, and the concept of elasticity. 
- [Compute](./compute/topic-notes.md)

Networking & VPC: The labyrinthine world of networking became navigable by understanding the Virtual Private Cloud (VPC). Defining subnets, route tables, and internet gateways suddenly made the internet feel less like magic and more like an organized, secure community.
- [Networking](./networking/topic-notes.md)

Storage & S3: I discovered the power of AWS S3—not just for backing up files, but as a powerful platform for hosting high-performance, static websites, a direct evolution of my initial web design interest.
- [Storage](./storage/topic-notes.md)

Linux & Bash: Mastering Linux and the Bash terminal provided a vital technical lingua franca, empowering me to manage systems directly and automate tasks, moving beyond graphical interfaces into the heart of the machine.
- [Linux](./linux/topic-notes.md)


Databases: I gained an introduction to the landscape of AWS databases, learning that data isn't a one-size-fits-all problem, but that services like RDS (relational) and DynamoDB (NoSQL) each have their perfect use case.
- [Databases](./databases/database-design.md)

Security Services: Crucially, I learned about foundational security, navigating Security Groups, network Subnets, and the multi-layered security model that underpins every cloud deployment. 
- [Security](./security/topic-notes.md)


## Skills, Technologies, and The Lessons Learned

The technical skills acquired are certainly the currency of this industry, but the lessons I found most valuable are centered around how we apply that knowledge in a professional environment.

- Hard Skills & Technologies:

Cloud Fundamentals: AWS Core Services (EC2, VPC, S3, IAM, CloudFront, Route 53, CloudWatch).

System Administration: Linux and Bash scripting.

Networking: Subnetting, CIDR, Security Groups, and NACLs.

Database Management: Introduction to Relational vs. NoSQL (DynamoDB).

Web Services: Static website hosting and CDN implementation.

- Soft Skills & Professional Insight:

Reputation Management (Critical Service Delivery): A fundamental shift in my thinking, similar to how I learned that branding isn’t about a company’s logo or colour scheme. It's more centred around the company’s reputation among its customer base. This highlighted the importance of rendering good and consistent service to stakeholders, taking criticism and feedback in a constructive manner, as well as resolving any issues or complaints quickly before they snowball into a social media trend or worse, a devastating public incident. This insight directly applies to my backend and security aspirations: ensuring the services I build are reliable, responsive, and trustworthy is the ultimate measure of success.

Systematic Problem Solving: Moving from "Is it working?" to "What exactly is failing, and why?" using logs, monitoring, and methodical troubleshooting processes.

Collaboration and Communication: Learning to articulate complex technical challenges clearly to both technical and non-technical peers in a project setting.

## Group Project 1: Static Site with Serverless Backend

My first major collaborative project involved delivering a highly available, performant static website using a serverless approach. This was where theory met practice, and where I truly got to flex my emerging backend muscles.

Our team’s objective was to host a modern, secure website. My primary responsibility focused on the infrastructure delivery:

Static Content Migration: I was tasked with migrating the website’s static assets onto AWS S3, ensuring the bucket was configured correctly for website hosting, complete with appropriate permissions (while adhering to the principle of least privilege, of course).

Performance & Global Delivery: To achieve low-latency delivery, I implemented AWS CloudFront, configuring it to act as the Content Delivery Network (CDN) caching the S3 content globally. This provided crucial performance benefits and enhanced security.

Backend Integration (DynamoDB): My most exciting task was setting up the basic backend infrastructure. We chose DynamoDB as our serverless, NoSQL database to handle simple interactions (like storing customer contact messages or simple product listings). This allowed me to integrate a fully managed database solution, proving the concept of a modern, scalable web architecture that is completely decoupled from traditional, stateful servers.

This project was a revelation, showing me the real-world application of the modules we studied and cementing my passion for building out the reliable, scalable systems that power the digital landscape.

## Conclusion

This document marks just the first milestone in a long and dedicated career in technology. The AWS re/Start program has equipped me not only with invaluable skills like working with VPCs and DynamoDB but, more importantly, with a robust methodology for approaching technical challenges and a deep appreciation for service delivery. The journey from a self-taught designer to a certified Cloud Practitioner is underway, and I am highly motivated to continue down the path of backend engineering and, ultimately, into the vital field of cybersecurity. I’m ready for the next challenge, eager to learn, and excited to build.

LinkedIn Profile: www.linkedin.com/in/kebaabetswe-sennelo-28226130 
Contact Details: ka.sennelo@gmail.com

# My Restart Graduate Journey

This repository is a collection of modules and activities covered in the AWS re/Start program. This collection is set to assist future employers and recruiters gain an understanding of what I’ve learned and the skills set gained throughout the program. It includes sample folders, notes, and lab examples for each major topic: Compute, Storage, Databases, and more.

## Why This Repo?

- Helps me track and document my learning journey in the AWS re/Start program
- It's an exhibit of skills gained in the program
- Serves as a personal knowledge base
- A portfolio to be shared with recruiters