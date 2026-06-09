<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** irahimsindhu@gmail.com  
**Email:** irahimsindhu@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create a private, isolated network in AWS where you can launch and manage resources like EC2 instances.

It is useful because it gives you control over networking, including IP addresses, subnets, route tables, and security, allowing you to securely organize and isolate your cloud infrastructure.

### How I used Amazon VPC in this project

I used Amazon VPC to create and configure public and private subnets, route tables, internet gateways and security groups.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the absolute simplicity and straight-forward guidance.

### This project took me...

This project took me around 30 minutes to complete

---

## Setting Up Direct VM Access

Directly accessing an EC2 instance means logging into the virtual server itself (using SSH for Linux or RDP for Windows) so you can manage its operating system, files, and software.

### SSH is a key method for directly accessing a VM

SSH traffic means "Secure Shell" and it is a way that developers can use to directly log in to a remote computer from their machines.

### To enable direct access, I set up key pairs

Key pairs are a pair of public and private keys that provide secure access to your EC2 instance. The public key is stored on the EC2 instance, while the private key is kept securely by the user. When the user attempts to connect to the instance, they prove possession of the private key through a cryptographic authentication process. The instance verifies this using the stored public key, and access is granted only if the keys match.

A private key's file format means "Privacy-Enhanced Mail" which is a text-based file format used to store cryptographic keys and certificates, such as an EC2 private key
My private key's file format was ".pem".

---

## Launching a public server

I had to change my EC2 instance's networking settings by modifying its associated security groups, subnet, route table, and network ACL settings within the VPC to allow the required inbound and outbound traffic.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because the private server needs stricter access control, it is not exposed to the internet, while the public server allows internet traffic, so they use different security groups to apply different security rules.

My private server's security group's source is the security group of my public server so that only traffic coming from the public server is allowed, keeping the private server inaccessible from the internet while still enabling internal communication between them.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I used a resource map to help me in mapping my VPC with public and private subnets, route tables and the internet gateways.

A VPC resource map is a visual diagram that shows all your AWS resources within a VPC and how they are connected to each other.

My new VPC has a CIDR block of 10.0.0.0/16. It is possible for it to have the same IPv4 CIDR block as an existing VPC because VPCs are logically isolated from each other in AWS, so overlapping CIDR ranges do not conflict unless the VPCs are connected through peering or other networking setups.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 0 or 2. This was because I created a subnet in each Availability Zone for high availability, and each public subnet is tied to a specific AZ, so the template or lab required either not creating any public subnets or creating one per AZ (two AZs = two public subnets).

A NAT Gateway is an AWS service that allows instances in a private subnet to access the internet for outbound traffic, while still preventing the internet from initiating connections to them.
It is used so private servers can:
- Download updates
- Access external APIs
- Install packages
but remain not publicly accessible.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-ec2_8ee57662)

---

---
