## DR - Disaster Recovery Plan
 - A Disaster Recovery (DR) plan on AWS refers to the set of procedures and processes that an organization has in place to recover its critical IT infrastructure and operations in the event of a major disruptive event, such as a natural disaster, cyber-attack, or human error.

## What is it used for?
- A DR plan is used to ensure business continuity and minimize downtime in the event of a disaster or outage. It helps organizations to recover their critical IT systems and applications quickly and efficiently, and resume normal operations as soon as possible. This is important to maintain the availability, integrity, and confidentiality of data, as well as to meet regulatory compliance requirements.

## What are its benefits?
- Minimizes downtime
- Reduces Data Loss
- Increases customer confidence

## S3
- **Amazon Simple Storage Service (S3)** is a cloud-based object storage service provided by AWS. 
- It is designed for storing and retrieving any amount of data, at any time and from anywhere on the web.
-  S3 is a highly scalable and durable storage solution, making it ideal for businesses of all sizes, from small startups to large enterprises.
-
- **AWS CLI (Command Line Interface)** is a unified tool provided by AWS to manage various AWS services from the command line. It allows you to interact with AWS services using commands in your command-line shell.

- **AWS SDK (Software Development Kit)** is a collection of software tools and libraries that allow developers to build applications that integrate with various AWS services. The SDK provides APIs (Application Programming Interfaces) for popular programming languages such as Java, Python, .NET, and more, making it easier to develop AWS applications.

-
# Amazon S3 Setup

- So far, we have used the `tech221.pem` file to ssh into ubuntu, now we will access it with aws access and secret keys to get access to S3:

1. Create instance with SSH rule on port 22
2. SSH into the instance using Git terminal
3. `sudo apt update -y` `sudo apt upgrade -y`
4. `sudo apt install python3-pip -y`
5. `sudo python3 -m pip install awscli`
6. Run `aws configure`
7. Insert access ID
8. Insert secret key
9. Insert `eu-west-1`
10. Insert `json`
11. Run `aws s3 ls` to list everything available on s3
13. Create a bucket/folder:
14. Run `aws s3 mb s3://janete-tech221` to make a bucket with the name `janete-tech221` and if we do `aws s3 ls` we can check if the bucket is there
15. `sudo nano test.txt` to create file
16. `aws s3 cp test.txt s3://janete-tech221` - to copy file to your bucket in aws s3
17. `aws s3 cp s3://janete-tech221/test.txt /home/ubuntu` to copy/download file from bucket to ec2 instance
18. `aws s3 rm s3://janete-tech221/test.txt` deletes item inside the bucket
19. `aws s3 rb s3://janete-tech221` to remove the bucket
20. We can't delete a bucket if it has files inside it


- S3 Storage is cost-effective
- S3 storage classes:
- 

16. Upload/download data
17. 
18. 
**CRUD** - Create, Read, Update, Delete

we need an aws config file and store the keys
