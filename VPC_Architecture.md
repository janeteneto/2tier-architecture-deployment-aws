# What is a VPC?

- isolated place provided by the public cloud provider 
- VPC stands for Virtual Private Cloud
- Secure, isolated private cloud hosted within a public cloud
- Run code, store data, host websites, etc but the private cloud is hosted remotely by a public cloud provider.

# What are the benefits?

- Agility - the resources can be scaled dynamically in real-time.
- Security - users data and space don’t mix with a cloud provider’s other customers
- Easy to deploy- it’s relatively easy to connect a VPC to a public cloud

# What is Internet Gateway

- An Internet Gateway is a network component that allows communication between a private network, such as a Virtual Private Cloud (VPC) in the cloud, and the public internet.
In simpler terms, an Internet Gateway is like a **doorway that connects your private network to the internet, allowing traffic to flow in and out of your network**.

# What is a subnet?

-  a subnet is like a smaller network within a larger network. It enables you to divide a larger network into smaller, more manageable segments, which can improve network performance and security.
- defined by an IP address range, and each device or instance within a subnet is assigned a unique IP address.
- subnet can have a security groups to protect multiple instances

# CIDR Blocks

- It's basically a set of IP addresses is similar to a post-code
- stands for Classless Inter-Domain Routing
- CIDR block is a way of representing a range of IP addresses that can be used to define the address space for a network or subnet
- CIDR block is a set of IP addresses that have been grouped together for the purpose of network management

# Route Tables

-Route tables are a set of rules or policies that determine how network traffic is directed or routed within a network or subnet. Each rule specifies a destination IP address or range of addresses, and the next hop to which the traffic should be forwarded.
- A route table is like a map that tells network traffic where to go. It includes a list of IP address ranges and the network interfaces or gateways that should be used to reach those ranges.

# AWS VPC Steps:

1. Create VPC 10.0.0.0/16
2. Internet gateway 2.1: attach the IG to VPC
3. Create a public subnet 10.0.4.0/24 - connection to VPC
4. Create route table - associate it w public subnet as well as attach to IG

# App Deployment on VPC

1. Create AMI for app instance and db instance one at a time (there is a separate README file with steps for this).
2. Create instance for app and db image
3. Connect app instance through ssh as usual
4. Create new private subnet
5. Create a CIDR block
6. Create route table
7. Associate route with your own vpc
8. Edit subnet and tick private
9. Go to the terminal and run `sudo nano .bashrc`, then change the ip do the db private ip address of your instance
10. Run `source .bashrc`
11. Start the app as usual
12. Seed the database and open posts page 
