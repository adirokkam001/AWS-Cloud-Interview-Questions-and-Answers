# ☁️ AWS Cloud Interview Questions and Answers

## 📚 Complete AWS / Cloud / EC2 / VPC / S3 / EBS / ELB Interview Notes

This README contains detailed interview-oriented questions and answers covering **AWS fundamentals, EC2, EBS, S3, AMI, Snapshots, VPC, Subnets, Internet Gateway, NAT Gateway, Security Groups, NACL, VPC Peering, Route Tables, Elastic IP, Load Balancing, Linux, Windows Server, Apache, IIS, networking, CIDR, and AWS limits**.

Each topic is explained with:

* **Definition**
* **Purpose / Use**
* **Example**
* **Important Interview Points**
* **Commands or Steps where applicable**

---

# 📑 Table of Contents

1. [Availability Zone vs Region](#1-what-is-the-difference-between-availability-zone-and-region)
2. [EIP vs Public IP](#2-what-is-the-difference-between-eip-and-public-ip)
3. [EBS vs S3](#3-what-is-the-difference-between-ebs-and-s3)
4. [AMI vs Snapshot](#4-what-is-the-difference-between-ami-and-snapshot)
5. [Security Group](#5-what-is-security-group)
6. [AMI](#6-what-is-ami)
7. [Snapshot](#7-what-is-snapshot)
8. [Elastic IP](#8-what-is-eip)
9. [ELB and Types](#9-whats-is-elb-and-its-types)
10. [Change EC2 Instance Type](#10-how-to-change-instance-type)
11. [S3 and Storage Classes](#11-whats-is-s3-and-its-types)
12. [VPC](#12-what-is-vpc)
13. [Subnet](#13-what-is-subnet)
14. [Internet Gateway](#14-what-is-igw)
15. [NAT Gateway](#15-what-is-nat-gateway)
16. [NACL](#16-what-is-nacl)
17. [VPC Peering](#17-what-is-vpc-peering)
18. [Route Table](#18-what-is-route-table)
19. [Public Subnet](#19-what-is-public-subnet)
20. [Private Subnet](#20-what-is-private-subnet)
21. [Public vs Private Subnet](#21-difference-between-public-subnet-and-private-subnet)
22. [Security Group vs NACL](#22-difference-between-sg-and-nacl)
23. [Common Port Numbers](#23-rdp-dns-ssh-http-https-port-numbers)
24. [Create an AMI](#24-how-to-take-ami-of-the-server)
25. [Create Linux User](#25-how-to-create-a-user-in-linux-box)
26. [Create Windows User](#26-how-to-create-a-user-in-windows-server)
27. [Key Pair](#27-what-is-a-key-pair)
28. [Apache vs IIS](#28-what-is-the-difference-between-apache-and-iis)
29. [IIS Port](#29-what-is-port-number-of-iis)
30. [Apache Port](#30-what-is-the-port-number-of-apache)
31. [Run Apache on Custom Port](#31-how-to-run-apache-server-on-custom-port-number)
32. [Create EBS Volume](#32-how-to-create-ebs-volume-of-a-server)
33. [Make Subnet Public](#33-how-to-make-a-subnet-public)
34. [Make Subnet Private](#34-how-to-make-a-subnet-private)
35. [Communication Between Two VPCs](#35-how-to-communicate-a-server-in-vpc1-to-a-server-in-vpc2)
36. [Ping](#36-what-is-ping)
37. [Telnet](#37-what-is-telnet)
38. [Check IP Address](#38-command-to-check-ip-address-of-a-server)
39. [Create Linux User Command](#39-command-to-create-a-user-in-linux-box)
40. [Change Linux Password](#40-how-to-change-the-password-of-a-user-in-linux)
41. [Apache Installation Path](#41-apache-default-installation-path)
42. [IIS Installation Path](#42-iis-default-installation-path)
43. [Install Apache](#43-command-to-install-apache-in-linux)
44. [Install IIS](#44-how-to-install-iis-in-windows)
45. [ELB Listener](#45-what-is-a-listener-in-elb)
46. [Target Group](#46-what-is-target-group-in-elb)
47. [ALB vs NLB](#47-alb-vs-nlb)
48. [Reduce EBS Volume](#48-is-it-possible-to-reduce-ebs-volume)
49. [CIDR](#49-what-is-a-cidr)
50. [Tags](#50-what-is-the-use-of-tags)
51. [Elastic IP Default Quota](#51-by-default-how-many-elastics-ip-aws-offers)
52. [S3 Bucket Limit](#52-how-many-buckets-we-can-create-per-region)
53. [S3 Object Size](#53-what-is-the-size-of-object-which-we-can-upload-to-s3-bucket)
54. [EBS Volume Size](#54-ebs-volume-size-limit)
55. [AWS](#55-what-is-aws)
56. [Cloud Computing](#56-what-is-cloud-computing)
57. [Access AWS Platform](#57-how-to-access-aws-platform)
58. [EC2](#58-what-is-ec2)
59. [Attach EBS to Multiple Instances](#59-how-to-add-ebs-volume-to-multiple-instances)

---

# 1. What is the difference between Availability Zone and Region?

## Definition

### Region

An **AWS Region** is a geographical area where AWS has multiple isolated data centers called Availability Zones.

Examples:

```text
ap-south-1  → Mumbai Region
ap-south-2  → Hyderabad Region
us-east-1   → N. Virginia Region
```

### Availability Zone

An **Availability Zone (AZ)** is one or more isolated data centers within an AWS Region.

For example:

```text
Mumbai Region
     |
     |--- ap-south-1a
     |--- ap-south-1b
     |--- ap-south-1c
```

## Example

Suppose your application is deployed in:

```text
Region: ap-south-1

AZ-1: ap-south-1a
AZ-2: ap-south-1b
```

If one AZ has a problem, your application can continue operating from another AZ if you have designed it for high availability.

## Difference

| Region                           | Availability Zone                                   |
| -------------------------------- | --------------------------------------------------- |
| Geographical location            | Isolated location/data center group within a Region |
| Contains multiple AZs            | Belongs to one Region                               |
| Used for geographical deployment | Used for high availability                          |
| Example: Mumbai                  | Example: ap-south-1a                                |

## Interview Answer

> A Region is a geographical AWS location containing multiple Availability Zones, while an Availability Zone is an isolated location within a Region. We use multiple AZs to improve availability and fault tolerance.

---

# 2. What is the difference between EIP and Public IP?

## Public IP

A public IP address allows an AWS resource such as an EC2 instance to communicate with the internet.

A normal public IPv4 address can change when the instance is stopped and started.

## Elastic IP

An **Elastic IP (EIP)** is a static public IPv4 address allocated to your AWS account.

It remains allocated to your account until you release it.

## Example

Suppose your EC2 server has:

```text
Public IP:
13.234.x.x
```

If the instance is stopped and started, its public IP may change.

If you use an Elastic IP:

```text
Elastic IP:
13.235.x.x
```

You can keep the same address while associating it with the appropriate resource.

## Difference

| Public IP                                  | Elastic IP                                        |
| ------------------------------------------ | ------------------------------------------------- |
| Public IPv4 address                        | Static public IPv4 address                        |
| Can change after stop/start                | Remains allocated until released                  |
| Automatically assigned when applicable     | Explicitly allocated                              |
| Suitable for temporary public connectivity | Useful when a persistent IPv4 address is required |

## Interview Answer

> A public IP is generally an automatically assigned public IPv4 address and may change after a stop/start. An Elastic IP is a static public IPv4 address allocated to the AWS account that can be associated with a resource.

---

# 3. What is the difference between EBS and S3?

## EBS

**EBS = Elastic Block Store**

EBS provides persistent block storage primarily for EC2 instances.

It behaves similarly to a hard disk or SSD attached to a server.

## S3

**S3 = Simple Storage Service**

S3 is an object storage service used to store files and objects.

## Example

For an EC2 server:

```text
EC2
 |
 └── EBS
      |
      ├── Operating System
      ├── Applications
      └── Database files
```

For file storage:

```text
S3 Bucket
 |
 ├── images
 ├── videos
 ├── backups
 └── documents
```

## Difference

| EBS                              | S3                                        |
| -------------------------------- | ----------------------------------------- |
| Block storage                    | Object storage                            |
| Mainly used with EC2             | Independent storage service               |
| Behaves like a disk              | Stores objects/files                      |
| Suitable for OS and applications | Suitable for backups, media and documents |
| Attached to EC2                  | Accessed through APIs/SDKs/console        |

## Interview Answer

> EBS is block-level storage designed primarily for EC2 workloads, whereas S3 is object storage designed to store and retrieve objects such as files, images, backups, and logs.

---

# 4. What is the difference between AMI and Snapshot?

## AMI

**AMI = Amazon Machine Image**

An AMI is a template used to launch EC2 instances.

It contains information required to create an EC2 instance, including the root volume configuration.

## Snapshot

A snapshot is a point-in-time backup of an EBS volume.

## Relationship

```text
EC2
 |
 EBS
 |
 Snapshot
```

An AMI can reference EBS snapshots as part of its storage configuration.

## Example

Suppose you have configured an EC2 server:

```text
Amazon Linux
Apache
Application
Configuration
```

You create an AMI:

```text
Existing EC2
     |
   Create AMI
     |
     AMI
     |
Launch New EC2
```

The new EC2 can be launched using the same configuration represented by the AMI.

## Difference

| AMI                                            | Snapshot                                |
| ---------------------------------------------- | --------------------------------------- |
| EC2 launch template/image                      | EBS volume backup                       |
| Used to launch EC2 instances                   | Used to back up/restore EBS data        |
| Can contain information about multiple volumes | Represents a point-in-time volume state |
| Used for server replication                    | Used for storage backup                 |

## Interview Answer

> A snapshot is a point-in-time backup of an EBS volume, while an AMI is a template used to launch EC2 instances.

---

# 5. What is Security Group?

A **Security Group** is a virtual firewall that controls network traffic for resources such as EC2 instances.

It controls:

* Inbound traffic
* Outbound traffic

## Example

Suppose you have a Linux web server.

You can configure:

```text
SSH
TCP
22
Source: My IP

HTTP
TCP
80
Source: 0.0.0.0/0

HTTPS
TCP
443
Source: 0.0.0.0/0
```

This means:

```text
Internet
   |
   |---- TCP 80 ----> EC2
   |
   |---- TCP 443 ---> EC2

Your IP
   |
   |---- TCP 22 ----> EC2
```

## Important Characteristics

Security Groups are:

* **Stateful**
* Associated with network interfaces/resources
* Allow rules only
* Used for controlling traffic at the resource/network-interface level

## Interview Answer

> A Security Group is a stateful virtual firewall for AWS resources such as EC2. It controls inbound and outbound traffic using allow rules.

---

# 6. What is AMI?

**AMI = Amazon Machine Image**

An AMI is a template used to launch EC2 instances.

It can contain:

* Operating system
* Installed software
* Application configuration
* Storage configuration
* Launch configuration information

## Example

Suppose you configure:

```text
Amazon Linux
Apache
Python
Application
Configuration
```

You create an AMI from that server.

Now you can launch multiple servers:

```text
             AMI
              |
       +------+------+
       |      |      |
      EC2    EC2    EC2
```

All instances can start from the same base image.

## Uses

AMI is useful for:

* Creating identical servers
* Server backup/template creation
* Auto Scaling
* Application deployment
* Disaster recovery
* Creating custom server images

## Interview Answer

> An AMI is a template containing the information needed to launch an EC2 instance.

---

# 7. What is Snapshot?

A **snapshot** is a point-in-time backup of an EBS volume.

## Example

```text
EBS Volume
    |
    | Create Snapshot
    ↓
Snapshot
```

If the original EBS volume has a problem, the snapshot can be used to create another EBS volume.

## Uses

Snapshots are commonly used for:

* Backup
* Disaster recovery
* Data migration
* Creating new EBS volumes
* Supporting AMI creation

## Example

```text
Original EBS
     |
   Snapshot
     |
New EBS Volume
```

## Interview Answer

> An EBS snapshot is a point-in-time backup of an EBS volume that can be used to restore or create another volume.

---

# 8. What is EIP?

**EIP = Elastic IP**

An Elastic IP is a static public IPv4 address allocated to an AWS account.

## Example

```text
EC2
 |
Elastic IP
 |
Internet
```

If you need a fixed public IPv4 address for a server, an EIP can be used.

## Example Scenario

Suppose a client has configured DNS or firewall rules for:

```text
13.235.x.x
```

If the server changes but you retain the Elastic IP, you can associate the EIP with the replacement resource.

## Important Point

Unused Elastic IPs can incur charges under current AWS pricing, so release EIPs that you no longer need.

## Interview Answer

> An Elastic IP is a static public IPv4 address that you can allocate to your AWS account and associate with supported resources.

---

# 9. What is ELB and its types?

**ELB = Elastic Load Balancing**

ELB distributes incoming traffic across multiple targets.

Example:

```text
              Users
                |
                ↓
              ELB
           /    |    \
          ↓     ↓     ↓
        EC2   EC2   EC2
```

## Why do we use ELB?

ELB is used for:

* High availability
* Traffic distribution
* Health checking
* Scalability
* Removing unhealthy targets from traffic

## Types of ELB

### 1. Application Load Balancer — ALB

ALB works at **Layer 7**.

It supports HTTP and HTTPS traffic.

It supports features such as:

* Host-based routing
* Path-based routing
* HTTP headers
* Web application routing

Example:

```text
example.com/api
       ↓
API Target Group

example.com/images
       ↓
Image Target Group
```

---

### 2. Network Load Balancer — NLB

NLB operates primarily at **Layer 4**.

It supports:

* TCP
* UDP
* TLS

It is designed for high-performance network traffic and low latency.

---

### 3. Gateway Load Balancer — GWLB

GWLB is designed for deploying and scaling network/security appliances such as firewalls and inspection systems.

---

### 4. Classic Load Balancer — CLB

Classic Load Balancer is the older generation of Elastic Load Balancing.

For new architectures, AWS generally recommends using the newer load balancer types based on workload requirements.

## Interview Answer

> Elastic Load Balancing distributes incoming traffic across multiple targets and improves availability and scalability. The major current types are ALB, NLB, and GWLB, while Classic Load Balancer is the older generation.

---

# 10. How to Change Instance Type?

You can change the EC2 instance type when the workload requires different CPU, memory, networking, or other instance capabilities.

## Steps

1. Open AWS Console.
2. Go to **EC2**.
3. Select the instance.
4. Stop the instance.
5. Choose:

```text
Actions
→ Instance settings
→ Change instance type
```

6. Select the new instance type.
7. Apply the change.
8. Start the instance.

## Example

```text
t3.micro
    ↓
t3.small
```

The new instance type must be supported for your AMI architecture and configuration.

## Interview Answer

> To change an EC2 instance type, I normally stop the instance, choose Change Instance Type, select the required type, apply the change, and start the instance again.

---

# 11. What is S3 and its Types?

**S3 = Simple Storage Service**

S3 is an AWS object storage service.

It is used to store:

* Images
* Videos
* Documents
* Backups
* Logs
* Static website files
* Application data

## Basic S3 Structure

```text
S3
 |
 Bucket
 |
 Objects
```

Example:

```text
my-company-bucket
 |
 ├── images/
 │    ├── logo.png
 │    └── product.jpg
 |
 ├── documents/
 │    └── report.pdf
 |
 └── backups/
      └── backup.zip
```

## S3 Storage Classes

S3 provides different storage classes for different access patterns.

### S3 Standard

Designed for frequently accessed data.

### S3 Intelligent-Tiering

Automatically moves objects between access tiers based on access patterns.

### S3 Standard-IA

Designed for infrequently accessed data that still requires rapid access.

### S3 One Zone-IA

Infrequently accessed data stored in a single Availability Zone.

### S3 Glacier Instant Retrieval

Archive storage where millisecond access is required.

### S3 Glacier Flexible Retrieval

Archive storage for data that does not need immediate access.

### S3 Glacier Deep Archive

Designed for long-term archival and very infrequent access.

## Interview Point

Technically, these are called **S3 storage classes**, not simply "S3 types."

---

# 12. What is VPC?

**VPC = Virtual Private Cloud**

A VPC is a logically isolated virtual network in AWS.

You control important networking components such as:

* IP address range
* Subnets
* Route tables
* Internet Gateway
* NAT Gateway
* Security Groups
* Network ACLs

## Example

```text
VPC
10.0.0.0/16
 |
 +----------------------+
 |                      |
Public Subnet        Private Subnet
10.0.1.0/24          10.0.2.0/24
 |                      |
EC2/ALB               Database
```

## Use

VPC allows you to design the network architecture of your AWS environment.

## Interview Answer

> A VPC is a logically isolated virtual network in AWS where we deploy and control resources such as EC2 instances, subnets, route tables, and network security components.

---

# 13. What is Subnet?

A **subnet** is a smaller IP network created inside a VPC.

## Example

VPC:

```text
10.0.0.0/16
```

Subnets:

```text
10.0.1.0/24
10.0.2.0/24
10.0.3.0/24
```

## Why use subnets?

Subnets allow you to:

* Organize resources
* Separate application layers
* Control routing
* Build public/private network architecture
* Improve network security

## Example

```text
VPC
 |
 +--- Public Subnet
 |       |
 |      ALB
 |
 +--- Private Subnet
         |
        EC2
```

---

# 14. What is IGW?

**IGW = Internet Gateway**

An Internet Gateway is a VPC component that enables communication between resources in a VPC and the internet when the routing and addressing configuration permits it.

## Example

```text
Internet
    |
    ↓
Internet Gateway
    |
    ↓
Public Subnet
    |
    ↓
EC2
```

## Requirements for Internet Connectivity

For a resource such as an EC2 instance to communicate with the internet through an IGW, the architecture generally requires:

1. VPC
2. Internet Gateway attached to the VPC
3. Public subnet route table
4. Route:

```text
0.0.0.0/0 → Internet Gateway
```

5. Appropriate public IPv4 address
6. Appropriate Security Group/NACL rules

## Interview Answer

> An Internet Gateway is a VPC component that provides a path between a VPC and the internet for appropriately configured public resources.

---

# 15. What is NAT Gateway?

**NAT = Network Address Translation**

A NAT Gateway allows resources in a private subnet to initiate outbound connections to the internet without giving those private resources public IP addresses.

## Architecture

```text
Private EC2
    |
    ↓
NAT Gateway
    |
    ↓
Internet Gateway
    |
    ↓
Internet
```

## Example

Suppose a private EC2 server needs to download Linux package updates.

The EC2 doesn't need a public IP.

It sends the request through:

```text
Private EC2
     ↓
NAT Gateway
     ↓
IGW
     ↓
Internet
```

## Important Point

NAT Gateway is primarily used for **outbound internet connectivity from private subnets**.

It is not a mechanism for allowing arbitrary unsolicited inbound internet connections to the private instance.

---

# 16. What is NACL?

**NACL = Network Access Control List**

A NACL is a network-level firewall associated with a subnet.

It controls:

* Inbound traffic
* Outbound traffic

## Characteristics

NACLs are:

* Stateless
* Associated with subnets
* Support allow rules
* Support deny rules
* Rules are evaluated in rule-number order

## Example

```text
Internet
   |
   ↓
NACL
   |
   ↓
Subnet
   |
   ↓
EC2
```

## Interview Answer

> A Network ACL is a stateless subnet-level firewall that controls inbound and outbound traffic using both allow and deny rules.

---

# 17. What is VPC Peering?

**VPC Peering** allows two VPCs to communicate using private IP addresses.

## Example

```text
VPC-A
10.0.0.0/16
      |
      |
 VPC Peering
      |
      |
VPC-B
10.1.0.0/16
```

## Steps

### Step 1 — Create VPC Peering

Create a peering connection between VPC-A and VPC-B.

### Step 2 — Accept the request

The other VPC owner/account accepts the peering request when required.

### Step 3 — Add routes

VPC-A route table:

```text
Destination: 10.1.0.0/16
Target: VPC Peering Connection
```

VPC-B route table:

```text
Destination: 10.0.0.0/16
Target: VPC Peering Connection
```

### Step 4 — Configure Security Groups

Allow the required traffic.

### Step 5 — Configure NACLs

Ensure the NACLs permit the traffic.

## Important Point

The VPC CIDR ranges must not overlap for standard VPC peering.

---

# 18. What is Route Table?

A route table contains routing rules that determine where network traffic should be sent.

## Example

```text
Destination       Target
--------------------------------
10.0.0.0/16       local
0.0.0.0/0         igw-xxxx
```

This means:

```text
VPC traffic
   ↓
local

Internet traffic
   ↓
Internet Gateway
```

## Example Private Route Table

```text
Destination       Target
--------------------------------
10.0.0.0/16       local
0.0.0.0/0         NAT Gateway
```

## Interview Answer

> A route table controls where traffic from a subnet is routed by defining destination CIDRs and their targets.

---

# 19. What is Public Subnet?

A subnet is considered **public** when its route table contains a route to an Internet Gateway.

Example:

```text
Destination:
0.0.0.0/0

Target:
Internet Gateway
```

## Example

```text
Internet
   |
   ↓
IGW
   |
   ↓
Public Subnet
   |
   ↓
Load Balancer
```

## Important Point

A subnet having an IGW route does not automatically make every resource publicly accessible.

The resource also needs appropriate addressing and security configuration.

---

# 20. What is Private Subnet?

A private subnet does not have a direct route to an Internet Gateway for direct public internet access.

It can use a NAT Gateway for outbound internet access.

## Example

```text
Private EC2
    |
    ↓
NAT Gateway
    |
    ↓
Internet Gateway
    |
    ↓
Internet
```

## Common Use

Private subnets are commonly used for:

* Application servers
* Databases
* Internal services
* Backend systems

---

# 21. Difference Between Public Subnet and Private Subnet

| Public Subnet                                                  | Private Subnet                                 |
| -------------------------------------------------------------- | ---------------------------------------------- |
| Has route to Internet Gateway                                  | Does not have direct route to Internet Gateway |
| Used for public-facing resources                               | Used for internal resources                    |
| Can contain resources with public IPs                          | Resources generally use private IPs            |
| Commonly used for ALB/public services                          | Commonly used for backend/database workloads   |
| Can have direct internet connectivity when properly configured | Outbound internet can use NAT Gateway          |

## Example

```text
Internet
   |
   ↓
IGW
   |
Public Subnet
   |
   ↓
ALB
   |
   ↓
Private Subnet
   |
   ↓
Application/Database
```

---

# 22. Difference Between Security Group and NACL

| Security Group                          | NACL                                      |
| --------------------------------------- | ----------------------------------------- |
| Stateful                                | Stateless                                 |
| Resource/network-interface level        | Subnet level                              |
| Allow rules only                        | Allow and deny rules                      |
| Return traffic automatically allowed    | Return traffic must be explicitly allowed |
| Applied to resources/interfaces         | Applied to subnets                        |
| Commonly used for instance-level access | Used for subnet-level network control     |

## Simple Memory Trick

```text
Security Group
↓
Stateful
Resource level
Allow only

NACL
↓
Stateless
Subnet level
Allow + Deny
```

## Example

Security Group:

```text
Allow TCP 22
Allow TCP 80
```

NACL:

```text
Rule 100 → Allow TCP 80
Rule 110 → Deny TCP 23
```

---

# 23. RDP, DNS, SSH, HTTP, HTTPS Port Numbers

| Protocol | Port | Common Transport |
| -------- | ---: | ---------------- |
| SSH      |   22 | TCP              |
| DNS      |   53 | UDP/TCP          |
| HTTP     |   80 | TCP              |
| HTTPS    |  443 | TCP              |
| RDP      | 3389 | TCP/UDP          |

## SSH

Used to remotely administer Linux servers.

```text
Port: 22
```

## RDP

Used for remote desktop access to Windows systems.

```text
Port: 3389
```

## HTTP

Used for normal web traffic.

```text
Port: 80
```

## HTTPS

Encrypted HTTP using TLS.

```text
Port: 443
```

## DNS

Used for domain name resolution.

```text
Port: 53
```

DNS commonly uses UDP, while TCP is also used for certain operations.

---

# 24. How to Take AMI of the Server?

For an EC2 instance:

## Steps

1. Open AWS Console.
2. Go to **EC2**.
3. Select the EC2 instance.
4. Choose:

```text
Actions
→ Image and templates
→ Create image
```

5. Enter an AMI name.
6. Review storage configuration.
7. Create the image.

AWS creates the AMI and the associated EBS snapshots required by the image.

## Architecture

```text
Existing EC2
     |
     ↓
Create AMI
     |
     ↓
AMI
     |
     ↓
Launch New EC2
```

## Use

AMI creation is useful when you need to:

* Replicate a server
* Create identical EC2 instances
* Create a deployment template
* Support Auto Scaling
* Create a server recovery image

---

# 25. How to Create a User in Linux Box?

Use:

```bash
sudo useradd username
```

For a home directory:

```bash
sudo useradd -m username
```

For Bash shell:

```bash
sudo useradd -m -s /bin/bash username
```

Then set a password:

```bash
sudo passwd username
```

## Example

```bash
sudo useradd -m -s /bin/bash adi
sudo passwd adi
```

## Verify

```bash
id adi
```

or:

```bash
getent passwd adi
```

---

# 26. How to Create a User in Windows Server?

You can create a local Windows user through the GUI.

## GUI Method

```text
Server Manager
      ↓
Tools
      ↓
Computer Management
      ↓
Local Users and Groups
      ↓
Users
      ↓
New User
```

Enter:

* Username
* Password
* Password options

## PowerShell Method

Run PowerShell as Administrator:

```powershell
New-LocalUser -Name "adi"
```

You can then add the user to the appropriate local group.

For example:

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "adi"
```

Only grant administrative privileges when required.

---

# 27. What is a Key Pair?

An AWS key pair is a combination of:

```text
Public Key
+
Private Key
```

It is commonly used for secure authentication to EC2 instances.

## Linux EC2 Example

When launching an EC2 instance, you select a key pair.

You receive/download the private key, commonly:

```text
my-key.pem
```

Then connect:

```bash
ssh -i my-key.pem ec2-user@<public-ip>
```

## Concept

```text
AWS
 |
Public Key
 |
EC2

Your Computer
 |
Private Key
 |
SSH
```

## Important

Never share your private key.

The private key should be stored securely.

---

# 28. What is the Difference Between Apache and IIS?

## Apache

Apache HTTP Server is an open-source web server commonly used on Linux and also available on other operating systems.

## IIS

**IIS = Internet Information Services**

IIS is Microsoft's web server and is commonly used on Windows Server.

## Difference

| Apache                           | IIS                                              |
| -------------------------------- | ------------------------------------------------ |
| Open-source                      | Microsoft web server                             |
| Common on Linux                  | Common on Windows Server                         |
| Configuration uses files         | Strong integration with Windows management tools |
| Supports many application stacks | Strong integration with ASP.NET/.NET             |
| Cross-platform                   | Windows-focused                                  |

## Example

```text
Linux Server
    ↓
Apache
    ↓
Website
```

```text
Windows Server
    ↓
IIS
    ↓
Website
```

---

# 29. What is Port Number of IIS?

The default IIS ports are:

```text
HTTP  → 80
HTTPS → 443
```

Example:

```text
http://server-ip
```

uses port 80 by default.

```text
https://server-ip
```

uses port 443 by default.

---

# 30. What is the Port Number of Apache?

Apache commonly uses:

```text
HTTP  → 80
HTTPS → 443
```

Example:

```text
http://server-ip
```

uses port 80.

You can configure Apache to listen on another port.

Example:

```text
8080
```

---

# 31. How to Run Apache Server on Custom Port Number?

Suppose you want Apache to listen on:

```text
8080
```

## Step 1 — Edit Apache configuration

On RHEL/Amazon Linux, configure:

```apache
Listen 8080
```

For example, Apache's main configuration is commonly:

```text
/etc/httpd/conf/httpd.conf
```

## Step 2 — Configure VirtualHost

Example:

```apache
<VirtualHost *:8080>
    DocumentRoot /var/www/html
</VirtualHost>
```

## Step 3 — Restart Apache

Amazon Linux/RHEL:

```bash
sudo systemctl restart httpd
```

Ubuntu/Debian:

```bash
sudo systemctl restart apache2
```

## Step 4 — Allow the port in AWS Security Group

Add:

```text
Type: Custom TCP
Port: 8080
Source: Appropriate CIDR
```

## Step 5 — Test

```text
http://<server-ip>:8080
```

---

# 32. How to Create EBS Volume of a Server?

## Step 1

Open:

```text
AWS Console
→ EC2
→ Volumes
```

## Step 2

Choose:

```text
Create volume
```

## Step 3

Select:

* Volume type
* Size
* Availability Zone

Example:

```text
Volume type: gp3
Size: 20 GiB
AZ: ap-south-1a
```

## Important

The EBS volume must be created in the same Availability Zone as the EC2 instance for normal attachment.

## Step 4

Create the volume.

## Step 5

Select volume:

```text
Actions
→ Attach volume
```

## Step 6

Select EC2 instance.

## Linux Example

Check the disk:

```bash
lsblk
```

Create filesystem:

```bash
sudo mkfs -t xfs /dev/nvme1n1
```

Create mount point:

```bash
sudo mkdir /data
```

Mount:

```bash
sudo mount /dev/nvme1n1 /data
```

Verify:

```bash
df -h
```

---

# 33. How to Make a Subnet Public?

A subnet becomes public when its route table contains a route to an Internet Gateway.

## Steps

### Step 1

Create or use an Internet Gateway.

```text
VPC
 |
Internet Gateway
```

### Step 2

Attach the Internet Gateway to the VPC.

### Step 3

Create/select a route table.

Add:

```text
Destination:
0.0.0.0/0

Target:
Internet Gateway
```

### Step 4

Associate the route table with the subnet.

### Step 5

For a resource to be directly reachable from the internet, configure appropriate public addressing.

For example, an EC2 instance may need a public IPv4 address.

### Step 6

Configure Security Group and NACL rules.

## Architecture

```text
Internet
    |
    ↓
IGW
    |
    ↓
Route Table
    |
    ↓
Public Subnet
    |
    ↓
EC2
```

---

# 34. How to Make a Subnet Private?

A private subnet should not have a direct route to an Internet Gateway.

## Example

```text
Private Subnet
     |
     ↓
NAT Gateway
     |
     ↓
Internet Gateway
     |
     ↓
Internet
```

## Steps

1. Create a subnet.
2. Associate it with a route table.
3. Do not add:

```text
0.0.0.0/0 → Internet Gateway
```

4. If outbound internet is required, configure:

```text
0.0.0.0/0 → NAT Gateway
```

5. Ensure Security Groups and NACLs allow the required traffic.

## Example

```text
Private Route Table

Destination       Target
10.0.0.0/16       local
0.0.0.0/0         NAT Gateway
```

---

# 35. How to Communicate a Server in VPC1 to a Server in VPC2?

One common method is **VPC Peering**.

## Example

```text
VPC 1
10.0.0.0/16
 |
 | VPC Peering
 |
VPC 2
10.1.0.0/16
```

Suppose:

```text
Server 1:
10.0.1.10

Server 2:
10.1.1.10
```

## Steps

### Step 1

Create VPC Peering connection.

### Step 2

Accept the connection.

### Step 3

Update VPC1 route table:

```text
10.1.0.0/16 → Peering Connection
```

### Step 4

Update VPC2 route table:

```text
10.0.0.0/16 → Peering Connection
```

### Step 5

Update Security Groups.

Example:

```text
Allow:
TCP 22
Source:
10.0.0.0/16
```

### Step 6

Update NACLs if necessary.

### Step 7

Test connectivity.

---

# 36. What is Ping?

`ping` is a network troubleshooting utility that uses **ICMP Echo Request and Echo Reply** messages to test IP-level connectivity.

## Example

```bash
ping 10.0.1.10
```

Output may look like:

```text
64 bytes from 10.0.1.10:
time=2.3 ms
```

## What Does Ping Test?

Ping can help determine:

* Whether an IP is reachable
* Network latency
* Packet loss

## Important Interview Point

Ping does not test TCP ports.

For example:

```text
ping server
```

does not prove:

```text
TCP 22
```

is open.

ICMP must also be permitted by the relevant network controls.

---

# 37. What is Telnet?

Telnet is an old remote-login protocol that sends data without encryption.

Because of its security limitations, it should not be used for secure server administration.

However, the `telnet` client can sometimes be used to test whether a TCP port is reachable.

## Example

```bash
telnet 10.0.1.10 80
```

This attempts to establish a TCP connection to port 80.

## Use in Troubleshooting

Suppose your web server is expected to listen on:

```text
TCP 8080
```

You can test:

```bash
telnet 10.0.1.10 8080
```

## Important

For secure remote administration:

```text
Linux → SSH
Windows → RDP
```

---

# 38. Command to Check IP Address of a Server

## Linux

Use:

```bash
ip addr
```

or:

```bash
ip a
```

To check routing:

```bash
ip route
```

To check hostname:

```bash
hostname
```

## Windows

Use:

```cmd
ipconfig
```

PowerShell:

```powershell
Get-NetIPAddress
```

## Example

Linux:

```bash
ip a
```

You may see:

```text
inet 10.0.1.25/24
```

The private IP is:

```text
10.0.1.25
```

---

# 39. Command to Create a User in Linux Box

Basic command:

```bash
sudo useradd username
```

Create a home directory:

```bash
sudo useradd -m username
```

Create user with Bash shell:

```bash
sudo useradd -m -s /bin/bash username
```

Set password:

```bash
sudo passwd username
```

## Example

```bash
sudo useradd -m -s /bin/bash adi
sudo passwd adi
```

Check:

```bash
id adi
```

---

# 40. How to Change the Password of a User in Linux?

Use:

```bash
sudo passwd username
```

Example:

```bash
sudo passwd adi
```

The system asks for:

```text
New password:
Retype new password:
```

## Root Changing Another User's Password

A privileged administrator can use:

```bash
sudo passwd adi
```

---

# 41. Apache Default Installation Path

The exact path depends on the Linux distribution.

## Amazon Linux / RHEL

Apache package:

```text
httpd
```

Configuration directory:

```text
/etc/httpd/
```

Main configuration:

```text
/etc/httpd/conf/httpd.conf
```

Default document root:

```text
/var/www/html
```

## Ubuntu / Debian

Configuration directory:

```text
/etc/apache2/
```

Default document root:

```text
/var/www/html
```

## Example

Website file:

```text
/var/www/html/index.html
```

When Apache is running on port 80:

```text
http://server-ip
```

can serve that file.

---

# 42. IIS Default Installation Path

The default IIS website root is:

```text
C:\inetpub\wwwroot
```

Example:

```text
C:\inetpub\wwwroot\index.html
```

When IIS is running, the default website can be accessed through:

```text
http://server-ip
```

assuming the network and firewall configuration allows HTTP traffic.

---

# 43. Command to Install Apache in Linux

## Amazon Linux

For current Amazon Linux versions:

```bash
sudo dnf install -y httpd
```

On versions using `yum`:

```bash
sudo yum install -y httpd
```

Start Apache:

```bash
sudo systemctl start httpd
```

Enable Apache at boot:

```bash
sudo systemctl enable httpd
```

Check status:

```bash
sudo systemctl status httpd
```

## Ubuntu

Update package repository:

```bash
sudo apt update
```

Install:

```bash
sudo apt install -y apache2
```

Start:

```bash
sudo systemctl start apache2
```

Enable:

```bash
sudo systemctl enable apache2
```

Check:

```bash
sudo systemctl status apache2
```

---

# 44. How to Install IIS in Windows?

IIS can be installed using PowerShell.

Open PowerShell as Administrator.

Run:

```powershell
Install-WindowsFeature -Name Web-Server -IncludeManagementTools
```

Check installation:

```powershell
Get-WindowsFeature Web-Server
```

## GUI Method

You can also use:

```text
Server Manager
      ↓
Add Roles and Features
      ↓
Server Roles
      ↓
Web Server (IIS)
      ↓
Install
```

After installation, test:

```text
http://localhost
```

or:

```text
http://<server-ip>
```

---

# 45. What is a Listener in ELB?

A **listener** checks for incoming connection requests on a specified protocol and port.

## Example

Suppose an ALB has:

```text
HTTPS
Port 443
```

The listener receives HTTPS traffic.

```text
Client
  |
  ↓
ALB
  |
Listener :443
  |
Target Group
  |
EC2
```

## Listener Rule Example

An ALB can have rules such as:

```text
/api/*
     ↓
API Target Group
```

and:

```text
/images/*
     ↓
Image Target Group
```

## Interview Answer

> A listener is configured on a load balancer to accept connections on a specific protocol and port and then forward traffic according to listener rules.

---

# 46. What is Target Group in ELB?

A **Target Group** is a logical group of targets to which a load balancer forwards traffic.

Targets can include, depending on the load balancing configuration:

* EC2 instances
* IP addresses
* Lambda functions

## Example

```text
ALB
 |
Listener :80
 |
Target Group
 |
 +--- EC2-1
 |
 +--- EC2-2
 |
 +--- EC2-3
```

## Health Checks

The target group performs health checks.

For example:

```text
Protocol: HTTP
Port: 80
Path: /health
```

If a target fails health checks, the load balancer can stop sending normal traffic to it.

## Interview Answer

> A target group contains the backend targets that receive traffic from a load balancer and defines health-check behavior for those targets.

---

# 47. ALB vs NLB

## ALB

**Application Load Balancer**

Works at Layer 7.

Supports:

* HTTP
* HTTPS
* Host-based routing
* Path-based routing
* HTTP-aware routing

Example:

```text
example.com/api
        ↓
API servers

example.com/web
        ↓
Web servers
```

## NLB

**Network Load Balancer**

Works primarily at Layer 4.

Supports:

* TCP
* UDP
* TLS

It is designed for high-performance, low-latency network traffic.

## Comparison

| ALB                | NLB                            |
| ------------------ | ------------------------------ |
| Layer 7            | Layer 4                        |
| HTTP/HTTPS         | TCP/UDP/TLS                    |
| Path-based routing | Network-level traffic handling |
| Host-based routing | High-performance connections   |
| Web applications   | TCP/UDP workloads              |

## Interview Answer

> I would use ALB for HTTP/HTTPS applications where application-level routing is required, and NLB for high-performance TCP/UDP/TLS workloads where Layer 4 load balancing is appropriate.

---

# 48. Is it Possible to Reduce EBS Volume?

For most EBS volume types, you cannot directly shrink an existing EBS volume.

You can increase the size, but reducing it requires migration to a smaller volume.

## Example

Suppose:

```text
Current EBS:
100 GB
```

You need:

```text
50 GB
```

You cannot simply change:

```text
100 GB → 50 GB
```

Instead:

```text
100 GB EBS
     |
   Snapshot
     |
Create 50 GB EBS
     |
Copy required data
     |
Attach new volume
```

## Steps

1. Back up the data.
2. Create a snapshot if appropriate.
3. Create a smaller volume.
4. Attach the new volume.
5. Copy/migrate the data.
6. Verify the data.
7. Switch the application to the new volume.
8. Remove the old volume when no longer required.

## Interview Answer

> EBS volumes can generally be expanded, but they cannot simply be shrunk in place. To reduce the size, I would create a smaller volume and migrate the required data.

---

# 49. What is CIDR?

**CIDR = Classless Inter-Domain Routing**

CIDR notation is used to represent IP address ranges.

Example:

```text
10.0.0.0/16
```

The `/16` represents the prefix length.

## Example VPC

```text
VPC:
10.0.0.0/16
```

Subnets:

```text
Public:
10.0.1.0/24

Private:
10.0.2.0/24
```

## Why CIDR is Important

CIDR is used for:

* VPC address ranges
* Subnets
* Route tables
* Security Groups
* NACLs
* VPC Peering
* Network design

## Important Point

When designing VPCs that need to communicate with other networks, avoid overlapping CIDR ranges.

Example:

```text
VPC-A:
10.0.0.0/16

VPC-B:
10.1.0.0/16
```

These ranges do not overlap.

---

# 50. What is the Use of Tags?

Tags are key-value labels used to identify and organize AWS resources.

## Example

```text
Name = WebServer
Environment = Production
Project = ECommerce
Owner = DevOps
```

## Uses

### 1. Resource Identification

You can identify which server belongs to a project.

### 2. Cost Management

Tags can be used for cost allocation and reporting.

### 3. Automation

Scripts can find resources based on tags.

Example:

```text
Environment=Dev
```

An automation system can find all development resources.

### 4. Organization

Tags help manage large AWS environments.

### 5. Governance

Organizations can use tags to enforce naming and operational policies.

## Interview Answer

> Tags are key-value metadata attached to AWS resources and are used for organization, identification, cost allocation, automation, and governance.

---

# 51. By Default, How Many Elastic IPs Does AWS Offer?

AWS uses quotas for Elastic IP addresses.

A commonly applicable default quota is:

```text
5 Elastic IP addresses per Region
```

This is a quota, not a statement that every account can permanently use five EIPs for free.

The quota can be viewed and, when appropriate, increased through **AWS Service Quotas**.

## Interview Answer

> The common default Elastic IP quota is 5 per Region, and the quota can be increased through AWS Service Quotas if additional addresses are required.

## Important

Avoid unnecessary Elastic IPs. AWS charges for public IPv4 addresses under its current pricing model, including public IPv4 usage associated with AWS resources.

---

# 52. How Many Buckets Can We Create Per Region?

S3 bucket quotas are not best described as "10,000 buckets per Region."

For **general purpose S3 buckets**, the commonly applicable default quota is:

```text
10,000 buckets per AWS account
```

The quota is account-level.

## Interview Answer

> The commonly applicable default quota for general purpose S3 buckets is 10,000 buckets per AWS account, rather than a separate 10,000-bucket quota for every Region.

## Important

AWS service quotas can change, so for production planning always verify the current S3 quota documentation.

---

# 53. What is the Size of an Object Which We Can Upload to S3 Bucket?

The maximum size of a single S3 object is:

```text
5 TB
```

For very large objects, use **Multipart Upload**.

## Multipart Upload

Instead of uploading one huge file at once:

```text
Large File
    |
    +--- Part 1
    +--- Part 2
    +--- Part 3
    +--- Part 4
    |
    ↓
S3 Object
```

This improves reliability and allows failed parts to be retried without restarting the entire upload.

## Interview Answer

> The maximum size of a single S3 object is 5 TB. Multipart upload is recommended for large objects.

---

# 54. EBS Volume Size Limit

The maximum EBS volume size depends on the EBS volume type.

For common modern EBS volume types such as **gp3**, the maximum volume size is:

```text
64 TiB
```

For example:

```text
gp3
1 GiB → 64 TiB
```

The exact limits depend on the volume type.

## Interview Answer

> EBS volume limits depend on the volume type. For gp3, the maximum volume size is 64 TiB.

---

# 55. What is AWS?

**AWS = Amazon Web Services**

AWS is a cloud computing platform provided by Amazon.

It provides services for:

* Compute
* Storage
* Networking
* Databases
* Security
* Monitoring
* Serverless computing
* Containers
* AI/ML
* DevOps

## Important AWS Services

### Compute

```text
EC2
Lambda
ECS
EKS
```

### Storage

```text
S3
EBS
EFS
```

### Networking

```text
VPC
ELB
Route 53
CloudFront
```

### Database

```text
RDS
DynamoDB
```

### Security

```text
IAM
KMS
Secrets Manager
```

### Monitoring

```text
CloudWatch
```

## Example

Instead of buying a physical server:

```text
Traditional Data Center
        ↓
Purchase Hardware
        ↓
Install OS
        ↓
Maintain Hardware
```

With AWS:

```text
AWS
 ↓
Launch EC2
 ↓
Configure Application
 ↓
Run Application
```

---

# 56. What is Cloud Computing?

Cloud computing is the delivery of computing resources over the internet on demand.

Resources can include:

* Compute
* Storage
* Networking
* Databases
* Applications
* Analytics
* AI/ML

## Traditional Model

```text
Company
   ↓
Buy Physical Server
   ↓
Install OS
   ↓
Configure Hardware
   ↓
Maintain Server
```

## Cloud Model

```text
Cloud Provider
      ↓
Select Resource
      ↓
Configure
      ↓
Use
      ↓
Pay according to usage/pricing model
```

## Important Characteristics

Cloud computing commonly provides:

### On-Demand Resources

Resources can be provisioned when required.

### Scalability

Resources can be increased or decreased according to workload.

### Elasticity

Resources can automatically or manually scale based on requirements.

### Pay-as-you-go

Costs are based on the services/resources used and their pricing model.

### Broad Network Access

Services can be accessed over networks using standard protocols and interfaces.

## Example

A company needs a web server.

Instead of buying a physical server, it launches:

```text
EC2
 ↓
Install Apache
 ↓
Deploy Website
```

---

# 57. How to Access AWS Platform?

AWS can be accessed in several ways.

---

## 1. AWS Management Console

The AWS Management Console is a web-based graphical interface.

You can manage:

```text
EC2
S3
VPC
IAM
RDS
CloudWatch
```

and many other services.

Example:

```text
Browser
   ↓
AWS Management Console
   ↓
AWS Services
```

---

## 2. AWS CLI

AWS CLI allows you to interact with AWS using commands.

Example:

```bash
aws sts get-caller-identity
```

This checks the AWS identity associated with the CLI credentials.

Example:

```bash
aws ec2 describe-instances
```

This retrieves information about EC2 instances.

---

## 3. AWS SDK

Applications can interact with AWS through AWS SDKs.

For Python, the commonly used SDK is:

```text
Boto3
```

Example:

```python
import boto3

ec2 = boto3.client("ec2")
response = ec2.describe_instances()
```

---

## 4. Infrastructure as Code

Tools such as Terraform can create and manage AWS resources.

Example:

```text
Terraform
    ↓
AWS Provider
    ↓
AWS API
    ↓
EC2 / VPC / S3 / IAM
```

---

# 58. What is EC2?

**EC2 = Elastic Compute Cloud**

EC2 is AWS's virtual server/compute service.

An EC2 instance is a virtual machine that you can use to run applications.

## When launching EC2, you can configure:

* AMI
* Instance type
* Key pair
* VPC
* Subnet
* Security Group
* EBS storage
* Network settings
* IAM role

## Example

```text
AMI:
Amazon Linux

Instance Type:
t3.micro

Storage:
20 GB gp3

Security Group:
SSH 22
HTTP 80

Subnet:
Public Subnet
```

## EC2 Architecture

```text
                    AWS
                     |
                    VPC
                     |
                  Subnet
                     |
                    EC2
             /       |       \
          CPU      Memory     EBS
```

## Why EC2?

EC2 is used when you need control over:

* Operating system
* Software installation
* Server configuration
* Networking
* Application runtime
* Storage

## Interview Answer

> EC2 is AWS's virtual compute service that provides resizable compute capacity. We can select an AMI, instance type, storage, networking, and security configuration when launching an instance.

---

# 59. How to Add EBS Volume to Multiple Instances?

Normally, an EBS volume is attached to one EC2 instance.

```text
EBS Volume
     |
     ↓
EC2 Instance
```

However, AWS provides **EBS Multi-Attach** for supported configurations.

## EBS Multi-Attach

For supported EBS volume types and compatible EC2 instances, an EBS volume can be attached to multiple EC2 instances in the **same Availability Zone**.

Example:

```text
                EC2-1
                  |
                  |
EBS Multi-Attach --+-- EC2-2
                  |
                  |
                EC2-3
```

## Important

Multi-Attach does not mean that every filesystem can safely be mounted read/write simultaneously by multiple servers.

The application and filesystem must support the required concurrent access model.

For example, simply mounting a normal filesystem from multiple servers without appropriate coordination can result in data corruption.

---

## Alternative: EFS

If the requirement is:

> "Multiple EC2 instances need to access the same shared files."

Then **Amazon EFS** is often a more suitable architecture.

```text
              EFS
               |
       +-------+-------+
       |       |       |
      EC2     EC2     EC2
```

Multiple EC2 instances can mount the same EFS file system.

## Difference

```text
EBS
 ↓
Block Storage
 ↓
Primarily attached to EC2
```

```text
EFS
 ↓
Managed File Storage
 ↓
Designed for shared access
```

## Interview Answer

> Normally, an EBS volume is attached to one EC2 instance. AWS EBS Multi-Attach supports attaching certain supported EBS volumes to multiple compatible EC2 instances in the same Availability Zone. If multiple servers need shared file storage, I would generally consider EFS.

---

# ⭐ Important AWS Interview Revision

The following concepts are strongly connected and should be understood together.

---

# AWS Networking Architecture

```text
                         Internet
                            |
                            |
                   Internet Gateway
                            |
                            |
                    Public Subnet
                            |
                     Route Table
                            |
                     Load Balancer
                            |
                            |
                    Private Subnet
                            |
                       EC2 Server
                            |
                         Database
```

For outbound internet access from a private subnet:

```text
Private EC2
     |
     ↓
Private Route Table
     |
     ↓
NAT Gateway
     |
     ↓
Public Subnet
     |
     ↓
Internet Gateway
     |
     ↓
Internet
```

---

# VPC Communication

```text
VPC-1
10.0.0.0/16
     |
     |
VPC Peering
     |
     |
VPC-2
10.1.0.0/16
```

Routes must be configured in both directions.

---

# Security Architecture

```text
                    VPC
                     |
                  Subnet
                     |
              +------+------+
              |             |
             NACL           EC2
                            |
                     Security Group
```

Remember:

```text
NACL
↓
Subnet level
Stateless
Allow + Deny

Security Group
↓
Resource/Network Interface level
Stateful
Allow only
```

---

# Storage Architecture

```text
                    AWS Storage
                         |
          +--------------+--------------+
          |              |              |
         EBS            S3             EFS
          |              |              |
     Block Storage   Object Storage  File Storage
          |              |              |
         EC2          Objects       Shared Files
```

---

# AMI and Snapshot Relationship

```text
                 EC2
                  |
                EBS
                  |
             Snapshot
                  |
                  |
                 AMI
                  |
                  ↓
             New EC2
```

Remember:

```text
Snapshot
↓
Backup of EBS volume

AMI
↓
Template for launching EC2
```

---

# ELB Architecture

```text
                  Users
                    |
                    ↓
                   ELB
                    |
                 Listener
                    |
              Target Group
             /      |      \
            ↓       ↓       ↓
          EC2-1   EC2-2   EC2-3
```

Remember:

```text
ELB
 ↓
Listener
 ↓
Target Group
 ↓
Targets
```

---

# Common Port Numbers

| Service | Port |
| ------- | ---: |
| SSH     |   22 |
| DNS     |   53 |
| HTTP    |   80 |
| HTTPS   |  443 |
| RDP     | 3389 |

Memory:

```text
SSH   → 22
DNS   → 53
HTTP  → 80
HTTPS → 443
RDP   → 3389
```

---

# Linux Commands — Quick Revision

## Check IP

```bash
ip a
```

## Check Routes

```bash
ip route
```

## Create User

```bash
sudo useradd -m username
```

## Set Password

```bash
sudo passwd username
```

## Check User

```bash
id username
```

## Install Apache — Amazon Linux

```bash
sudo dnf install -y httpd
```

## Start Apache

```bash
sudo systemctl start httpd
```

## Enable Apache

```bash
sudo systemctl enable httpd
```

## Check Apache

```bash
sudo systemctl status httpd
```

## Check Block Devices

```bash
lsblk
```

## Check Mounted Filesystems

```bash
df -h
```

## Test Connectivity

```bash
ping <ip-address>
```

## Test TCP Port

```bash
telnet <ip-address> <port>
```

---

# Windows Server — Quick Revision

## Check IP

```cmd
ipconfig
```

## Install IIS

```powershell
Install-WindowsFeature -Name Web-Server -IncludeManagementTools
```

## Check IIS Feature

```powershell
Get-WindowsFeature Web-Server
```

## Create Local User

```powershell
New-LocalUser -Name "adi"
```

## IIS Default Website Path

```text
C:\inetpub\wwwroot
```

---

# 🔥 Most Important One-Line Interview Definitions

### Region

> A geographical AWS location containing multiple Availability Zones.

### Availability Zone

> An isolated location within an AWS Region used to improve availability and fault tolerance.

### VPC

> A logically isolated virtual network in AWS.

### Subnet

> A smaller IP network inside a VPC.

### Public Subnet

> A subnet whose route table has a route to an Internet Gateway.

### Private Subnet

> A subnet without a direct route to an Internet Gateway.

### Internet Gateway

> A VPC component that provides a path between appropriately configured VPC resources and the internet.

### NAT Gateway

> A managed NAT service that allows private subnet resources to initiate outbound internet connections.

### Route Table

> A set of routing rules that determines where network traffic should go.

### Security Group

> A stateful resource-level virtual firewall that uses allow rules.

### NACL

> A stateless subnet-level firewall that supports allow and deny rules.

### VPC Peering

> A private networking connection between two VPCs.

### EC2

> AWS's resizable virtual compute service.

### EBS

> Persistent block storage primarily used with EC2.

### S3

> AWS object storage service.

### Snapshot

> A point-in-time backup of an EBS volume.

### AMI

> A template used to launch EC2 instances.

### EIP

> A static public IPv4 address allocated to an AWS account.

### ELB

> A managed load-balancing service that distributes traffic across targets.

### Listener

> A load balancer configuration that accepts traffic on a specified protocol and port.

### Target Group

> A logical group of targets that receives traffic from a load balancer.

### CIDR

> A notation used to define IP address ranges using a network prefix.

### Tag

> Key-value metadata used to organize, identify, automate, and manage AWS resources.

---

# 🎯 Important Interview Comparisons

## Region vs Availability Zone

```text
Region
↓
Geographical Location
↓
Contains Multiple AZs

Availability Zone
↓
Isolated Location
↓
Inside a Region
```

---

## EBS vs S3

```text
EBS
↓
Block Storage
↓
EC2

S3
↓
Object Storage
↓
Files / Objects
```

---

## AMI vs Snapshot

```text
AMI
↓
Launch EC2

Snapshot
↓
Backup EBS
```

---

## Public IP vs EIP

```text
Public IP
↓
Can change

EIP
↓
Static Public IPv4
```

---

## Security Group vs NACL

```text
Security Group
↓
Stateful
↓
Resource/ENI
↓
Allow only

NACL
↓
Stateless
↓
Subnet
↓
Allow + Deny
```

---

## ALB vs NLB

```text
ALB
↓
Layer 7
↓
HTTP / HTTPS
↓
Application Routing

NLB
↓
Layer 4
↓
TCP / UDP / TLS
↓
High-performance Network Traffic
```

---

# 🧠 Final AWS Architecture to Remember

```text
                              AWS
                               |
                              Region
                               |
                    +----------+----------+
                    |                     |
                   AZ-1                  AZ-2
                    |                     |
                   VPC                   VPC
                    |
          +---------+---------+
          |                   |
    Public Subnet       Private Subnet
          |                   |
     Route Table          Route Table
          |                   |
         IGW              NAT Gateway
          |                   |
          |                  EC2
          |
         ALB
          |
     Target Group
       /      \
     EC2      EC2

                    Storage
                       |
             +---------+---------+
             |         |         |
            EBS       S3        EFS
             |         |         |
            EC2      Objects   Shared Files
```

---

# 🚀 Final Interview Memory Map

```text
AWS
│
├── Region
│   └── Availability Zones
│
├── VPC
│   ├── Subnets
│   │   ├── Public
│   │   └── Private
│   │
│   ├── Route Tables
│   ├── Internet Gateway
│   ├── NAT Gateway
│   ├── Security Groups
│   ├── NACL
│   └── VPC Peering
│
├── EC2
│   ├── AMI
│   ├── Instance Type
│   ├── Key Pair
│   ├── Security Group
│   ├── EBS
│   └── Elastic IP
│
├── Storage
│   ├── EBS
│   ├── S3
│   ├── EFS
│   └── Snapshots
│
└── Load Balancing
    ├── ALB
    ├── NLB
    ├── GWLB
    ├── Listener
    └── Target Group
```

---

# ✅ Interview Preparation Strategy

For each AWS interview question, try to answer in this order:

```text
1. Definition
        ↓
2. Purpose / Use
        ↓
3. Example
        ↓
4. Important Difference / Feature
```

For example:

### Interviewer:

**What is a Security Group?**

### Answer:

> A Security Group is a stateful virtual firewall associated with resources such as EC2 network interfaces. It controls inbound and outbound traffic using allow rules. For example, for a Linux web server, I can allow SSH on port 22 from my IP and HTTP on port 80 from the required clients. Because it is stateful, return traffic for an allowed connection is automatically permitted.

This structure makes the answer **clear, technical, and easy to understand during an interview**.

