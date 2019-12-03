## AWS Certified Developer Associate
My personal notes.

## Author
Aditya Hajare ([Linkedin](https://in.linkedin.com/in/aditya-hajare)).

## Current Status
WIP (Work In Progess).

## License
Open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).

**************

## Table of Contents
- AWS Basics (IAM & EC2)
    - [AWS Regions](#aws-regions)
    - [IAM - Identity And Access Management](#iam-basics)
    - [Security Groups](#security-groups)
    - [Elastic IPs](#elastic-ips)

---

### AWS Regions
Each availability zone is a physical data center in the region, but separated from the other ones (so that they're isolated from disasters).

### IAM - Identity And Access Management
- IAM has a global view.
- Whole AWS security is there:
    * Users
    * Groups
    * Roles
- Never use **Root** account except for initial setup
- One IAM **User** per physical person.
- One IAM **Role** per application.

### Security Groups
- Security groups are like firewall on EC2 instances.
- They regulate:
    * Access to ports.
    * Authorised IP ranges - IPv4 and IPv6.
    * Inbound network (from outside to instance).
    * Outbound network (from instance to outside).
- Security groups are locked down to a region/VPC combination.
- They live outside EC2. i.e. Security groups are not something that is running on EC2 instance.
- It's a good practice to create/maintain one separate security group for SSH access.
- By default:
    * All inbound traffic is blocked.
    * All outbound traffic is authorised
- Common gotchas:
    * If your application is not accessible (time out), then it's a security group issue.
    * If your application is giving "connection refused", then it's an application error. Or may be your application is not launched.

### Elastic IPs
- It is quite an uncommon pattern to use Elastic IPs. That is because:
    * We can have only 5 Elastic IPs in our account (although we can ask AWS to increate this limit.).
- Always **try to avoid using Elastic IP**.
    * They often reflect poor architectural decisions.
    * Instead, use a random public IP and register a DNS name to it.
    * One should use a load balancer and not use public IP.
- If we are not using elastic IP, when EC2 instance is stopped and then started again, it can change its public IP.
- If we need fixed public IP for our instance (god knows for what reason), then we go for Elastic IP.
- Elastic IP is a public IPv4 we own as long as we don't delete it.
- One elastic IP can be attached to one EC2 instance at a time.
- With elastic IP, we can mask the failure of an EC2 instance or software by rapidly remapping the address to another instance in our account.