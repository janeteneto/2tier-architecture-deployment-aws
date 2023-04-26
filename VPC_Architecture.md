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

![image](https://user-images.githubusercontent.com/129942042/234410926-f0d59eee-0359-4e18-8a15-406179d0668f.png)

## 1. Create VPC 10.0.0.0/16

1. Search for VPC Dashboard on AWS

2. Press `Create new VPC`

3. Change to the following settings (use your name) and press `Create VPC`:

![2023-04-25 (1)](https://user-images.githubusercontent.com/129942042/234411788-cd9cea33-adf9-4e1f-b0a9-0dff5811c504.png)

## 2. Create Internet Gateway

1. Look for internet gateway on the left menu

2. Press `Create internet gateway`

3. Add a name to it and create

4. Now, to attach to a VPC, press `Actions` on the internet gateway you just created

5. Attach to your VPC

## 3. Create Route Table

1. Search on the left side menu, open Route Tables and press `Create Route Tables`

2. Give it a name and create

3. Select your route table and edit to add a ``0.0.0.0` destination to allow traffic from anywhere

4. Create another route table for your private ip without adding the `0.0.0.0` rule

## 4. Create Subnet

1. Look on left menu for Subnets and press Create Subnet

2. Settings should be as follows, then create subnet:

![2023-04-25 (17)](https://user-images.githubusercontent.com/129942042/234415191-014f0476-5dd0-48e3-9ed6-b60fe2f8a562.png)

3. To connect to route table, select your subnet and press `edit route table association`

4. Select your route table and save it

5. Create a new subnet for your private ip and connect it to the private route table

# App Deployment on VPC

1. Create AMI for app instance and db instance one at a time (there is a separate README file with steps for this)
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

# Autoscalling and Load balancing

![image](https://user-images.githubusercontent.com/129942042/234581170-6ed37d6e-a9d5-4c9d-979b-8f98fcc157fd.png)

## Load Balancer
- Receives internet traffic and sends to instances, when the instance is underperforming or not performing well,  it will stop traffic and divert it another instance
- It distributes traffic between EC2 instances so that no one instance gets overwhelmed
- Load balancers can help ensure that your application stays available and reliable, even if some of your servers or instances fail.
- 
## Autoscalling

- Deletes and terminates the damaged instance and creates a fresh one to replace it, as soon as the application loads balancer says its not performing well
- While balancer will divert traffic, autoscalling will fix the damaged instance
- Instances are diverted from one area to another

**Auto scaling group** - group of EC2 instances that automatically scales up or down based on predefined conditions. Essentially, an Auto Scaling group helps ensure that you have the right amount of compute resources available to handle your workload

**Auto Scaling Policy** - set of rules that determine when and how an Auto Scaling group should add or remove EC2 instances based on changes in demand. It essentially tells the Auto Scaling group what actions to take in response to specific conditions.

- There are many auto scalling polocies, but we eill focus on **target tracking** - it adjusts the number of EC2 instances in an Auto Scaling group to maintain a target value for a specific metric, such as CPU utilisation or network traffic.

- With a target tracking policy, you simply specify a target value for the metric that you want to track, and AWS automatically adjusts the size of your Auto Scaling group to maintain that target value. For example, if you set a target CPU utilization of 50%, and the current utilization is higher than 50%, AWS will automatically launch more EC2 instances to bring CPU utilization back down to the target level. Conversely, if CPU utilisation drops below the target level, AWS will terminate some instances to reduce costs.

- A **target group** is a logical grouping of EC2 instances used to route traffic to the registered targets based on the rules defined by us. The load balancer then knows that the instances require ports 80 or 22 for example

- **Scaling up** involves increasing the number of computing resources to meet demand, while **scaling down** involves decreasing the number of resources to match decreased demand.


# Steps:
1. Launch template with required info
2. Set Autoscalling Policy (ASG) - Target tracking policy - 50% or above CPU utilisation
3. Create target group with required ports access
4. Set Load Balancer - Application Load Balancer (ALB)

