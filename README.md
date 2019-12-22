## AWS Certified Developer
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
    - [IAM - Identity And Access Management](#iam---identity-and-access-management)
    - [Security Groups](#security-groups)
    - [Elastic IPs](#elastic-ips)
    - [SSH Into EC2 Instance And Install Apache](#ssh-into-ec2-instance-and-install-apache)
    - [EC2 User Data](#ec2-user-data)

- AWS Fundamentals: ELB + ASG + EBS
    - [ELB - Elastic Load Balancers](#elb---elastic-load-balancers)
    - [ASG - Auto Scaling Group](#asg---auto-scaling-group)
    - [EBS - Elastic Block Store](#ebs---elastic-block-store)

- AWS Fundamentals: Route 53 + RDS + ElastiCache + VPC
    - [Route 53](#route-53)
    - [RDS - Relational Database Service](#rds---relational-database-service)
    - [ElastiCache](#elasticache)
    - [VPC - Virtual Private Cloud And 3 Tier Architecture](#vpc---virtual-private-cloud-and-3-tier-architecture)

- Amazon S3
    - [S3 - Buckets And Objects](#s3---buckets-and-objects)
    - [S3 - Versioning](#s3---versioning)
    - [S3 - Encryption For Objects](#s3---encryption-for-objects)
        - [SSE-S3](#sse-s3)
        - [SSE-KMS](#sse-kms)
        - [SSE-C](#sse-c)
        - [Client Side Encryption](#client-side-encryption)
    - [S3 - Security And Bucket Policies](#s3---security-and-bucket-policies)
    - [S3 - Websites](#s3---websites)
    - [S3 - CORS](#s3---cors)
    - [S3 - Consistency Model](#s3---consistency-model)
    - [S3 - Performance](#s3---performance)

- AWS CLI, IAM Roles, EC2 Instance Metadata, AWS SDK, CLI Profiles
    - [IAM Roles](#iam-roles)
    - [AWS CLI Dry Runs](#aws-cli-dry-runs)
    - [AWS CLI STS Decode Errors](#aws-cli-sts-decode-errors)
    - [EC2 Instance Metadata](#ec2-instance-metadata)
    - [AWS SDK](#aws-sdk)
    - [AWS CLI Profiles](#aws-cli-profiles)

- Elastic Beanstalk
    - [Elastic Beanstalk](#elastic-beanstalk)
    - [Elastic Beanstalk Deployment](#elastic-beanstalk-deployment)
    - [Elastic Beanstalk Advanced Concepts](#elastic-beanstalk-advanced-concepts)
    - [Elastic Beanstalk Important Points](#elastic-beanstalk-important-points)

- AWS CICD (CodeCommit, CodePipeline, CodeBuild, CodeDeploy)
    - [CICD - Continuous Integration And Continuous Deployment Intro](#cicd---continuous-integration-and-continuous-deployment-intro)
    - [CodeCommit](#codecommit)
    - [CodePipeline](#codepipeline)
    - [CodeBuild](#codebuild)
    - [CodeDeploy](#codedeploy)

- AWS CloudFormation (Infrastructure As Code)
    - [CloudFormation - Infrastructure As Code](#cloudformation---infrastructure-as-code)
    - [CloudFormation - Template - Resources](#cloudformation---template---resources)
    - [CloudFormation - Template - Parameters](#cloudformation---template---parameters)
    - [CloudFormation - Template - Mappings](#cloudformation---template---mappings)
    - [CloudFormation - Template - Outputs](#cloudformation---template---outputs)
    - [CloudFormation - Template - Conditions](#cloudformation---template---conditions)
    - [CloudFormation - Template - Intrinsic Functions](#cloudformation---template---intrinsic-functions)
    - [CloudFormation - Rollbacks](#cloudformation---rollbacks)

- AWS Monitoring & Audit: CloudWatch, X-Ray And CloudTrail
    - [AWS Monitoring Intro](#aws-monitoring-intro)
    - [CloudWatch Metrics](#cloudwatch-metrics)
    - [CloudWatch Alarms](#cloudwatch-alarms)
    - [CloudWatch Logs](#cloudwatch-logs)
    - [CloudWatch Events](#cloudwatch-events)
    - [AWS X-Ray](#aws-x-ray)
    - [AWS CloudTrail](#aws-cloudtrail)

- AWS Integration And Messaging: SQS, SNS And Kinesis
    - [Introduction To Messaging](#introduction-to-messaging)
    - [AWS SQS](#aws-sqs)
    - [AWS FIFO Queue](#aws-fifo-queue)
    - [SQS Extended Client](#sqs-extended-client)
    - [SQS Security](#sqs-security)
    - [AWS SNS](#aws-sns)
    - [SNS + SQS - Fan Out](#sns-+-sqs---fan-out)
    - [AWS Kinesis](#aws-kinesis)
    - [Kinesis Security](#kinesis-security)
    - [Kinesis Data Analytics](#kinesis-data-analytics)
    - [Kinesis Firehose](#kinesis-firehose)
    - [SQS vs SNS vs Kinesis](#sqs-vs-sns-vs-kinesis)
    - [Amazon MQ](#amazon-mq)

- AWS Serverless: Lambda
    - [AWS Serverless](#aws-serverless)
    - [AWS Lambda](#aws-lambda)
    - [AWS Lambda Configurations](#aws-lambda-configurations)
    - [AWS Lambda Limits](#aws-lambda-limits)
    - [AWS Lambda Concurrency And Throttling](#aws-lambda-concurrency-and-throttling)
    - [AWS Lambda Retries And DLQ](#aws-lambda-retries-and-dlq)
    - [AWS Lambda Logging Monitoring And Tracing](#aws-lambda-logging-monitoring-and-tracing)
    - [AWS Lambda Versions And Aliases](#aws-lambda-versions-and-aliases)
    - [AWS Lambda Best Practices](#aws-lambda-best-practices)

- AWS Serverless: DynamoDB
    - [DynamoDB Intro](#dynamodb)
    - [DynamoDB - Provisioned Throughput](#dynamodb---provisioned-throughput)
    - [DynamoDB - Partitions Internal](#dynamodb---partitions-internal)
    - [DynamoDB - Throttling](#dynamodb---throttling)
    - [DynamoDB - Basic APIs](#dynamodb---basic-apis)
    - [DynamoDB - Indexes](#dynamodb---indexes)
    - [DynamoDB - Concurrency](#dynamodb---concurrency)
    - [DynamoDB - Accelerator - DAX](#dynamodb---accelerator---dax)
    - [DynamoDB - Streams](#dynamodb---streams)
    - [DynamoDB - Security And Other Features](#dynamodb---security-and-other-features)

- AWS Serverless: API Gateway & Congnito
    - [API Gateway Intro](#api-gateway-intro)
    - [API Gateway - Deployment Stages](#api-gateway---deployment-stages)
    - [API Gateway - Mapping Templates](#api-gateway---mapping-templates)
    - [API Gateway - Swagger And Open API Specifications](#api-gateway---swagger-and-open-api-specifications)
    - [API Gateway - Caching](#api-gateway---caching)
    - [API Gateway - Logging Monitoring And Tracing](#api-gateway---logging-monitoring-and-tracing)
    - [API Gateway - CORS - Usage Plans And API Keys](#api-gateway---cors---usage-plans-and-api-keys)
    - [API Gateway - Security](#api-gateway---security)
    - [AWS Cognito](#aws-cognito)

- AWS Serverless: SAM - Serverless Application Model
    - [SAM 101](#sam-101)

- AWS Security & Encryption: KMS, Encryption SDK, SSM Parameter Store, IAM, STS
    - [Encryption 101](#encryption-101)
    - [KMS - Key Management System](#kms---key-management-system)
    - [Encryption SDK](#encryption-sdk)
    - [SSM Parameter Store](#ssm-parameter-store)
    - [IAM Best Practices - General](#iam-best-practices---general)

- AWS Other Services: CloudFront, Step Functions, SWF, Docker, ECS, ECR
    - [CloudFront](#cloudfront)
    - [Step Functions](#step-functions)
    - [SWF - Simple Workflow Service](#swf---simple-workflow-service)
    - [Docker](#docker)
    - [ECS - Elastic Container Service](#ecs---elastic-container-service)
    - [ECR - Elastic Container Registry](#ecr---elastic-container-registry)
    - [SES - Simple Email Service](#ses---simple-email-service)

---

### AWS Regions
Each `Availability Zone` is a physical data center in the region, but separated from the other ones (so that they're isolated from disasters).

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

### SSH Into EC2 Instance And Install Apache
- `ec2-user` is the default user in our EC2 instance machine.
- SSH command syntax: `ssh -i [PATH_TO_KEYFILE] [USER]@[PUBLIC_IP]`
- Copy public IP (In below example, we will use `192.168.0.1`).
- In terminal, type:
    ```
    # SSH into EC2 using public ip.
    ssh -i my-key-file.pem ec2-user@192.168.0.1

    # Get sudo access for our user.
    sudo su

    # Update packages.
    yum update -y

    # Install httpd.
    yum install -y httpd.x86_64

    # Start httpd.
    # NOTE: If we get error "bash:systemctl command not found", make sure to use "Amazon Linux 2" and not just "Amazon Linux".
    systemctl start httpd.service

    # Make sure system remains enabled across reboots. Below command will create a symlink.
    systemctl enable httpd.service

    # Lets do a quick CURL on localhost:80. It will give us default test HTML page code.
    curl localhost:80
    ```
- At this point if we visit public ip in our browser, we will get timeout. So clearly it's an issue with security groups configurations.
- Go to `Inbound Rules` security group settings and configure HTTP rule on port 80. Refer to following settings:
    ```
    Type: HTTP
    Protocol: TCP
    Port Range: 80
    Source: Custom 0.0.0.0/0
    ```
- Now, if we visit public ip in browser, we shall see test page.
- Default test page is located at:
    `/var/www/html/index.html`

### EC2 User Data
- It is possible to bootstrap our EC2 instances using an **EC2 User Data script**.
    * `Bootstrapping` simply means running commands when a machine starts.
    * Bootstrapping script is run only once on EC2 instance's **first start**.
- EC2 user data is used to automate boot tasks such as:
    * Installing updates.
    * Installing softwares.
    * Downloading common files from the internet.
    * Almost anything you can think of.
- **EC2 User Data Script is run with a ROOT user**. i.e. every command will be ran with `sudo` rights.
- Example:
    1. Launch new EC2 instance: `Amazon Linux 2 AMI (HVM), SSD Volume Type`.
    2. Select `t2-micro` and click on **Configure Instance Details**.
    3. Scroll down to **Advanced Details** -->  **User Data**
    4. Select **As Text** radio button and paste the entire example script from below:
        ```
        #!/bin/bash

        #####################################################
        # USE THIS FILE IF YOU HAVE LAUNCHED AMAZON LINUX 2 #
        #####################################################

        # Get admin priviledges. Although it is not required to do so since the script will be run with ROOT user.
        sudo su

        # Install httpd (Linux 2 version)
        yum update -y
        yum install -y httpd.x86_64
        systemctl start httpd.service
        systemctl enable httpd.service
        echo "Hello world from Aditya at $(hostname -f)" > /var/www/html/index.html
        ```
    5. Make sure EC2 instance is having a security group with `HTTP PORT 80` and `SSH` policy enabled.
    6. Launch the instance and visit EC2's public ip in browser. We shall see the test page.
    7. **NOTE:** With above script, we have automated entire flow from above - [SSH Into EC2 Instance And Install Apache](#ssh-into-ec2-instance-and-install-apache)

### ELB - Elastic Load Balancers
- Types of ELB (`Elastic Load Balancer`):
    1. Classic Load Balancer (v1 - Old Generation) - 2009
    2. Application Load Balancer (v2 - New Generation) - 2016
    3. Network Load Balancer (v2 - New Generation) - 2016
- Amazon recommends using new generation/v2 load balancers as they provide more features.
- Health Checks:
    * Health checks are done on port and route (/health is common).
    * If the response is 200 (OK) then instance is healthy.
- Application Load Balancer (ALB) - Layer 7 - Allow to do:
    * Load balancing to multiple HTTP applications across machines (Target Groups).
    * Load balancing to multiple applications on the same machine (for e.g. containers).
    * Load balancing based on **route** in url.
    * Load balancing based on **hostname** in url.
- Basically load balancers are osum for mico-services and container-based applications (For e.g. Docker and Amazon ECS).
- Load balancers has a port mapping feature to redirect to dynamic port.
- **Application Load Balancer v2** - Layer 7 - osum features:
    * Stickiness can be enabled at target group level:
        * Same request goes to the same instance.
        * Stickiness is directly generated by the ALB (not the application).
    * ALB supports HTTP, HTTPS and Websockets protocol.
    * The application servers don't see the ip of client directly.
        * The true ip of the client is inserted into header **X-Forwarded-For**
        * The port of client's request is inserted into header **X-Forwarded-Port**.
        * The prototype of client's request is inserted into header **X-Forwarded-Proto**.
- **Network Load Balancer v2** - Layer 4 - allow to:
    * Forward TCP traffic to your instance.
    * Handle millions of request per second.
    * Support for static ip or elastic ip.
    * Less latency ~100 ms (ALB has ~400 ms latency).
    * They are chosen for extreme performance and should not be the default load balancer you choose.
    * Creation process is quite same as Application Load Balancer.
- **Load Balancer 101**
    * Classic load balancers are deprecated.
    * `Application Load Balancer` is for HTTP, HTTPS and Websockets.
    * `Network Load Balancer` is for TCP.
    * `CLB` and `ALB` supports SSL certificates and provide SSL termination.
    * All load balancers have `health check` capability.
    * `ALB` can route based on `hostname` and `path (i.e. route based)`.
    * `ALB` is great fit with **ECS** (Docker).
    * Any load balancer has a static host name. IP resolved from hostname should never ever be used.
    * `Load Balancers` can scale but not instantaneously. Ask AWS for a `warm up`.
    * `NLB` (Network Load Balancer) directly see client ip at application tier.
        * There is no `X-Forwarded-For` or `X-Forwarded-Port` headers.
    * `4xx` errors are client induced errors.
    * `5xx` errors are application induced errors.
        * Load balancer error `503` means at capacity or no registered target.
    * If `Load Balancer can't connect to your application`, check your **Security Groups**.

### ASG - Auto Scaling Group
- Goal of Auto Scaling Group (ASG) is to:
    * `Scale out` (Add EC2 Instances) to match an increased load.
    * `Scale in` (Remove EC2 instances) to match a decreased load.
    * Ensure we have minimum and a maximum number of machines (instances) running in an ASG.
    * Automatically `Register` new instances to a load balancer.
- LB (Load Balancer) and ASG (Auto Scaling Group) works hand in hand in AWS.
- ASGs have following attributes:
    * Launch configuration:
        * AMI (`Amazon Machine Image` e.g. `Amazon Linux 2`) + Instance Type.
        * [EC2 User Data](#ec2-user-data).
        * EBS (Elastic Block Store) Volumes.
        * Security Groups.
        * SSH Key Pair.
    * Minimum Size, Maximum Size, Initial Capacity.
    * Network + Subnet Information.
    * LB (Load Balancer) Information.
    * Scaling Policies (i.e. What will trigger a scale out and what will trigger a scale in).
- It is possible to scale an ASG based on `CloudWatch` alarms.
    * `CloudWatch Alarm` monitors a metric (such as `Average CPU`).
    * `Metrics` are computed for the overall `ASG` instances.
    * Based on `Alarm`:
        * We can create `scale-out policies` (increase the number of instances).
        * We can create `scale-in policies` (decrease the number of instances).
- Auto Scaling New Rules:
    * It is now possible to define `better` auto scaling rules that are directly managed by EC2. For e.g.
        * Target Average CPU Usage.
        * Number of requests on the ELB per instance.
        * Average Network In.
        * Average Network Out.
- Auto Scaling Based On Custom Metric:
    * We can auto scale based on a custom metric. For e.g. Auto scale based on number of connected users to my application running on EC2 instance(s).
    * Send custom metric from application on EC2 to `CloudWatch (PutMetric API)`.
    * Use the `CloudWatch Alarm` as the scaling policy for `ASG`.
- **ASG (Auto Scaling Group) 101**:
    * Scaling policies can be on CPU usage, network usage etc.. and can even be on custom metrics as well as based on a schedule (if you know your visitors pattern).
    * ASGs use `Launch Configurations` and you update an ASG by providing a new `Launch Configuration`.
    * `IAM Roles` (Identity And Access Management Roles) attached to an ASG will get assigned to EC2 instances.
    * **ASGs are free**. You only pay for the underlying resources being launched.
        * i.e. Number of EC2 instances spun in.
    * ASG will automatically restart instances running under them if they (instances) get terminated for whatever reason. **Extra Safety!**
    * If a LB (Load Balancer) marks an instace as unhealthy, then ASG can terminate that instance and will replace it further.

### EBS - Elastic Block Store
- EC2 instance loses its root volume (main drive) when it is manually terminated.
- Enexpected terminations might happen from time to time (AWS would email you whenever this happens).
- Sometimes, you need a way to store your EC2 instance data somewhere even though it is terminated. This is where EBS volume comes into picture.
- **EBS (Elastic Block Store) Volume** is a network drive you can attach to your EC2 instance while they are running.
- It allows EC2 instances to persist data.
- **What are EBS volumes:**
    * It's a network drive (not a physical drive).
        * EC2 instance communicate to EBS volume over a network (since it is not physically attached to EC2 instance). So there may be bit of latency (very little though).
        * EBS volume can be detached from one EC2 instance and attached to another EC2 instance very quickly.
    * EBS volume is locked to an `Availability Zone (AZ)`.
        * For e.g. EBS Volume attached to EC2 instance running in `us-east-1a` cannot be attached to EC2 instance running in `us-east-1b`.
        * To move a volume across different `Availability Zone (AZ)`, we first need to **`snapshot`** it.
    * EBS volume has a provisioned capacity (size in GBs, and IOPS). i.e. We need to first specify the volume size and `IOPS (Number of I/O operations per second)`.
        * You get billed for all the provisioned capacity.
        * You can increase the size and IOPS over time.
    * Types of EBS volumes:
        1. GP2 (SSD): General Purpose SSD volume. Balances price and performance for a wide variety of workloads.
        2. IO1 (SSD): **Highest Performance SSD volume**. Good for mission-critical low-latency or high throughput workloads.
        3. ST1 (HDD): Low Cost HDD volume designed for frequent access and throughput-intensive workloads. Good for Big Data operations.
        4. SC1 (HDD): **Lowest Cost HDD volume**. Good for less frequently accessed workloads.
    * EBS volumes are characterized in **Size, Throughput and IOPS (Number of I/O operations per second)**.
    * Always consult AWS documetations about EBS volumes before choosing one.
    * EBS Snapshots:
        * EBS volumes can be backed up using `snapshots`.
        * Snapshots only take the actual space of the blocks on the volume.
        * Snapshots are used for:
            * Backups: ensuring you can save your data in case of catastrophe.
            * Volume migration:
                * Resizing a volume down.
                * Changing the volume type.
                * Encrypt a volume.
- **EBS Encryption:**
    * When we create an encrypted EBS volume, we get following:
        * Data at rest is encrypted inside the volume.
        * All the data moving between EC2 instance and volume is encrypted.
        * All `snapshots` are encrypted.
        * All volumes created from `snapshots` are also encrypted.
    * Encryption and decryption is handled transparently (we have nothing to do there).
    * Encryption has a minimal impact on latency.
    * EBS encryption leverages keys from **KMS (AES-256)**.
    * Copying and unencrypted snapshot allows encryption.
- **EBS vs Instance Store:**
    * Some EC2 instance do not come with Root EBS volumes, instead they come with `Instance Store`.
    * `Instance Store` is physically attached to the EC2 machine.
    * **Instance Store:**
        * Pros:
            * Since the `Instance Store` is physically attached to EC2 instance, it provides better I/O performance.
        * Cons:
            * On EC2 instance termination, `Instance Store` is lost.
            * You can't resize the `Instance Store`.
            * Backups must be operated by user.
    * Overall, EBS-backed EC2 instances are good and should fir most applications workloads.
- **EBS - Important Points:**
    * EBS can be attached to only one EC2 instance at a time.
    * EBS are locked at the AZ (Availability Zone) level.
    * Migrating an EBS volume across AZ means first backing it up (snapshot), then recreating it in the other AZ.
    * EBS backups (snapshot) use IO and you shouldn't perform a `snapshot` operation while your application is handling a lot of traffic.
    * Root EBS volumes of EC2 instances get terminated by default if the EC2 instance gets termiated. **This can be disabled**.

### Route 53
- Route 53 is a DNS (Domain Name System) management facility.
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
- In AWS, the most common records are:
    * `A Record`: URL to IPv4.
    * `AAAA Record`: URL to IPv6.
    * `CNAME Record`: URL to URL.
    * `Alias Record`: URL to AWS Resource.
- Route 53 can use:
    * Public domain names you own (or buy). For e.g. adiinviter.com
    * Private domain names that can be resolved by your EC2 instances in your VPCs. For e.g. `adiinviter.internal`
- Route 53 has some advanced features such as:
    * Load balancing through DNS. Also called `Client Load Balancing`.
    * Health checks (Although limited).
    * Routing policies:
        * Simple
        * Failover
        * Geolocation
        * Geoproximity
        * Latency
        * Weighted
- Prefer **Alias** over **CNAME** for AWS resources (For good performance).

### RDS - Relational Database Service
- RDS uses SQL query language.
- RDS allows us to create following types of databases in cloud:
    * Postgres
    * Oracle
    * MySQL
    * MariaDB
    * MSSQL (Microsoft SQL Server)
    * Aurora (AWS Proprietary Database)
- **Why use RDS** instead of installing DB software directly on EC2 instance:
    * RDS is a managed service. It is manged by AWS. AWS RDS offers following features:
        * OS patching level.
        * Continuous backup and restore to specific timestamp (`Point In Time Restore`).
        * Monitoring Dashboard.
        * `Read Replicas` for improved read performance.
        * Multi `AZ` (Availability Zones) setup for `DR` (Disaster Recovery).
        * Maintenance windows for upgrades.
        * Scaling capability (vertical & horizontal).
        * **Only Con:** You can't SSH into your RDS instances.
- **Read Scalability** setup - RDS Read Replicas:
    * Up to 5 `Read Replicas`.
    * They can be created:
        * Within AZ `(Availability Zone)`.
        * Cross AZ `(Availability Zone)`.
        * Cross Region.
    * Replication is `ASYNC`, so reads are eventually consistent.
    * Replicas can be promoted to their own DB.
    * Applications must use appropriate connection strings to use read replicas.
        * For e.g. In PHP Laravel, we can setup connection strings for:
            * Master
            * Slave 1
            * Slave 2
    * In this setup, only `Master` takes read and write operations and `Read Replicas` are used only for read operations.
    * `Master` performs replication of data in `ASYNC` manner.
- **Disaster Recovery** setup - Multi AZ (`Availability Zone`):
    * **NOT USED FOR SCALING!**
    * `Master` performs replication in `SYNC` manner into `Standby Replica (Slave)`.
    * `One DNS Name` - Automatic App Failover To `Standby Replica (Slave)`. i.e. If a `Master Replica` fails, `Standby Replica (Slave)` will be converted to `Master Replica`.
    * **Not used for READ SCALIBILITY!**
    * **Multi AZ setup is used to increase AVAILABILITY**.
    * Complete failover in case of:
        * Loss of AZ.
        * Loss of network.
        * Instance failure.
        * Storage failure.
* We can use combination of Read Scalability and Disaster Recovery setup.
- **RDS Backups:**
    * Backups are automatically enabled in RDS.
    * Automated backups offer:
        * Daily full snapshot of the database.
        * Capture transaction logs in real time.
        * Ability to restore to any point in time.
        * Backups are retained for 7 days by default (Can be increased to 35 days).
- **DB Snapshots:**
    * These are not automatic. These are manually triggered by user.
    * Snapshots are retained as long as you want.
- **RDS Encryption:**
    * Encryption is at rest (everywhere).
    * Uses `AWS KMS (Key Management Service) - AES-256` encryption.
    * SSL certificates can be used to encrypt data on the fly.
    * To **Enforce SSL:**
        * PostgreSQL: In AWS RDS console (`Parameters Group`) run following:
            ```
            rds.force_ssl = 1
            ```
        * MySQL: Execute following query within the DB:
            ```
            GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;
            ```
    * To **Connect Using SSL** to DB:
        * Provide the SSL Trust Certificate (Can be downloaded from AWS).
        * Provide SSL options while connecting to database.
- **RDS Security:**
    * RDS databases are usually deployed within a private subnet, not in a public one.
    * RDS security works by leveraing the `Security Groups` (Same concept as for EC2 instances).
        * It controls who can communicate with RDS.
    * `IAM (Identity And Access Management) Policies` help control who can manage AWS RDS.
    * Traditional username and password can be used to login to the database.
    * **New:** IAM users can now be used too for MySQL and Aurora.
- **RDS vs. Aurora:**
    * Aurora is a proprietary technology from AWS.
    * `Postgres` and `MySQL` are both supported as `Aurora DB`. i.e. Our Postgres and MySQL drivers will work as if they are `Aurora DB`.
    * Aurora is `AWS Cloud Optimized` and claims:
        * 5x performance improvement over `MySQL on RDS`.
        * 3x performance improvement over `Postgres on RDS`.
    * Aurora storage automatically grows in increments of 10GB. Up to 64TB.
    * Aurora can have 15 replicas while MySQL can have 5.
    * Replication is very fast on Aurora Replicas.
    * Failover in Aurora is instantanious. Its **HA Native** (`Highly Available`).
    * Aurora costs more than RDS (Almost 20% more).
    * Overall, Aurora is more efficient.

### ElastiCache
- `ElastiCache` is like RDS for caches.
- `ElastiCache` is an AWS managed service for:
    * Redis
    * Memcached
- They help make your application `Stateless`.
- `Caches` are in-memory databases with really high performance and super low latency.
- They help reduce load off of databases for read intensive workloads.
- They provide `Write Scaling` using `Sharding`.
- They provide `Read Scaling` using `Read Replicas`.
- They are `Multi AZ (Availability Zone)` with `Failover Capability`.
- AWS takes care of:
    * OS Maintenance.
    * Patching.
    * Optimizations.
    * Setup.
    * Configuration.
    * Monitoring.
    * Failure Recovery.
    * Backups.
- Sample workflow:
    * Application queries `ElastiCache` for data.
    * If the data is available in `ElastiCache`, read from there.
    * If the data is not available in `ElastiCache` then query RDS, store in `ElastiCache` and read further.
- `ElastiCache` helps relieve load in RDS.
- `ElastiCache` must have an `Invalidation Strategy` to make sure only the most current data is stored in there.
- **Redis:**
    * `Redis` is an `in-memory key-value store`.
    * Super low latency (sub ms).
    * Redis cache survives reboots `by default` (it's called `persistence`).
    * Great to host:
        * User Sessions.
        * Leaderboard Data (For Gaming).
        * Distributed States.
        * Relieve pressure on databases (such as RDS).
        * `Pub/Sub` capability for messaging.
    * `Multi AZ (Availability Zone)` with `Automatic Failover` for disaster recovery.
    * Have support for `Read Replicas`.
- **Memcached:**
    * `Memcached` is an `in-memory object store`.
    * Cache doesn't survive reboots.
    * Use cases:
        * Quick retrieval of objects from memory.
        * Cache often accessed objects.
- Overall, `Redis` is largely popular than `Memcached` and provides way better features.
- For caching needs, always try to go for `Redis`.

### VPC - Virtual Private Cloud And 3 Tier Architecture
- `VPC (Virtual Private Cloud)` is created within a `Region`.
- Each `VPC` contains `subnets` (networks).
- Each subnet must be mapped to an **AZ**.
- It's common to have public subnet (Public IP) in VPC.
- It's common to have private subnet (Private IP) in VPC.
- It's common to have many subnets per `AZ`.
- **Public and Private subnets can communicate if they're in the same `VPC (Virtual Private Cloud)`.**
- **Public Subnets** usually cointains:
    * Load Balancers.
    * Static Websites.
    * Files.
    * Public Authentication Layers.
- **Private Subnets** usually cointains:
    * Web Application Servers.
    * Databases.
    * ElastiCache.
- **VPC Important Points:**
    * VPC are `Per Account Per Region`.
    * Subnets are `Per VPC Per AZ (Availability Zone)`.
    * All new AWS accounts come with a default VPC.
    * It's possible to use a VPN to connect to a VPC and access all the private IPs straight from our laptop.
    * `VPC Flow Logs` allows us to monitor the traffic within, in and out of our VPC. This is useful for security, performance and audit etc.
    * Some AWS resources can be deployed in VPC while others can't.
    * We can peer VPC (Within or across different AWS accounts) to make it look like they're part of the same network.
- **Example Of 3 Tier Architecture Application:**
    1. User visits a URL in his browser.
    2. `Amazon Route 53` routes this request to `ELB (Elastic Load Balancer)`. ELB is in `Public Subnet`.
    3. Then suppose in `Private Subnet` we have `ASG (Auto Scaling Group)` setup in 2 different `AZ (Availability Zone)` and there are EC2 instances running in our ASG. The ELB will point this request furhter to EC2 instance.
    4. EC2 instance will communicate with `ElastiCache` (Setup in `Private Subnet`) and try to read data from there.
    5. If the data is not found on `ElastiCache`, EC2 instance will try to query data from `RDS` (Setup in `Private Subnet`). Once the data is retrieved from RDS, EC2 instance will store it in `ElastiCache` and use it further.

### S3 - Buckets And Objects
- Amazon S3 is a **Global Service**.
- Amazon S3 allows people to store `Objects` (files) in `Buckets` (directories).
- **There is no concept of directories in S3 buckets.** It's just buckets separated by slash (/) in any object key.
- **Buckets:**
    * `Buckets` must have globally unique names.
    * `Buckets` are defined at the `Region Level`.
    * Bucket Naming Convention:
        * No Uppercase.
        * No Underscore.
        * 3-63 Characters long.
        * Not and IP.
        * Must start with lowercase letter or number.
- **Objects (Files):**
    * `Objects` have a `Key` and the `Key` is the `Full Path`. For e.g.
        ```
        <my_bucket>/my_file.txt
        <my_bucket>/folder1/folder2/my_file.txt
        ```
    * `Object Values` are the content of the body:
        * Max `Object` (file) size `5TB`.
        * `Objects` (files) greater than `5GB` in size cannot be uploaded to S3 Bucket unless we use `multi-part upload`.
    * Objects can have `Metadata`. Metadata is nothing but a list of `Text Key/Value Pairs` (System or User metadata).
    * Objects can have `Tags`. Tags are nothing but `Unicode Key/Value Pairs (Up to 10)`. They are useful for `Security and Lifecycle`.
    * Objects can have `Version ID` (If versioning is `enabled`).

### S3 - Versioning
- We can version our files in AWS S3.
- `Versioning` is enabled at the **Bucket Level**.
- With every overwrite of file, it will increment the version.
- It is best practice to version your buckets. Following are the main benefits:
    * Protect against unintended deletes (Ability to restore a version).
    * Easy roll back to previous version.
- **Only downside** of having `Versioning` is that you use just a little more space on your Amazon S3.
- Any `Object` (File) that is not versioned prior to enabling versioning will have version **`null`**.

### S3 - Encryption For Objects
- There are 4 methods of encrypting objects in S3:
    * `SSE-S3`: Encrypts S3 objects using keys handled and managed by AWS.
    * `SSE-KMS`: Leverage `AWS KMS (Key Management Service)` to manage encryption keys.
    * `SSE-C`: When you want to manage your own encryption keys.
    * `Client Side Encryption`.
- #### SSE-S3:
    * Encryption using keys handled & managed by `AWS S3`.
    * Object is encrypted server side.
    * AES-256 encryption type.
    * To use `SSE-S3`, set following request header while sending file to S3 bucket:
        ```
        "x-amz-server-side-encryption":"AES256"
        ```
- #### SSE-KMS:
    * Encryption using keys handled & managed by `KMS (Key Management Service) Customer Master Key (CMK)`.
    * Object is encrypted server side.
    * KMS Advantages: User Control + Audit Trail.
    * To use `SSE-KMS`, set following request header while sending file to S3 bucket:
        ```
        "x-amz-server-side-encryption":"aws:kms"
        ```
- #### SSE-C:
    * Encryption using data keys fully managed by the customer (you) outside of AWS.
    * Object is encrypted server side.
    * Amazon will not store the encryption key you provide.
    * **HTTPS must be used.**
    * For every HTTP request made, encryption key must be provided in headers.
- #### Client Side Encryption:
    * Client library such as the `Amazon S3 Encryption Client` should be used.
    * Clients must `encrypt` data themselves before sending to S3.
    * Clients must `decrypt` data themselves when retrieving from S3.
    * The entire Encryption-Decryption cycle and data keys are managed by customers (Not AWS).
- #### Encryption in transit/fligh (SSL/TLS):
    * Encryption in flight/transit is also called `SSL/TLS`.
    * AWS S3 exposes:
        * `HTTP` endpoint: Non Encrypted.
        * `HTTPS` endpoint: Encryption In Flight.
    * You are free to use the endpoint you want (HTTP or HTTPS) , but **HTTPS is recommended**.
    * **HTTPS is mandatory for SSE-C.**

### S3 - Security And Bucket Policies
- Types of S3 Security:
    * User Based:
        * `IAM Policies`: These policies define which API calls should be allowed for a specific user from IAM console.
    * Resource Based: These are popular
        * `Bucket Policies`: These are very popular. `Bucket Policies` are bucket wide rules set from the S3 console. Allows cross account.
        * `Object ACL (Access Control List)`: These are finer grain.
        * `Bucket ACL (Access Control List)`: These are less common.
- **S3 Bucket Policies:**
    * `JSON` based policies. Bucket Policy has 4 major elements:
        * `Resources`: Buckets and objects.
        * `Actions`: Set of APIs to `Allow` or `Deny`.
        * `Effect`: Allow/Deny.
        * `Principal`: The account or user to apply the policy to.
    * **Why Use S3 Bucket Policies:**
        * To grant public access to the bucket.
        * To force objects to be encrypted at upload.
        * To grant access to another account (`Cross Account`).
- **S3 Security: Important Points**
    * Networking:
        * S3 supports `VPC Endpoints` (For EC2 instances running in VPC without internet access).
    * Logging And Audit:
        * S3 access logs can be stored in other S3 bucket. Never store access logs in same bucket where we are storing our application objects.
        * API calls can be logged in `AWS CloudTrail`.
    * User Security:
        * `MFA (Multi Factor Authentication)` can be required in versioned buckets to delete objects.
        * `Signed URLs` are URLs that are valid only for a limited time (for e.g. Premium video service for logged in users).

### S3 - Websites
- S3 can host static websites and have them accessible on the www.
- The website URL will be:
    * > \<bucket-name>.**s3-website-**<AWS-region>.amazonaws.com
    * **OR**
    * > \<bucket-name>.**s3-website.**<AWS-region>.amazonaws.com
- If you get a `403 (Forbidden)` error, make sure the bucket policy allows public reads.

### S3 - CORS
- `CORS` stands for `Cross Origin Resource Sharing`.
- If you request data from another S3 bucket, you need to enable `CORS`.
- `CORS` allows you to limit the number of websites that can request your files in S3 (and limit your costs).
- `CORS` is handled by following header:
    ```
    Access-Control-Allow-Origin: <domain>
    ```

### S3 - Consistency Model
- `Read After Write Consistency` for `PUTS` of new objects:
    * As soon as an object is written, we can retrieve it. (For e.g. `PUT 200 --> GET 200`).
    * This is true, **except** if we did a `GET` before to see if the object existed. (For e.g. `GET 404 --> PUT 200 --> GET 404`) - `Eventually Consistent`.
- `Eventual Consistency` for `DELETES` and `PUTS` of existing objects:
    * If we read an object after updating, we might get the older version. (For e.g. `PUT 200 --> PUT 200 --> GET 200`) - Might be older version.
    * If we delete an object, we might still be able to retrieve it for a short time. (For e.g. `DELETE 200 --> GET 200`) - We might still retrieve an object.
- **In short:**
    * `Read After Write Consistency` for **PUTS**:
        * Write (no prior read operation) and then read operation will always give us new object copy.
        * If object doesn't exists already, `Read Operation` then `Write Operation` and then `Read Operation`might give us `404` because it takes time for S3 to update it's cache and first `Read Operation` response might be received from cache in this situation.
    * `Eventual Consistency` for **DELETES** and **PUTS**:
        * `PUTS`: Even though object has been overwritten, we might still retrieve an old copy of object.
        * `DELETES`: Even though object has been deleted, we might retrieve a copy of object for short time.

### S3 - Performance
- **Old Times:**
    - When you had > 100 TPS (Transaction per second), S3 performance could degrade.
    - Behind the scene, each object goes to an S3 partition and for the best performace, we want the highest partition distribution.
    - It was recommended to have random characters in front of your key name to optimize performance. For e.g.
        * >\<my_bucket>/**7i4p**_my_folder/my_file1.txt
        * >\<my_bucket>/**2k5t**_my_folder/my_file2.txt
        * **Never use dates** to prefix keys. For e.g.:
            * >\<my_bucket>/**2019_12_05**_my_folder/my_file1.txt
- **Current Times:**
    - As of July 17th, 2018, we can scale up to 3500 RPS (Requests Per Second) for **PUT** and 5500 RPS for **GET** for `EACH PREFIX`.
    - This request rate performace increase removes any guidance to put randomized characters in keys etc. from old times (Refer above).
- Use `Multipart Upload` for faster upload of large objects (>5GB). `Multipart Upload` provides:
    * Parallel `PUTs` for greater throughput.
    * Maximize network bandwidth.
    * Decrease time to retry in case a part fails.
- Use `CloudFront` to cache S3 objects around the world (improves reads).
- `S3 Transfer Acceleration`: If you are geo located far away from where your bucket is geo located, you might experice slow uploads. This is where `S3 Transfer Acceleration` service comes into picture. It uses `edge locations`. To use this service, no code changes are required. Only need to change the S3 bucket endpoint where you write to.
- If using `SSE-KMS` encryption you may see a **performance decrease**. With `SSE-KMS` encryption, you may be limited to your AWS limits for KMS (Key Management Service) usage (~100 - 1000 downloads/uploads per second.

### IAM Roles
- IAM Roles can be attached to EC2 instances.
- IAM Roles can come with a policy authorizing exactly what the EC2 instance should be able to do.
- An EC2 instance can have one IAM Role at a time.
- `IAM Policies` can be attached to `IAM Roles`.
- With the set of strong and specific `IAM Policies` attached to `IAM Roles`, we can achieve a much secured setup.
- The only way to test the `IAM Policy` is to use the `Policy Simulator` or `--dry-run` option.

### AWS CLI Dry Runs
- Some AWS CLI Commands (**Not All**) contain a `--dry-run` option to simulate API calls.

### AWS CLI STS Decode Errors
- When you run API calls and they fail, you will get a long error message (big ass characters string).
- This character string can be decoded using the `STS Command Line`. Following is a command to do so:
    ```
    aws sts decode-authorization-message --encoded-message <MESSAGE_STRING>
    ```
- `STS Command Line` is used to decode `Encoded authorization failure message`.

### EC2 Instance Metadata
- It allows EC2 instances to `learn about themselves` **without using an IAM Role for that purpose**.
- The URL is `http://169.254.169.254/latest/meta-data`
    * `169.254.169.254` is an internal ip to AWS.
    * This URL will not work from our computer directly.
    * This URL **Only Works** from our EC2 instances.
    * Using this URL, you can retrieve the `IAM Role Name` from metadata but you cannot retrieve the `IAM Policy`.
    * You cannot retrieve the contents of `IAM Policy` using this URL.
    * **Metadata:** Info about the EC2 instance.
    * **Userdata:** Launch script of the EC2 instance.
- Visting `http://169.254.169.254/latest/` yields following:
    ```
    dynamic
    meta-data
    user-data
    ```
- We can visit trailing APIs in above structure to retrieve various information about the EC2 instance.
- To visit above URL from our EC2 instance using CURL, run following command:
    ```
    curl http://169.254.169.254/latest/meta-data
    ```

### AWS SDK
- AWS SDK is used to perform actions on AWS directly from your applications code (without using the CLI).
- For e.g. when coding against `DynamoDB`, we have to use AWS SDK.
- The AWS CLI uses `Python SDK (boto3)`.
- By default `us-east-1` will be used as a `Default Region` if we do not specify or configure one.
- **SDK Credentials Security:**
    * It is recommended to use `default credential provider chain`.
    * The `default credential provider chain` works seamlessly with:
        * AWS credentials stored in file at `~/.aws/credentials` (Only on your computer or premise).
        * `Instance Profile Credentials` using `IAM Roles` (for EC2 machines etc..)
        * `Environment Variables` such as: **AWS_ACCESS_KEY_ID**, **AWS_SECRET_ACCESS_KEY**.
            * In Laravel application, we set these 2 in `/config/app.php`.
            * This method is not recommended but still widely used.
- **Never EVER EVER** store `AWS Credentials` in your code.
- **Best Practices:**
    * `AWS Credentials` should be inherited from mechanisms above (Except setting them in `Environment Variables`).
    * **100% IAM Roles** if working from within AWS Services.
- **Exponential Backoff:**
    * Any API call that fails because of too many calls needs to be retried with `Exponential Backoff`.
    * These apply to `Rate Limited APIs`.
    * It simply means - If our API call fails, it will wait twice as long as previous API call to try again (Exponential Time Complexity).
    * Retry mechanisms are included in SDK API Calls.

### AWS CLI Profiles
- To create multiple profiles with dfferent AWS credentials, use below command and follow the on screen instructions:
    ```
    aws configure --profile <PROFILE-NAME>
    ```
- Almost every AWS command has `--profile` flag.
    * For e.g. To list S3 buckets for a profile, execute following command:
        ```
        aws s3 ls --profile <PROFILE-NAME>
        ```

### Elastic Beanstalk
- `Elastic Beanstalk` is developer centric view of deploying an application on AWS.
- It uses all the components like EC2, ASG, ELB, RDS etc..
- Beanstalk is **Free** but you **pay for only the underlying resources**.
- Features:
    * It's a managed service by AWS.
    * Instance Configuration, OS is handled by the Beanstalk.
    * Deployment strategy is fully configurable but managed by Beanstalk.
    * Just the application code is the responsibility of the developer.
- It has:
    * Three Architecture Models:
        * `Single Instance Deployment` - Good for `DEV` environment.
        * `LB + ASG` - Good for `Prod` and `Pre-Prod` environments (for e.g. Web Apps).
        * `ASG Only` - Good for Non-Web Apps in `Production` environment (for e.g. Worker etc).
    * Three Components:
        * Application.
        * Application Version: Each deployment gets assigned a version.
        * Environment Name: Free naming (for e.g. Dev, Test, Prod etc..)
- You deploy application versions to environments and can promote application versions to next environments.
- Provides `Rollback` feature to previous application version.
- It gives full control over the lifecycle of environments.
- If your platform is not supported by Elastic Beanstalk, you can write your custom platform (Advanced).

### Elastic Beanstalk Deployment
- Deployment Modes:
    - `Single Instance`: Great for `Dev` environment.
    - `High Availability With Load Balancer`: Great for `Prod`, `Pre-Prod` environments.
- Update Options:
    - **All At Once (Deploy All In One Go):** Fastest, but instances aren't available to serve traffic for a bit (downtime) while codebase is being updated on those EC2 instances.
        * Fastest deployment.
        * Application has downtime.
        * Great for quick iterations in development environment.
        * No additional cost.`
    - **Rolling:** Update a few instances at a time (bucket), and then move onto the next bucket once the first bucket is healthy and updated.
        * Long deployment time.
        * Application is running below capacity.
        * Can set the bucket size.
        * Application is running both versions simultaneously.
        * No additional cost.
    - **Rolling With Additional Batches:** Like `Rolling`, but spins up new instances to move the batch (so that the old application is still available to serve traffic).
        * Long deployment time.
        * Application is running at capacity.
        * Can set the bucket size.
        * Application is running both versions simultaneously.
        * Additional batch is removed at the end of deployment.
        * **Good for Prod**.
        * Small additional cost.
    - **Immutable:** Spins up new instances in a new `ASG (Auto Scaling Group)`, deploys version to these instances, and then swaps all the instances (swap out whole `ASG` with a new one) when everything is healthy and updated.
        * Long deployment time.
        * **Zero Downtime.**
        * A new (temporary) `ASG (Auto Scaling Group)` is created this kind of deployment.
        * New codebase is deployed on EC2 instances running on temporary ASG.
        * **High Cost, Double Capacity.**
        * Quick rollback is available in case of failures (Just terminate the entire new (temporary) `ASG`).
        * **Great for Prod**.
    - **Blue/Green:** `Not a direct feature` of Elastic Beanstalk. Very manual to do.
        * Zero downtime and release facility.
        * Create a new `Stage` environment and deploy new codebase there.
        * The new environment (green) can be validated independently and roll back if issues.
        * Route 53 can be setup using weighted policies to redirect a little bit of traffic to the stage environment.
        * Using Beanstalk, `Swap URLs` when done with the environment test.

### Elastic Beanstalk Advanced Concepts
- Whenever deploying code on Elastic Beanstalk, a codebase must be zipped and this zip will get deployed to Elastic Beanstalk.
- All the parameters configured in AWS UI can be configured with code using files.
- Requirements (Elastic Beanstalk Extension Files):
    * `EB` extension configuration files reside under `.ebextensions/` directory created at the root of source code.
    * Files under `.ebextensions/` directory are in `YAML` or `JSON` format.
    * Files under `.ebextensions/` directory ends with `.config` extension. For e.g. `logging.config`.
    * Default settings can be modified using `option_settings` options.
    * Ability to configure and add resources such as RDS, ElastiCache, DynamoDB etc..
    * Resources managed by `.ebextensions` **get deleted** if the environment goes away.
- We can install an additional CLI called the **EB CLI** which makes working with Beanstalk from the CLI easier.
    * Why would you use `EB CLI`:
        - It's helpful for your automated deployment pipelines.
    * Following are some of the basic commands available in `EB CLI`:
        - `eb create`: Used to create ElastiCache Beanstalk environment.
        - `eb status`: To check ElastiCache Beanstalk status.
        - `eb health`: To check ElastiCache Beanstalk health.
        - `eb events`: To see events.
        - `eb logs`: To view logs.
        - `eb open`: Opens the public URL of your website in the default browser.
        - `eb deploy`: Deploys the application source bundle from the initialized project directory to the running application.
        - `eb config`: To change ElastiCache Beanstalk environment configuration settings.
        - `eb terminate`: To terminal ElastiCache Beanstalk environment.

### Elastic Beanstalk Important Points
- Under the hood, Elastic Beanstalk relies on **CloudFormation**.
- Uses **CodeDeploy** under the hood.
- How Elastic Beanstalk deployment works:
    - Project dependencies are specified in project specific dependency files. For e.g.
        * For `PHP` project using `composer`, we specify dependencies under `composer.json`.
        * For `Node` project, dependencies are specified under `package.json`.
        * For `Python` project, dependencies are specified under `requirements.txt`.
    - Project source code is zipped.
    - This zip will will get deployed and expanded to each EC2 instance.
    - Each EC2 machine will resolve/install dependencies of source code. For e.g. For `Node` project, dependencies will be installed from `package.json`.
        * **This process is pretty slow depending on the number and size of dependencies.**
        * **For Optimization:** We can package/zip required dependencies with project source code itself.

### CICD - Continuous Integration And Continuous Deployment Intro
- CICD is all about automating the deployment while adding increased safety.
- Key aspects of CICD:
    * `AWS CodeCommit`: For storing our code.
    * `AWS CodePipeline`: For automating our pipeline from code to Elastic Beanstalk.
    * `AWS CodeBuild`: For building and testing our code.
    * `AWS CodeDeploy`: For deploying source code to EC2 fleets (**Not Beanstalk**).
- **Continuous Integration:**
    * It simply means developers can push their to a code repository very often (Code Repository e.g. `GitHub`, `CodeCommit`, `Bitbucket` etc.)
    * As soon as the code is pushed into repository, a `Testing` or `Build` server gets the code from repository and `Test/Build` it. For this, `CodeBuild`, `Jenkins CI` etc. can be used from open source world.
    * After this, developer gets feedback about the tests and checks that have passed/failed.
    * **Continuous Integration Goals:**
        - Find bugs early and fix 'em.
        - Offers faster delivery as the code is tested.
        - Offers developers to deploy codes very often.
        - Makes developers happy as they're unblocked.
- **Continuous Delivery:**
    * It usually means `Automated Deployment`. Deployments can be automated using tools such as:
        - `CodeDeploy`.
        - `Jenkins CD`.
        - `Spinnaker`.
    * Ensures that the software can be released reliably whenever needed.
    * Ensures that deployments happen often and are quick.
    * If your company had `1 Release Every 3 Months` policy before, then with `Continuous Delivery` you can achieve `5 Releases a day` easily.
- **Technology Stack For CICD (`Continuous Integration And Continuous Deployment`)**
    - Code Repository:
        * AWS `CodeCommit`.
        * `GitHub`.
        * Or any 3rd party code repository.
    - Code Build And Test:
        * AWS `CodeBuild`.
        * `Jenkins CI`.
        * Or any 3rd party CI servers.
    - Code Deploy And Provision:
        * AWS `Elastic Beanstalk`.
        * AWS `CodeDeploy` to deploy on user managed EC2 instances `Fleet` (CloudFormation).
- AWS **CodePipeline** is used to orchestrate/perform all above. i.e.:
    * Code.
    * Build.
    * Test.
    * Deploy.
    * Provision.

### CodeCommit
- **Version Control** is the ability to understand the various changes that happened to the code over time (and possibly roll back).
- All these are enabled by using a version control system such as `Git`.
- A `Git` repository can live on one's machine, but it usually lives on a central online repository.
- Benefits of using a version control system are:
    * Collaborate with multiple developers.
    * Make sure the code is backed-up somewhere.
    * Make sure it's fully viewable and auditable.
- **Why Choose CodeCommit:**
    * `Git` repositories can be expensive. Free public repositories, but private repositories is a paid feature.
    * AWS `CodeCommit`:
        - Private `Git` repositories (At low costs).
        - No size limit on repositories (scale seamlessly).
        - Fully managed, highly available.
        - Source code resides only in `AWS Cloud Account`. Because of this, it provides security and compliance.
        - Secure (has encryption, access control etc.)
        - Integrated with `Jenkins`/`CodeBuild`/Other CI tools.
- **CodeCommit Security:**
    * Since they are `Git` repositories, interactions are done using `Git` (standard).
    * When you `Authenticate` in `Git`,
        - You have `SSH Keys`: AWS Users can configure SSH keys in their `IAM Console`.
        - Or you can use `HTTPS`: Done through the `AWS CLI Authentication Helper` or by `Generating HTTPS Credentials`.
        - If you want **really extra** security, you can enable `MFA (Multi Factor Authentication)`.
    * **Authorization in Git:**
        - `IAM Policies` manage user/roles rights to repositories.
    * **Encryption:**
        - Repositories are automatically encrypted at rest using `KMS (Key Management Service)`.
        - Encrypted in trasit (Since we can only use `HTTPS` or `SSH Keys` - both are secured).
    * **Cross Account Access:**
        - Do not ever share your AWS credentials.
        - Do not ever share your SSH keys.
        - Use `IAM Role` in your AWS Account and use `AWS STS (with AssumeRole API)`. `AssumeRole` is a cross-account access role api.
- **CodeCommit vs GitHub:**
    - **Similarities:**
        * Both are `Git` repositories.
        * Both support code review `Pull Requests`.
        * Both can be integrated with AWS `CodeBuild`.
        * Both support `HTTPS` and `SSH` authentication methods.
    - **Differences:**
        * Security:
            - `GitHub` is administered through `GitHub Users` system.
            - `CodeCommit` uses `AWS IAM Users & Roles`.
        * Hosting:
            - `GitHub`: Codebase is hosted by `GitHub`.
            - `GitHub Enterprise`: Self hosted on your servers.
            - `CodeCommit`: Managed and hosted by AWS.
        * UI:
            - `GitHub`: GitHub is a clear winner. UI is fully featured.
            - `CodeCommit`: UI is minimal.
- **CodeCommit Notifications:**
    * `CodeCommit` can integrate and trigger notifications using `AWS SNS (Simple Notification Service)` or `AWS Lambda` or `AWS CloudWatch Event Rules`.
    * Use cases for `SNS` / `AWS Lambda Notifications`: Examples when notifications can be triggered
        - Deletion of branches.
        - Trigger notifications pushes on to master branch.
        - Trigger notifications to `External Build System`.
        - Trigger AWS `Lambda function` to perform codebase analysis.
            * For e.g. Analyze codebase to see if developer have used AWS credentials in codes and are those committed in the codes. Trigger notification if done so etc.
    * Use cases for `CloudWatch Event Rules`:
        - Trigger notifications for `Pull Request Updates`:
            * Created.
            * Updated.
            * Deleted.
            * Commented.
        - Trigger notifications when someone comments on `Commit`.
        - `CloudWatch Event Rules` goes into an `SNS (Simple Notification System) Topic`. i.e. `CloudWatch Event Rules` triggers notification into `SNS Topic`.

### CodePipeline
- `CodePipeline` is nothing but a visual tool to perform `Continuous Delivery`.
- `CodePipeline` is made of stages:
    * Each stage can have sequential actions and /or parallel actions.
     - Stages example: Build / Test/ Deploy / Load Test / etc..
    * Manual approval can be defined at any stage.
- Pipeline works with `Artifacts`.
    * `Artifacts` are nothing but bunch of files that are passed and stored through in `Amazon S3` and passed on to the next stage.
    * Each pipeline stage can create `Artifacts`.
- **CodePipeline Troubleshooting:**
    * Whenever there is a state change in a pipeline (For e.g. New code committed/pushed), it will generate an `AWS CloudWatch Event`, which can in return create `SNS` notfication.
        - For e.g. You can create events for failed pipelines.
        - For e.g. You can create events for cancelled stages.
    * If `CodePipeline fails` a stage then your pipeline will stop and you will get information in the console.
    * `AWS CloudTrail` can be used to audir `AWS API` calls.
    * If pipeline can't perform an action, make sure the `IAM Service Role` attached does have enough permissions (`IAM Policy`).
        - For e.g. Pipeline is not able to deploy to `AWS Elastic Beanstalk`. In this case, make sure that your policy is not incorrect or incomplete.

### CodeBuild
- `CodeBuild` is a fully AWS managed `build service`. Alternative to `CodeBuild` is `Jenkins` but it is not as powerfull as `CodeBuild`.
- `CodeBuild` is a **Continuous Scaling** system. That means you don't have to manage or provision any servers. There is no build queue.
- `CodeBuild` can build code from `GitHub` / `CodeCommit` / `CodePipeline` / `Bitbucket` / `S3` etc.
- You only **Pay For Usage**: i.e. The time it takes to complete the builds.
- Under the hood it uses **Docker** for reproducible builds.
- Using our own `base Docker images`, we can easily extend the capabilities of `CodeBuild`.
- **Security:**
    * Integration with `KMS` for encryption of build artifacts.
    * `IAM` for `Build Permissions`.
    * `VPC` for network security.
    * `CloudTrail` for API calls logging.
- Custom build instructions can be defined in `buildspec.yml` file.
- Output logs to `Amazon S3` and `AWS CloudWatch Logs`.
- AWS provides metrics to monitor `CodeBuild` statistics (Helpful to make sure build doesn't timeout or fail).
- You can use `CloudWatch Alarms` to detect failed builds and trigger notifications.
- You can also use `CloudWatch Events` or `AWS Lambda` as a Glue for everything.
- You have an ability to trigger `SNS Notifications`.
- Ability to reproduce `CodeBuild` locally to troubleshoot in case of errors.
- **Pipelines can be defined within CodePipeline or CodeBuild itself.**
- **CodeBuild `BuildSpec`**:
    * `buildspec.yml` file must be at the root of your code.
    * We can define environment variables inside `buildspec.yml`
        - Plaintext variables.
        - Secure Secrets: Use `SSM Parameter Store`.
    * We can specify commands to run for different phases of `CodeBuild`:
        - **Install**: Install dependencies you may need for your build.
        - **Pre Build**: Commands to execute before build.
        - **Build**: Actual build commands.
        - **Post Build**: Commands to run after build (for e.g. zip output).
    * `Artifacts`: What to upload to S3 (Encrypted with `KMS`).
    * `Cache`: Files to cache (usually dependencies) on S3 for future build speedups.
- **CodeBuild Local Build**:
    * In case of need of deep troubleshooting beyond logs.
    * You can run `CodeBuild` locally on your desktop (after installing `Docker`).
    * For this, we will have to use **CodeBuild Agent**.

### CodeDeploy
- `CodeDeploy` is used to deploy application (automatically) to many EC2 instances.
- It is more powerful than `Elastic Beanstalk`.
- **`CodeDeploy` only deploys application. It does NOT provision resources. It assumes that your EC2 instances are already existing.**
- `CodeDeploy` is an Amazon AWS managed service.
- `CodeDeploy` **is used to deploy codebase on EC2 instances managed by us (EC2 Instances Not Managed By Elastic Beanstalk).**
- Beside `CodeDeploy` there are many Open Source technologies to manage deployment on non Elastic Beanstalk managed EC2 instances:
    * Ansible.
    * Terraform.
    * Chef.
    * Puppet.
    * etc.
- It runs directly from the `AWS Console or Environments`.
- **How `CodeDeploy` works:**
    * Each EC2 machine (or `On Promise` machine) must be running the `CodeDeploy Agent`.
    * The `CodeDeploy Agent` is continuously `polling` **AWS CodeDeploy** for work to do.
    * `AWS CodeDeploy` sends **appspec.yml** file (or at least point to it).
    * Then application source code will be pulled from `GitHub` or `S3`.
    * EC2 will run the deployment instructions.
    * `CodeDeploy Agent` will report of success/failure of deployment on the EC2 instance.
- EC2 instances are grouped by deployment group (dev/test/prod).
- `CodeDeploy` provides lots of flexibility to define any of deployments.
- `CodeDeploy` can be chained into `CodePipeline` and use `Artifacts` from there.
- `CodeDeploy` can re-use existing setup tools (like anything you have on your EC2 machine).
- It works with any kind of application.
- `CodeDeploy` provides seamless auto scaling integration.
- We can do **Blue/Green** deployments but it works only on `EC2 instances` and not `On Promise Instances`.
- It does support `AWS Lambda Deployments`.
- **Primary Components:**
    * `Application`: Unique Name.
    * `Compute Platform`: EC2/On-Promise or Lambda.
    * `Deployment Configuration`: Deployment rules for success/failure.
        - `EC2/On-Promise`: You can specify the minimum number of healthy instances for the deployment.
        - `AWS Lambda`: You can specify how traffic is routed to your updated `Lambda Function` versions.
    * `Deployment Group`: Group of `Tagged Instances` (Allows to deploy gradually).
    * `Deployment Type`: In-place deployment or Blue/green deployment.
    * `IAM Instance Profile`: Need to give EC2 the permissions to pull codebase from `S3/GitHub`.
    * `Application Revision`: Application Code + `appspec.yml` file.
    * `Service Role`: Role for `CodeDeploy` to perform what it needs (What it needs to perform the deployment).
    * `Target Revision`: Target deployment application version.
- **AppSpec (`appspec.yml`) File:**
    * `File Section`: How to source and copy from S3/GitHub to filesystem.
    * `Hooks`: Set of instructions or commands are to be executed to deploy the new version (**Hooks can have timeouts**). Order is very important:
        - `ApplicationStop`: Specifies when to stop the current application that is being run on EC2 instance.
        - `DownloadBundle`: Specifies how to download new application (From S3/GitHub etc.)
        - `BeforeInstall`: Set of commands to run before new aplication is installed.
        - `AfterInstall`: Set of commands to run after the new application is installed. For e.g. May be you wanna do cleanup or launch a server etc.
        - `ApplicationStart`: Specifies how to start new application.
        - **`ValidateService`:** Very Important! Like a `Health Check`. It specifies how to validate newly deployed application version is running properly or not. For e.g. May be visit `status.html` and see if the response code is `200 OK`.
        - `BeforeAllowTraffic (Only in Blue/Green Deployment Type)`: Things to do before traffic is allowed to EC2 instance.
        - `AllowTraffic (Only in Blue/Green Deployment Type)`: Specifies how to allow traffic to EC2 instance. For e.g. May be pull off `Laravel setup from Maintainance Mode to Active`.
        - `AfterAllowTraffic (Only in Blue/Green Deployment Type)`: Things to do once the traffic is allowed to EC2 instance.
- **Deployment Config:**
    * Configs:
        - `One at a time`: One instance at time. If one instance fails --> Entire deployment stops.
        - `Half at a time`: 50%. If 2 or more instances fail --> Entire deployment stops.
        - `All at once`: Quick but no healthy host, no downtime. **Good for dev**. If all instances fail --> Entire deployment stops.
        - `Custom`: For e.g. You can specify minimum healthy host = 75%.
    * Failure: In case of failures:
        - Instances stay in `failed state`.
        - New deployments will first be deployed to `failed state` instances which guarentees you don't bring down your whole application because of a failure.
        - To Rollback: You can re-deploy old deployment or enable automated rollback on failures.
    * Deployment Targets:
        - These can be EC2 instances with tags.
        - Or you can directly deploy to an `ASG (Auto Scaling Group)`.
        - Or you can create `Deployment Segments` which is a mix of `ASG` and `Tags (EC2 Instances)`.
        - For advanced users: You can customize in scripts with `DEPLOYMENT_GROUP_NAME` environment variables.

### CloudFormation - Infrastructure As Code
- `CloudFormation` is a declarative way of outlining your `AWS Infrastructure` for any resources (most of them are supported).
- `CloudFormation` supports `YAML` and `JSON` scripting languages. `JSON` is quite considered horrible for writing `CloudFormation` templates.
- For e.g. Within a `CloudFormation Template`, you say:
    * I want a security group.
    * I want 2 EC2 machines using this security group.
    * I want 2 `Elastic IPs` for these EC2 machines.
    * I want an `S3 Bucket`.
    * I want a load balancer (`ELB`) in front of these EC2 machines.
- Then CloudFormation creates those for you, in the `right/correct order` with the **Exact Configurations** that you specify.
- **Benefits of CloudFormation:**
    * `Infrastructure As Code`:
        - No resources are manually created, which is excellent for control.
        - The code can be version controlled for example using `Git`.
        - All the changes to the infrastructure are reviewed through code.
    * **Cost:**
        - CloudFormation is free, you only pay for the underlying resources.
        - Each resources within stack is `stagged` with an identifier so you can easlity see how much a stack costs you.
        - You can estimate the costs of your resources using the CloudFormation template.
        - Saving Strategy: For e.g. In Dev environment, you could automate the deletion of `Templates` at 5PM and recreate them at 8AM safely.
    * **Productivity:**
        - Ability to destroy and re-create an infrastructure on the cloud on the fly.
        - Automated generation of Diagram for your templates (Quite nice for presentations).
        - Declarative programming (no need to figure out ordering and orchestration).
    * **True Separation Of Concern:** Create many stacks for many apps, and many layers. For e.g.
        - VPC Stacks.
        - Network Stacks.
        - App Stacks.
    * **Don't Re-Invent The Wheel:**
        - Leverage existing `CloudFormation Templates` on the web!
        - Leverage the documentations.
- **How CloudFormation Works:**
    * Templates have to be uploaded in S3 and then referenced in CloudFormation.
    * To update a template, we can't edit previous ones. We have to re-upload a new version of the template to AWS.
    * Stacks are identified by a name.
    * Deleting a stack deletes every single artifact that was created by CloudFormation.
- **How To Create And Deploy CloudFormation Templates:**
    * `Manual Way`:
        - Editing templates in the `CloudFormation Designer`.
        - Using the console to input parameters, etc.
    * `Automated Way`:
        - Editing templates in a YAML file.
        - Using the AWS CLI (Command Line Interface) to create and deploy templates.
        - **This is the recommended way if you want to fully automate the flow.**

### CloudFormation - Template - Resources
- They are **MANDATORY**.
- `Resources` are the core of your `CloudFormation` template.
- They represent the different AWS Components that will be created and configured.
- `Resources` are declared and can reference each other.
- AWS figures out creation, updation and deletion of resources in right order for us.
- There are over 224 types of AWS resources.
- `Resource Identifiers` has the following form:
    ```
    AWS::aws-product-name::data-type-name
    ```
- **FAQ:**
    * Can I create a dynamic amount of resources?
        - **No, You can't!** Everything in the `CloudFormation Template` has to be declared. You can't perform dynamic code generation there.
    * Is every AWS Service supported?
        - **Almost!** Only a select few niches are not there yet.
        - You can work around that using `AWS Lambda Custom Resources`.

### CloudFormation - Template - Parameters
- `Parameters` are way to provide inputs to your `CloudFormation Templates`.
- They are super important to know about if you want to:
    * You want to **re-use** your templates across the company/AWS accounts/Regions.
    * Some inputs cannot be determined ahead of time.
        - For e.g. The key-pair you gonna link to your EC2 instances.
- `Parameters` are extremely powerful, controlled and can prevent errors from happening in your templates. Thanks to `Types`.
- **When to use `Parameters`:**
    * Ask yourself this:
        - Is this `CloudFormation Resource Configuration` likely to change in the future? If so, make it a `Parameter`.
        - By making some configuration a `Parameter`, you won't have to re-upload a `CloudFormation Template` to change it's content.
- **How to use/reference a `Parameter`:**
    * The `Fn::Ref` function can be used to reference a `Parameter`.
    * `Parameters` can be used anywhere in `CloudFormation Template`.
    * The shorthand for this `YAML` is `!Ref`. Instead of shorthand, you can also use `Fn::Ref`.
    * The `Fn::Ref` function can also reference other elements within the `CloudFormation Template`.
- **Pseudo Parameters:**
    * These are offered by AWS and they are available in any `CloudFormation Template`.
    * These can be used any time and are available by default.
    * For e.g.
        - `AWS::AccountId`: Gives the AWS account id. Quite handful if you are trying to construct some `AWS ARN` in your template.
        - `AWS::Region`: Gives the AWS region.
        - `AWS::StackName`: Gives the `AWS CloudFormation Stack Name`.

### CloudFormation - Template - Mappings
- `Mappings` are fixed variables within your `CloudFormation Template`.
- They are very useful to differentiate between different environments (dev, prod etc), AWS Regions, AMI Types etc..
- All `Mapping Values` are hardcoded within your `CloudFormation Template`.
- For e.g.: `YAML``
    ```
    Mappings:
        Mapping01:
            Key01:
                Name: Value01
            Key 02:
                Name: Value 02
            Key 03:
                Name: Value 03
    ```
- **When to use `Mappings`:**
    * When you know all the values that can be taken and that they can deduced from variables such as:
        - `Region`.
        - `Availability Zone`.
        - `AWS Account`.
        - `Environment (e.g. Dev, Prod etc)`.
    * They allow safer control over the `CloudFormation Template`.
    * Use `Parameters` when values are user specific. i.e. when you don't know the value and you want user to input value.
- **How to use/access Mapping Value:**
    * `Fn::FindInMap` function is used to access/use `Mapping Value`.
    * `Fn::FindInMap` is used to return a named value from a specific key.
    * Following is a shorthand for `Fn::FindInMap` function:
        ```
        !FindInMap [ MapName, TopLevelKey, SecondLevelKey ]
        ```

### CloudFormation - Template - Outputs
- The `Outputs` section in `CloudFormation Template` defines `Optional Output` values that we can import into our `Stacks` (If you `Export` them first!)
- You can also view the `Outputs` in `AWS Console` or in using `AWS CLI`.
- They are very useful, for e.g. If you define a `Network CloudFormation` template and output the variables such as `VPC Ids` and your `Subnet Ids`. These Ids can be re-used in your other `CloudFormation Templates`.
- It's a best way to perform `Cross Stack Collaboration`, as you let expert handle their own part of the `CloudFormation Stack`.
- **You can't delete a `CloudFormation Stack` if it's `Output Values` are referenced by another `CloudFormation Stack`.**
- Only values that are specified under **Export**, can be used used as `Output Values`.
- **`Fn::ImportValue`** function is used to reference a cross stack output value.
- You can't delete the underlying stack unless all the references stacks are deleted.
- Shorthand syntax is:
    ```
    !ImportValue
    ```

### CloudFormation - Template - Conditions
- `Conditions` are used to control the creation of resources or to control outputs based on conditionals.
- `Conditions` can be whatever you want them to be, but the common ones are:
    * `Environment`: For e.g. dev/test/prod.
    * `AWS Region`.
    * Any `Parameter Value`.
- Each `Condition` can reference another `Condition`, `Parameter Value` or `Mapping Value`.
- **How to define a condition?**
    * Following codeblock describes: Create producion resources (`CreateProdResources`) only if parameter value of `EnvType` is equals to `prod`.
        ```
        Conditions:
            CreateProdResources: !Equals [ !Ref EnvType, prod ]
        ```
    * The logical Id (`CreateProdResources`) is for you to choose. It's how you name condition.
    * The logical functions can be any of the following:
        - `Fn::And`
        - `Fn::Equals`
        - `Fn::If`
        - `Fn::Not`
        - `Fn::Or`
- **How to use a condition?**
    * Conditions can be applied to resources/outputs/etc..
    * For e.g. Following codeblock will create `AWS::EC2::VolumeAttachment` only if condition `CreateProdResources` is `true`:
        ```
        Resources:
            MountPoint:
                Type: "AWS::EC2::VolumeAttachment"
                Condition: CreateProdResources
        ```
        **Note:** They are at the same level as `Type`.

### CloudFormation - Template - Intrinsic Functions
- Following are some of the important `Intrinsic Functions`:
    * `Ref`
        - It is used to reference the value.
            * If referencing the `Parameter`, then it will return `value` of that `Parameter`.
            * If referencing the `Resource`, then it will return `Physical Id` of the underlying resource. For e.g. `Id of EC2 Instance`.
        - Shorthand in `YAML` is `!Ref`.
        - E.g. `!Ref MyVPC` will return the physical Id of `MyVPC`.
            ```
            DbSubnet1:
                Type: AWS::EC2::Subnet
                Properties:
                    VpcId: !Ref MyVPC
            ```
    * `Fn::GetAtt`
        - It is used to get the `Attribute` value of resources.
        - `Attributes` are attached to any resources you create.
        - To know the attributes of your resources, the best place to look at is the AWS documentation.
        - E.g. To get the `Availability Zone` of EC2 instance:
            ```
            NewVolume:
                Type: "AWS::EC2::Volume"
                Condition: CreateProdResources
                Properties:
                    Size: 100
                    AvailabilityZone:
                        !GetAtt EC2Instance.AvailabilityZone
            ```
    * `Fn::FindInMap`
        - It is used to get the `Mapping Values`.
        - We use `Fn::FindInMap` to return a named value from a specific key.
        - Shorthand in `YAML` is as follows:
            ```
            !FindInMap [ MapName, TopLevelKey, SecondLevelKey ]
            ```
    * `Fn::ImportValue`
        - It is used to import values that are exported in other `CloudFormation Templates`.
    * `Fn::Join`
        - It is used to join values with a delimiter.
        - Syntax:
            ```
            !Join [delimiter, [comma-delimited list of values]]
            ```
        - For e.g. To create following string: `a:b:c`:
            ```
            !Join [":", [a, b, c]]
            ```
    * `Fn::Sub`
        - It is used to substitute variables from a text.
        - It allows you to fully customize your `CloudFormation Templates`.
        - Shorthand in `YAML` is `!Sub`.
        - For e.g. You can combine `Fn::Sub` with `References` or `AWS Pseudo Variables`.
        - `String` must contain `${VariableName}` and will substitute them.
    * Condition Functions:
        - `Fn::And`
        - `Fn::Equals`
        - `Fn::If`
        - `Fn::Not`
        - `Fn::Or`

### CloudFormation - Rollbacks
- When **Stack Creation Fails** in CloudFormation:
    * By `Default`: Everything rolls back (gets deleted). We can look at the logs.
    * When you create a `Stack`, you have option to `Disable Rollback And Troubleshoot` what happened.
- When **Stack Update Fails** in CloudFormation:
    * The stack automatically rolls back to the previous known working state.
    * You also have an ability to see in the logs what happened and error messages.

### AWS Monitoring Intro
- **AWS CloudWatch:**
    * **Metrics:** Collect and track key metrics.
    * **Logs:** Collect, monitor, analyze and store log files.
    * **Events:** Send notifications when certain events happen in your AWS.
    * **Alarms:** React in real-time to metrics/events.
- **AWS X-Ray:**
    * Troubleshooting application performance and errors.
    * Distributed tracing of microservices.
- **AWS CloudTrail:**
    * Internal monitoring of API calls being made.
    * Audit changes to AWS Resources by your users.

### CloudWatch Metrics
- `CloudWatch` provides metrics for **all** services in AWS.
- `Metric` is a variable to monitor (For e.g. In EC2 Instance - `CPUUtilization`, `NetworkIn` etc..)
- Metrics belong to `namespaces`.
- `Dimension` is an attribute of a metric (For e.g. instance id, environment, etc..).
- We can have up to `10 Dimensions` per `Metric`.
- Metrics have `timestamps`.
- Out of metrics we want, we can create `CloudWatch Dashboards`.
- **CloudWatch EC2 Detailed Monitoring:**
    * EC2 instance metrics have metrics `Every 5 Minutes`.
    * With `Detailed Monitoring` (For extra cost), you can get metrics for `Every 1 Minute`.
    * Use `Detailed Monitoring` if you want to more promptly scale your `ASG`.
    * `AWS Free Tier` allows us to have `10 Detailed Monitoring Metrics`.
    * **Note:** EC2 `Memory Usage` is not pushed as a `Metric` by default. It must be pushed from inside the EC2 instance as a `Custom Metric`.
- **CloudWatch Custom Metrics:**
    * It is possible to define and send your own custom metrics to CloudWatch. And they can be whatever you want.
    * Ability to use `Dimensions (Attributes)` to segment metrics. For e.g.
        - `Instance.id`
        - `Environment.name`
    * `Metric Resolution` for `Custom Metrics`:
        - Standard: `1 Minute`.
        - Higher Resolution: If you want, you can get Metric data up to every `1 Second` using `StorageResolution API Parameter`. It is offered at **Higher Cost**.
            * `StorageResolution API Parameter` enables `High Resolution Custom Metric`.
    * To send a Metric Data to CloudWatch `PutMetricData` API call is used.
    * You can use `Exponential Back Off` in case of `Throttle Errors`.

### CloudWatch Alarms
- `Alarms` are used to trigger notifications for any metric.
- Alarms can be attached to `Auto Scaling Groups`, `EC2 Actions`, `SNS Notifications` etc..
- Various options (sampling, %, max, min, etc..)
- **Alarm States:**
    * `OK`
    * `INSUFFICIENT_DATA`
    * `ALARM`: When Alarm threshold is passed.
- **Alarm Period:**
    * Length of time in seconds to evaluate the metric.
    * High Resolution Custom Metrics: Can only choose 10 sec or 30 sec.

### CloudWatch Logs
- Applications can send logs to `CloudWatch` using the SDK.
- `CloudWatch` can collect logs from:
    * Elastic Beanstalk: Collection of logs from application.
    * ECS: Collection from containers.
    * AWS Lambda: Collection from function logs.
    * VPC Flow Logs: VPC specific logs.
    * API Gateway.
    * `CloudTrail` based on filter.
    * `CloudWatch Log Agents`: For e.g. On EC2 machines.
    * `Route53`: Log DNS queries.
- **CloudWatch Logs Can Go To:**
    * Batch exporter to S3 for archival.
    * Stream to `ElasticSearch Cluster` for further analytics.
- `CloudWatch Logs` can use filter expressions.
- **CloudWatch Logs Storage Architecture:**
    * Log Groups: Arbitrary name, usually representing an application.
    * Log Streams: Instances within application/log files/containers.
- Can define log expiration policies (Never Expire, 30 Days, etc..)
- Using `AWS CLI` we can tail the `CloudWatch Logs`.
- To send logs to `CloudWatch`, make sure your `IAM Permissions` are correct.
- **Security:** Encryption of logs using **KMS At Rest** at the `Group Level`.

### CloudWatch Events
- Events can be scheduled using `Cron Jobs`.
- You can also define `Event Pattern` is `CloudWatch Events`: `Event Rules` to react to a service doing something.
    * For e.g: `CodePipeline` state changes!
- Triggers to `Lambda Functions`, `SQS`, `SNS`, `Kinesis Messages` etc..
- `CloudWatch Event` creates a small `JSON` document to give information about the change.

### AWS X-Ray
- AWS X-Ray gives **Visual Analysis** of your application.
- **Advantages:**
    * Troubleshooting performance (bottlenecks).
    * Understand dependencies in a microservice architecture.
    * Pinpoint service issues.
    * Review request behavior.
    * Find errors and exceptions.
    * With `AWS X-Ray`, you can answer questions such as "Are we meeting time SLA in terms of latency or time to process a request etc"?
    * You can find out which service is slowing you down/"Where I am throttled"?
    * You can identify users that are impacted.
- **Compatibility:**
    * AWS Lambda.
    * Elastic Beanstalk.
    * ECS.
    * ELB.
    * API Gateway.
    * EC2 Instances or any application server (even on premise).
- AWS X-Ray **Leverages Tracing**. Tracing is something:
    * Tracing is an end to end way to following a `request`.
    * Each component dealing with the request adds its own `trace`.
    * Tracing is made of segments (+ sub segments).
    * Annotations can be added to traces to provide extra information.
    * **Ability To Trace:**
        - Every request.
        - Sample request (as a % for e.g. or a rate per minute).
    * **X-Ray Security:**
        - `IAM` for authorization.
        - `KMS` for encryption at rest.
- **How to enable AWS X-Ray?**
    * Your code (Java, Python, Go, Node.js, .NET) must import `AWS X-Ray SDK`.
        - Very little code modifications needed.
        - The application SDK will then capture:
            * Calls to AWS services.
            * HTTP/HTTPS requests.
            * Database Calls (MySQL, PostgreSQl, DynamoDB).
            * Queue Calls (SQS).
    * After modifying code, we will have to install the `X-Ray Daemon` or enable `X-Ray AWS Integration`:
        - `X-Ray Daemon` works as a low level UDP packet interceptor (Linux/Windows/Mac etc..)
        - AWS Lambda/Other AWS services already run the `X-Ray Daemon` for you.
        - Each application must have the `IAM` rights to write data to `X-Ray`.

### AWS CloudTrail
- Provides governance, compliance and audit for your AWS account.
- CloudTrail is **Enabled By Default.**
- Get an history of events/API calls made within your AWS account by:
    * Console
    * SDK
    * CLI
    * AWS Services
- Can put logs from CloudTrail into CloudWatch Logs.
- If a resource is deleted in AWS, **look into CloudTrail first!**

### Introduction To Messaging
- When we start deploying multiple applications, they will inevitably need to communicate with one another.
- There are 2 patterns of application communication:
    * Synchronous Communication: **Application To Application**.
    * Asynchronous / Event Based: **Application To Queue To Application**.
- Synchronous communication between applications can be problematic if there are sudden spikes of traffic.
- It's better to **decouple** your applications and scale **decoupled applications** individually.
- Asynchronous communication between applications can be achieved by:
    * `SQS`: Queue model.
    * `SNS`: Pub/Sub model.
    * `Kinesis`: Real-time streaming model.
    * **These services can scale independently from our application.**

### AWS SQS
- SQS stands for `Simple Queue Service`.
- **Types Of Queues:**
    * `Standard Queue`:
        - It is the oldest offering by AWS (Over 10 years old).
        - Fully managed by AWS.
        - Scales from 1 messages per secord to 10000s per second.
        - Default retention of messages: 4 days, maximum of 14 days.
        - No limit to how many messages can be in the queue.
        - Low latency (< 10ms on publish and receive>).
        - Horizontal scaling in terms of number of consumers.
        - Can have duplicate messages (at least one delivery, occasionally).
        - Can have out of order messsages (best effort ordering).
        - Limitation of `256kb` per message sent.
    * `Delay Queue`:
        - Delay a message (Consumers don't see it immediately) up to 15 minutes.
        - Default is 0 seconds (messages are available right away).
        - Can set `Default Delay` at `Queue` level.
        - Can override the `Default Delay` using `DelaySeconds` parameter.
    * `Dead Letter Queue (DLQ)`:
        - In `Standard Queue` and `Delay Queue`:
            * If a consumer fails to process a message within the `Visibility Timeout`, the message goes back to the queue.
            * We can set a threshold of how many times a message can go back to the queue - It's called a **Redrive Policy**.
        - After the threshold (**Redrive Policy**) is exceeded, the message goes into a `Dead Letter Queue (DLQ)`.
        - We have to create a `Dead Letter Queue (DLQ)` first and then designate it a Dead Letter Queue.
        - Make sure to process the messages in `Dead Letter Queue (DLQ)` before they expire.
- **Producing Messages:** Message form:
    * Define message body upto 256kb.
    * Add message attributes (metadata - optional). For e.g. `Name`, `Type`, `Value` etc..
    * Provide Delay Delivery (optional). For e.g. with `DelaySeconds` parameters.
    * After processing message, we get back folling data as a response:
        - Message Identifier.
        - MD5 Hash of the message body.
- **Consuming Messages:**
    * Consumers..
    * Consumers `Poll` SQS for messages (receive up to 10 messages at a time).
    * Consumers have duty to process messages before the `Visibility Timeout`.
    * Once the message is processed, Consumer will tell the SQS to delete the message or when the `Visibility Timeout` is reached, SQS will delete the message using `Message Id` and `Receipt Handle`.
- **SQS - Visibility Timeout:**
    * The length of the time (in seconds) for which a message received from a queue will be invisible to other receiving components.
    * When a consumer polls a message from a queue, the message is `invisible` to other consumers for a defined period. This is what is called a `Visibility Timeout`.
    * Default `Visibility Timeout` is 30 Seconds.
    * You can set any value between 0 Seconds To 12 Hours.
    * If the `Visibility Timeout` is set too high (e.g. 15 minutes) and a consumer fails to process the message, you must wait a long time before processing the message again.
    * If the `Visibility Timeout` is set too low (e.g. 30 seconds) and a consumer needs time to process the message (e.g. 2 minutes), another consumer will receive the message and the message will be processed more than once.
    * **ChangeMessageVisibility API:**
        - If a consumer receives a message and starts processing it, and while processing, consumer figures out it will need more time to process the message, then consumer can change message's `Visibility Timeout` value using `ChangeMessageVisibility API` while processing the message.
    * **DeleteMessage API:**
        - Consumer can use `DeleteMessage API` to tell SQS that the message was successfully processed and you can delete it.
- **SQS - Long Polling:**
    * When a consumer requests message from the queue, it can optionally `wait` for messages to arrive if there are none in the queue. This is called **Long Polling**.
    * `Long Polling` decreases the number of API calls made to SQS while increasing the efficiency and latency of your application.
    * Wait time can be between 1 Second to 20 Seconds (20 Seconds Preferable).
    * **Long Polling is preferable over Short Polling.**
    * `Long Polling` can be enabled at queue level or at the API level using `WaitTimeSeconds API`.

### AWS FIFO Queue
- Newer offering (First In - First Out) - **Not available in all regions.**
- Name of queue must end in `.fifo`.
- Lower throughput (up to 3000 per second with batching | 300 per second without batching).
- Messages are processed in order by consumer.
- Messages are sent exactly once.
- No per message delay (**Only Per Queue Delay**).
- Ability to do content based de-duplication.
- 5-Minute interval de-duplicattion using `Duplication Id`.
- Message Groups:
    * Possibility to group messages for FIFO ordering using `Message GroupId`.
    * Only one worker can be assigned per message group so that messages are processed in order.
    * Message group is just an extra tag on the Message!

### SQS Extended Client
- Message size limit is 256kb, how to send large messages? This is where `Extended Client` comes into picture.
- It is available only under `Java Library` at the moment.
- It leverages `S3` over `SQS Queue`.

### SQS Security
- Encryption in flight using the HTTPS endpoint.
- Can enable `SSE (Server Side Encryption)` using `KMS`.
    * Can set the `CMK (Customer Master Key)` we want to use.
    * Can set the data key reuse period (between 1 minute and 24 hours).
        - Lower and KMS API will be used often.
        - Higher and KMS API will be called less often.
    * SSE only encrypts the message body, not the metadata (Message Id, Timestamp, Attributes).
- IAM policy must allow usage of SQS.
- SQS queue access policy:
    * Finer grained control over IP.
    * Control over the time the requests come in.
- **No VPC Endpoint to access SQS. SQS can only be accessed over internet.**

### AWS SNS
- `AWS SNS (Simple Notification System)` comes into the picture when we want to send one message to many receivers.
- The `Event Producer` only sends message to `SNS Topic`.
- As may `Event Receivers (Subscriptions)` as we want to listen to the `SNS Topic Notifications`.
- Each subscriber to the topic will get all the messages (**Note: Theres a new feature to filter messages**).
- Up to 10,000,000 subscribers per topic.
- 100,000 topics limit.
- Subscribers can be:
    * SQS Queues.
    * HTTP/HTTPS Endpoints (With delivery retries - how many times).
    * Lambda.
    * Emails.
    * SMS Messages.
    * Mobile Notifications.
- **SNS integrates with a lot of Amazon Products:**
    * Some services can send data directly to SNS for notifications.
    * CloudWatch (For Alarms).
    * Auto Scaling Group Notifications.
    * Amazon S3 (On Bucket events).
    * CloudFormation (Upon state changes --> Failed to build etc..)
- **How to publish:**
    * `Topic Publish` (Within your AWS Server - Using the SDK).
        - Create to a Topic.
        - Create a subscription (or many).
        - Publish the topic.
    * `Direct Publish` (For mobile apps SDK).
        - Create a platform application.
        - Create a platform endpoint.
        - Publish to the platform endpoint.
        - Works with Google GCM, Apple APNS, Amazon ADM etc..

### SNS + SQS - Fan Out
- SNS + SQS (Fan Out) is used when you want to publish the data to many SQS queues. i.e. **Push once in SNS, receive in many SQS.**
- Fully decoupled.
- No data loss.
- Ability to add receivers of data later.
- SQS allows for delayed processing.
- SQS allows for retries of work.
- May have many workers on one queue and one worker on the other queue.

### AWS Kinesis
- **Kinesis** is a managed alternative to `Apache Kafka`.
- Great for application logs, metrics, IoT, clickstreams etc..
- Basically it is great for anything with **Real-time Big Data**.
- Great for streaming processing frameworks (Spark, NiFi etc..)
- Data is automatically replicated to `3 Availability Zones`.
- There are 3 Kinesis sub products:
    * `Kinesis Streams`: Low latency streaming ingest at scale.
    * `Kinesis Analytics`: Perform real-time analytics on streams using SQL.
    * `Kinesis Firehose`: Load streams into S3, Redshift, ElasticSearch.
- **Kinesis Streams:**
    * Streams are divided in ordered `Shards/Partitions`.
    * On Shards, data retention is 1 day by default (can go up to 7 days).
    * Ability to reprocess/replay data (In SQS, when data is processed, it's gone. This is not the case with Kinesis).
    * Multiple applications can consume the same stream (Sort of like SNS).
    * Real time processing with scale of throughput.
    * Once data is inserted in Kinsis, it can't be deleted (immutability).
- **Kinesis Stream Shards:**
    * One stream is made of many different shards.
    * 1mb per second or 1000 messages per second at write `PER SHARD`. i.e. A producer can write 1000 messages per second.
    * 2mb per second at read `PER SHARD`.
    * Billing is per shard provisioned. You can have as many shards as you want.
    * Batching available or per message calls.
    * The number of shards can evolve over time (reshard/merge).
    * **Records are ordered per shard.**
- **Kinesis API - Put Records:**
    * On producer side, there is `Put Records API`.
    * `Put Records API` is a way to send data to Kinesis.
    * `PutRecords` API + `Partition Key` that gets hashed. `Partition Key` is hashed to determine shard id.
    * Rule is - Same key always goes to same partition. Helps with ordering for a specific key.
    * Messages that are sent to the shards, get a `sequence number`.
    * Choose a partition key that is highly distributed. Helps prevent `Hot Partition`.
        - For e.g. If your application has millions of users then use `user_id` as a `Partition Key`.
        - For e.g. If your apploication has milllions of users, do not use their `country_id` as a `Partition Key`. Befcause many users can belong to 1 country.
    * Use `Batching` with `PutRecords API` to reduce costs and increase throughput.
    * If we go over the limits, we will get an error `ProvisionedThroughputExceeded`.
    * Can use CLI, AWS SDK, or producer libraries from various frameworks.
    * **Common Exceptions:**
        - `ProvisionedThroughputExceeded` Exception:
            * Happens when sending more data (exceeding MBs per second or TPS for shard).
            * Make sure you dont have a hot shard (such as your partition key is bad and too much data goes to that partition).
        - **Solutions:**
            * Retries with backoff.
            * Increase shards (scaling).
            * Ensure your partition key is a good one.
- **Kinesis API - Consumers:**
    * Can yse a normal consumer (CLI, SDK etc..)
    * Can use `Kinesis Client Library` (in Java, Node, Python, Ruby, .Net).
        - `KCL (Kinesis Client Library` uses `DynamoDB` to checkpoint offsets.
        - `KCL (Kinesis Client Library` uses `DynamoDB` to track other workers and share the work amongst shards.

### Kinesis Security
- Control access/authorization using `IAM Policies`.
- Encryption in flight using HTTPS endpoints.
- Encryption at rest using `KMS (SSE - Server Side Encryption)`.
- Ability to encrypt/decrypt data at client side (harder).
- `VPC Endpoints` available for Kinesis to access within VPC.

### Kinesis Data Analytics
- Perform real-time analytics on `Kinesis Streams` using SQL.
- Kinesis Data Analytics:
    * Auto Scaling.
    * Managed: No servers to provision.
    * Continuos: Real Time.
- Pay for actual consumption rate.
- Can create strewams out of the real-time queires.

### Kinesis Firehose
- Fully managed service, no administration.
- Near Real Time (60 seconds latency).
- Load data into Redshift/Amazon S3/ElasticSearch/Splunk.
- Automatic scaling.
- Support many data format (Pay for conversion).
- Pay for the amount of data going through Firehose.

### SQS vs SNS vs Kinesis
- `SQS`:
    * Consumers `pull data`.
    * Data is deleted after being consumed.
    * Can have as many workers (consumers) as we want.
    * No need to provision throughput.
    * No ordering guarantee (Except FIFO queues).
    * Individual message delay capability.
- `SNS`: Pub/Sub
    * Push data to many subscribers.
    * Up to 10,000,000 subscribers.
    * Data is not persisted (lost if not delivered).
    * Pub/Sub.
    * Up to 100,000 topics.
    * No need to provision throughput.
    * Integrates with SQS for `Fan Out` architecture pattern.
- `Kinesis`:
    * Consumers `pull data`.
    * As many consumers as we want.
    * Possibility to replay data.
    * Meant for real-time big data, analytics and ETL.
    * Ordering at the shard level.
    * Data expires after X days.
    Must provision throughput.

### Amazon MQ
- SQS, SNS are `cloud native` services, and they're using proprietary protocols from AWS.
- Traditional applications running from on-promise may use open protocols such as: `MQTT, AMQP, STOMP, Openwire, WSS etc..`.
- When migrating to the cloud, instead of re-engineering the application to use SQS and SNS, **we can use Amazon MQ**.
- **Amazon MQ = Managed Apache ActiveMQ.**
- Amazon MQ doesn't `Scale` as much as SQS/SNS.
- Amazon MQ runs on a dedicated machine, can run in `HA (High Availability)` with failover.
- Amazon MQ has both queue feature (~SQS) and topic features (~SNS).
- Amazon MQ is a managed message broker service for Apache ActiveMQ that makes it easy to set up and operate message brokers in the cloud.
- Message brokers allow different software systems–often using different programming languages, and on different platforms–to communicate and exchange information.
- Amazon MQ reduces your operational load by managing the provisioning, setup, and maintenance of ActiveMQ, a popular open-source message broker.
- Connecting your current applications to Amazon MQ is easy because it uses industry-standard APIs and protocols for messaging, including JMS, NMS, AMQP, STOMP, MQTT, and WebSocket.
- Using standards means that in most cases, there’s no need to rewrite any messaging code when you migrate to AWS.

### AWS Serverless
- `Serverless` is a new paradigm in which the developers don't have to manage servers anymore.
- Initially, Serverless was `FaaS (Function as a Service)`.
- `Serverless` was pioneered by `AWS Lambda` but now also includes anything that's managed: For e.g. databases, messaging, storage, etc..
- Usually when people say `Serverless in AWS`, they mean `AWS Lambda`.
- **Serverless does not mean there are no servers. It meams you just don't manage/provision/see them.**
- `Serverless` in AWS has many different forms:
    * `AWS Lambda`.
    * `Step Functions (FaaS - Function as a Service)`.
    * `DynamoDB`.
    * `AWS Cognito`.
    * `AWS API Gateway`.
    * `Amazon S3`.
    * `AWS SNS & SQS`.
    * `AWS Kinesis`.
    * `Aurora Serverless`.

### AWS Lambda
- `Lambda` functions can be invoked `Synchronously` or `Asynchronously`.
- Difference between EC2 and Lambda:
    * In `EC2 Architecture`:
        - EC2 are `Virtual Servers` in the Cloud.
        - EC2 machines are limited by RAM and CPU.
        - EC2 instances are continuosly running.
        - Scaling means intervention to add/remove servers.
    * In `AWS Lambda`:
        - Lambda are **Virtual Functions**. No servers to manage!
        - Limited by time - **Short executions**.
        - Run **on-demand**.
        - **Scaling is automated!**
- Benifits:
    * Easy Pricing:
        - Pay per request and compute time. i.e. Pay for only when `AWS Lambda` functions are executed and the time they required to execute.
        - Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time.
    * Integrated with the whole AWS stack.
    * Integrated with many programming languages.
    * Easy monitoring through AWS CloudWatch.
    * Easy to get more resources per function (up to 3GB of RAM).
    * Increasing RAM will also improve CPU and network!

### AWS Lambda Configurations
- Timeout: Default 3 seconds, max of 300 seconds.
- Environment Variables.
- Allocated memory (128mb to 3gb).
- Ability to deploy within a VPC + Assign security groups.
- IAM execution role must be attached to the Lambda Function.

### AWS Lambda Limits
- Execution:
    * Memory Allocation: 128mb to 3008mb (64mb increments).
    * Maximum execution time: 300 seconds (5 Minutes). **Now AWS supports 15 minutes but exam still assumes 5 minutes max.**
    * Disk capacity in the `Function Container` i.e. in `/tmp` is 512mb.
    * Concurrency limit: Maximum 1000 lambda functions can cocurrently execute. This can be incremented by support ticket request.
- Deployment:
    * Lambda function deployment size (compressed .zip): 50mb.
    * Size of uncompressed deployment (code + dependencies): 250mb.
    * Can use `/tmp` directory to load other files at startup.
    * Size of environment variables: 4kb.

### AWS Lambda Concurrency And Throttling
- Concurrency: Up to 1000 executions (can be increased through ticket).
- Can set a `Reserved Concurrency` at the function level.
- Each invocation over the concurrency limit will trigger a `Throttle`.
- `Throttle Behavior`:
    - If `Synchronous Invocation` then it will return `ThrottleError - 429`.
    - If `Asynchronous Invocation` then it will retry automatically and then go to `DLQ`.

### AWS Lambda Retries And DLQ
- `Lambda` functions can be invoked `Synchronously` or `Asynchronously`.
- If it is invoked `Synchronously` and it fails then you are responsible as a `Caller` to retry. You could use `Exponential Back-off` to retry your function.
- If it is invoked `Asynchronously` and it fails then it will be retried **twice**.
    * After all retries (`Asynchronously` called function), unprocessed events go to the `Dead Letter Queue`.
    * Original event payload is sent to the DLQ.
    * This is an easy way to debug what's wrong with your functions in production without changing the code.
- In Lambda, a DLQ can be a `SNS Topic` or `SQS Queue`.
- **Make sure the IAM execution role is correct for your Lambda function.**

### AWS Lambda Logging Monitoring And Tracing
- `CloudWatch`:
    * AWS Lambda execution logs are stored in AWS `CloudWatch Logs`.
    * AWS Lambda metrics are displayed in AWS `CloudWatch Metrics`.
    * **Make sure your Lambda function has an execution role with an IAM policy that authorizes writes to CloudWatch.**
- `X-Ray`:
    * It's possible to trace Lambda with X-Ray.
    * Enable in Lambda configuration (runs the X-Ray daemon for you).
    * Use AWS SDK in Code.
    * **Ensure Lambda Function has correct IAM Execution Role.**

### AWS Lambda Versions And Aliases
- When you work on a Lambda function, you work on a version called `$LATEST`.
- `$LATEST` version is **mutable** (i.e. we can change it however we want).
- When we're ready to publish a Lambda function, we can create a version. This version is **immutable**.
- Versions are **immutable**.
- Versions have increasing version numbers.
- Versions get their own `ARN (Amazon Resource Name)`.
- Version represents `Code + Configuration`. **Nothing can be changed! Immutable.**
- Each version of the Lambda function can be accessed using the correct `ARN`.
- `AWS Lambda Aliases`:
    * **Aliases are mutable.**
    * Aliases are `pointers` to `Lambda Function Versions`.
    * We can define `dev`, `test`, `prod` aliases and have them point at different lambda versions.
    * Aliases enable `Blue/Green` deployments by assigning weights to lambda functions.
    * Aliases enable stable configuration of our event triggers/destinations.
    * **Aliases have their own ARNs.**

### AWS Lambda Best Practices
- Perform heavy duty work outside of your function handler:
    * Connect to databases outside of your function handler.
    * Initialize the AWS SDK outside of your function handler.
    * Pull in dependencies or datasets outside of your function handler.
- User `Environment Variables` for:
    * Database Connection Strings, S3 Bucket, etc.. do not put these values directly in your code.
    * Passwords, sensitive values, etc.. can be encrypted using `KMS`.
    * Environment Variables can be 4kb max in size.
- Minimize your deployment package size to its runtime necessities:
    * Break down the function if need be.
    * Remember the AWS Lambda limits.
        - Lambda function deployment size (compressed .zip): 50mb.
        - Size of uncompressed deployment (code + dependencies): 250mb.
- **Avoid using recursive code, never have a Lambda function call itself.**
- Don't put your Lambda function in a VPC unless you have to. In VPC, Lambda Function will take bit of a time to initialize.

### DynamoDB Intro
- NoSQL Databases:
    * Are non-relational databases and are **Distributed**.
    * For e.g. MongoDB, DynamoDB etc..
    * Do not support joins.
    * All the data that is needed for a query is present in one row.
    * Don't perform/provide aggregations such as `SUM`.
    * **NoSQL Databases scale horizontally!**
    * There's no `right or wrong` for NoSQL vs SQL, they just require to model the data differently and think about user queries differently.
- Fully managed, Highly available with replication across `3 Availability Zones` by default.
- NoSQL Database - Not a relational database.
- Scales to massive workloads, distributed database.
- Millions of requests per second, trillions of rows, 100s of TB of storage.
- Fast and consistent in performance (low latency on retrieval).
- Integrated with IAM for security, authorization and administration.
- Enables event driven programming with `DynamoDB Streams`.
- Low cost and auto scaling capabilities.
- **Basics:**
    * DynamoDB is made of **Tables**.
    * Each table has a **Primary Key** (must be decided at creation time).
    * Each table can have an infinite number of items (i.e. Rows).
    * Each item has **attributes** (can be added over time - can be null).
    * Maximum size of a item is 400kb.
    * Data types supported are:
        - Scaler Types: String, Number, Binary, Boolean, Null.
        - Document Types: List, Map.
        - Set Types: String Set, Number Set, Binary Set.
- **Primary Keys:**
    * Option 1: Partition key only (`HASH`)
        - Partition key must be unique for each item.
        - Partition key must be `diverse` so that the data is distributed.
        - For e.g. `user_id` for `users` table.
    * Option 2: `Partition Key + Sort Key`
        - The combination must be unique.
        - Data is grouped by partition key.
        - `Sort Key` is also a `Range Key`.
        - For e.g. In `users-games` table:
            * `user_id` for the `Partition Key`
            * `game_id` for the `Sort Key`.

## DynamoDB - Provisioned Throughput
- Table must have provisioned read and write capacity units.
- `Read Capacity Units (RCU)`: Throughput for reads ($0.00013 per RCU).
    * In DynamoDB, you get an option to choose `Strongly Consistent Read` or `Eventualy Consistent Read`.
        - **Eventually Consistent Read:** If we read just after a write, it is possible that we might get an unexpected response because of replication.
        - **Strongly Consistent Read:** If we read just after a write, we will definitely get the correct data.
        - **By Default:** DynamoDB uses `Eventually Consistent Read` but `GetItem, Query & Scan` has a `ConsistentRead` parameter you can set to `True`.
    * One `Read Capacity Unit (RCU)` represents `1 Strongly Consistent Read` per second, or `2 Eventually Consistent Reads` per second, for an item up to 4kb in size.
    * `1 RCU` = 1 Strongly consistent read of 4kb per second.
    * **OR**
    * `1 RCU` = 2 Eventually consistent read of 4kb per second.
    * If the items are larger than 4kb, more RCU are consumed.
    * Examples: Calculate RCU in following scenarios:
        - **Example 1:** 10 Strongly consistent reads per seconds of 4kb each:
            * We need `(10 * 4) / 4 = 10 RCU`.
        - **Example 2:** 16 Eventually consistent reads per seconds of 12kb each:
            * We need `(16 / 2) * (12 / 4) = 24 RCU`.
        - **Example 3:** 10 Strongly consistent reads per seconds of 6kb each:
            * We need `(10 * 8) / 4 = 20 RCU`. (We have to round up 6kb to 8kb)
- `Write Capacity Units (WCU)`: Throughput for writes ($0.00065 per WCU).
    * One `Write Capacity Unit (WCU)` represents one write per second for an item up to 1kb in size.
    * `1 WCU` = 1 Write of 1kb second.
    * If the items are larger than 1kb, more WCU are consumed.
    * Examples: Calculate WCU in following scenarios:
        - **Example 1:** We write 10 objects per seconds of 2kb each:
            * We need `2 * 10 = 20 WCU`.
        - **Example 2:** We write 6 objects per seconds of 4.5kb each:
            * We need `6 * 5 = 30 WCU` (4.5 gets rounded to the upped kb).
        - **Example 3:** We write 120 objects per **minute** of 2kb each:
            * We need `(120 / 60) * 2 = 4 WCU`.
- Option to setup auto-scaling of throughput to meet demand.
- Throughput can exceeded temporarily using `Burst Credit`.
- If ther burst credit are empty, you'll get a `ProvisionedThroughputException`.
- It's then advised to do an exponential back-off retry.

### DynamoDB - Partitions Internal
- Data is divided in partitions.
- Partition keys go through a hashing algorithm to know to which partition they go to.
- To compute the number of partitions:
    * By capacity: `(TOTAL RCU / 3000) + (TOTAL WCU / 1000)`.
    * By size: `Total Size / 10 GB`.
    * Total Partitions: `CEILING(MAX(Capacity, Size))`.
- **WCU and RCU are spread evenly between partitions**

### DynamoDB - Throttling
- If we exceed our RCU or WCU, we get `ProvisionedThroughputExceededException`.
- Reasons:
    * Hot Keys: One partition key is being read too many times (for e.g. popular item).
    * Hot partition.
    * Very large items: Remember RCU and WCU depends on size of items.
- Solutions:
    * Exponential back-off when exception is encountered (already in SDK).
    * Distribute partition keys as much as possible.
    * If RCU issue, we can use `DynamoDB Accelerator (DAX)`.

### DynamoDB - Basic APIs
- Writing Data:
    * `PutItem`: Write data to DynamoDB (Create data or full replace).
        - Consumes `WCU`.
    * `UpdateItem`: Update data in DynamoDB (Partial update of attributes).
        - Possibility to use `Atomic Counters` and increase them.
    * `Conditional Writes`:
        - Accept a write/update only if conditions are respected, otherwise reject.
        - Helps with concurrent access to items.
        - No performance impact.
- Deleting Data:
    * `DeleteItem`: Delete an individual row.
        - Ability to perform conditional delete.
    * `DeleteTable`: Delete a whole table and all its items.
        - Much quicker deletion than calling `DeleteItem` on all items.
- Batching Writes:
    * `BatchWriteItem`:
        - Up to 25 `PutItem` and/or `DeleteItem` in one call.
        - Up to 16 mb of data written.
        - Up to 400 kb of data per item.
    * Batching allows you to save in latency by reducing the number of API calls done against DynamoDB.
    * Operations are done in parallel for better efficiency.
    * It's possible for part of a batch to fail, in which case we have can retry for the failed items (using exponential back-off algorithm).
- Reading Data:
    * `GetItem`: Read based on `Primary Key`.
        - `Primary Key` = `Hash (Partition Key)` or `Hash-Range (Partition Key + Sort Key)`.
        - Eventually consistent read by default.
        - Option to use `Strongly Consistent Reads` (More RCU - might take longer).
        - `ProjectionExpression` can be specified to include only certain attributes.
    * `BatchGetItem`:
        - Up to 100 items.
        - Up to 16 mb of data.
        - Items are retrieved in parallel to minimize latency.
- DynamoDB Query:
    * `Query` returns items based on:
        - `PartitionKey` value (**Must be = operator**).
        - `SortKey` value (=, <, >, <=, >=, Between, Begin) - Optional.
        - `FilterExpression` to further filter (client side filtering).
    * Returns:
        - Up to 1mb of data.
        - Or number of items specified in `Limit`.
    * Able to do pagination on the results.
    * You can query a `table`, `a local secondary index` or a `global secondary index`.
- DynamoDB Scan:
    * `Scan` the entire table and then filter out data. **Extremely Inefficient!**
    * Returns up to 1 mb of data - use pagination to keep on reading.
    * Consumes a lot of `RCU`.
    * Limit impact using `Limit` or reduce the size of the result and pause.
    * For faster performance, use `Parallel Scans`.
        - Multiple instances scan multiple partitions at the same time.
        - Increases the throughput and RCU consumed.
        - Limit the impact of parallel scans just like you would do for `Scans`.
    * Can use `ProjectionExpression + FilterExpression` (No change to RCU).

### DynamoDB - Indexes
- `Local Secondary Index (LSI)`:
    * Alternate range key for your table. **Local to the hash key**.
    * Up to 5 local secondary indexes per table.
    * The sort key consist of exactly one scaler attribute.
    * The attribute you choose must be a scaler type: `String`, `Number` or `Binary`.
    * **`LSI` must be defined at table creation time.**
- `Global Secondary Index (GSI)`:
    * `GSI` is used to speed up queries on non-key attributes.
    * `GSI` = `PartitionKey` + `Optional SortKey`.
    * The index is a new `table` and we can project attributes on it.
        - The `PartitionKey` and `SortKey` of the original table are always projected (`KEYS_ONLY`).
        - You can specify extra attributes to project (`INCLUDE`).
        - You can use all attributes from main table (`ALL`)
    * `RCU and WCU` must be defined for `GSI`.
    * **`GSI` can be added/modified later. `LSI` cannot be added or modified later.**

### DynamoDB - Concurrency
- DynamoDB has a feature called `Conditional Update/Delete`.
- It means that you can ensure an item hasn't been changed before altering it.
- That makes DynamoDB an `Optimistic Locking` or `Concurrency` Database.

### DynamoDB - Accelerator - DAX
- `DAX = DynamoDB Accelerator`.
- Seamless cache for DynamoDB, no application re-write required.
- Writes go through DAX to DynamoDB.
- Micro Seconds latency for cached reads and queries.
- Solves the `Hot Key` problem (too many reads).
- By default, items live in cache for 5 minutes `TTL (Time To Live)`.
- Up to 10 nodes in cache cluster.
- `Multiple Availability Zones` (In production, minimum 3 nodes are recommended).
- Secure (Encryption at rest with KMS, VPC, IAM, CloudTrail..)

### DynamoDB - Streams
- Changes in DynamoDB (Create, Update, Delete) can end up in `DynamoDB Stream`.
- This stream can be read by AWS Lambda and we can then do:
    * React to changes in real time (Welcome email to new users).
    * Analytics.
    * Create derivative tables/views.
    * Insert into `Elastic Search`.
- You can implement cross region replication using `Streams`.
- `Stream` has 24 hours of data retention.

### DynamoDB - Security And Other Features
- Security:
    * VPC endpoints are available to access DynamoDB without internet.
    * Full access to DynamoDB is controlled by `IAM`.
    * Encryption at rest using `KMS`.
    * Encryption in transit using `SSl/TLS`.
- Backup and Restore features available:
    * `Point In Time` restore like RDS.
    * No performance impact.
- Ability to have `Global Table`:
    * Multi region, fully replicated, high performance.
- **`Amazon DMS` can be used to migrate to DynamoDB (From MongoDB, MySQL, Oracle, S3, etc..)**
- You can launch a local DynamoDB for development purposes.

### API Gateway Intro
- `API Gateway` is a way for us to `Build, Deploy & Manage` serverless APIs.
- `AWS Lambda + API Gateway`: No infrastructure to manage.
- Handle API versioning (v1, v2..)
- Handle different environments (dev, test, prod).
- Handle security (Authentication and Authorization).
- Create API keys, handle request throttling.
- `Swagger/Open API Import` to quickly define APIs.
- Transform and validate requests and responses.
- Generate SDK and API specifications.
- Cache API responses to limit the load that comes to your Lambda functions.
- API Gateway Integrations:
    * `Outside of VPC`:
        - AWS Lambda (Most popular/powerful).
        - Endpoints on EC2.
        - Load Balancers.
        - Any AWS Service.
        - External and publicly accessible HTTP endpoints.
    * `Inside of VPC`:
        - AWS Lambda in your VPC.
        - EC2 endpoints in your VPC.

### API Gateway - Deployment Stages
- Making changes in the API Gateway does not mean they're effective.
- You need to make a `deployment` for them to be in effect.
- It's a common source of confusion.
- Changes are deployed to `Stages` (As many as you want).
- Use the naming you like for `Stages` (Dev, Test, Prod).
- Each stage has it's own configuration parameters.
- Stages can be rolled back as a history of deployments is kept.
- `Stage Variables`:
    * Stage variables are like environment variables for API Gateway.
    * Use them change configuration values in different environments.
    * They can be used in:
        - Lambda function ARN.
        - HTTP Endpoints.
        - Parameter mapping templates.
    * Use cases:
        - Configure HTTP endpoints your stages talk to (dev, stage, test, prod).
        - Pass configuration parameters to AWS Lambda through mapping templates.
    * Stage Variables are passed to the `context` object in AWS Lambda.
- `Stage Variables & Lambda Aliases`:
    * We create a srtage variable to indicate the corresponding Lambda alias.
    * Our API gateway will automatically invoke the right Lambda function.
- `Canary Deployment`:
    * Possibility to enable `Canary Deployments` for any stage (usually prod).
    * Choose the % of traffic that goes to `Canary Channels`.
    * Metrics & Logs are separate (For better monitoring).
    * Possibility to override stage variables for Canary.
    * This is `Blue/Green Deployment` with `AWS Lambda & API Gateway`.

### API Gateway - Mapping Templates
- `Mapping Templates` can be used to modify request/responses.
- They allow us to:
    * Rename parameters.
    * Modify body content.
    * Add Headers.
    * Map JSON to XML for sending to backend or back to client.
    * Filter poutput results (Remove unnecessary data).
- `Mapping Templates` use `Velocity Template Language (VTL)`. `VTL` supports `for loops, if statements etc..`

### API Gateway - Swagger And Open API Specifications
- Common way of defining REST APIs, using API definition as code.
- Import existing `Swagger/OpenAPI 3.0 Spec` to API Gateway.
    * Method.
    * Method Request.
    * Integration Request.
    * Method Response.
    * +AWS extensions for API Gateway and setup every single option.
- Can export current API as `Swagger/OpenAPI Spec`.
- `Swagger` can be written in `YAML` or `JSON`.
- Using `Swagger`, we can generate `SDK` for our applications.

### API Gateway - Caching
- Caching reduces the number of calls made to the backend.
- Default time `TTL (Time To Live)` for cache is 300 seconds. `Minimum: 0 seconds | Maximum: 3600 seconds`.
- Caches are defined per stage (dev, prod etc..).
- Cache encryption option.
- Cache capacity between `0.5 GB` to `237 GB`.
- Possible to override cache settings for specific API methods.
- Able to flush the entire cache (`Invalidate`) immediately.
- **Can client invalidate the cache?**
    * YES! With following 2 points:
        - Client must have proper `IAM Authorization`.
        - Client need to set following header:
            ```
            Cache-Control: max-age=0
            ```

### API Gateway - Logging Monitoring And Tracing
- **CloudWatch Logs:**
    * Enable CloudWatch logging at the `Stage Level` (with `Log Level`).
    * Can override settings on a per API basis (For e.g. `Error`, `Debug`, `Info`).
    * Log contains information about `request/response` body.
- **CloudWatch Metrics:**
    * Metrics are by `Stage`.
    * Possibility to enable `Detailed Metrics`.
- **X-Ray:**
    * Enable tracing to get extra information about requests in API Gateway.
    * `X-Ray API Gateway + AWS Lambda` gives you the full picture.

### API Gateway - CORS - Usage Plans And API Keys
- **CORS:**
    * `CORS` must be enabled when you receive API calls from another domain.
    * The `Options` pre-flight request must contain the following headers:
        ```
        Access-Control-Allow-Methods
        Access-Control-Allow-Headers
        Access-Control-Allow-Origin
        ```
    * `CORS` can be enabled through console.
- **Usage Plans And API Keys:**
    * What if you want to limit your customers usage of your API?
        - **Usage Plans:**
            * `Throttling`: Set overall capacity and burst capacity.
            * `Quotas`: Number of requests made per day/week/month.
            * You can configure `Usage Plans` for different `Stages (For e.g. Dev, Prod)`.
        - **API Keys:**
            * Generate one per customer.
            * Associate with `Usage Plans`.
            * Ability to track usage for `API Keys`.

### API Gateway - Security
- There are 3 aspects to API Gateway - Security:
    * `IAM Permissions`.
    * `Lambda Authorizers`.
    * `Cognito User Pools`.
- **IAM Permissions:**
    * Create an IAM policy authorization and attach to `User/Role`.
    * API Gateway verifies `IAM Permissions` passed by the calling application.
    * Good to provide access within your own infrastructure.
    * Leverages `Sig v4` (Signature v4) capability where IAM credentials are in headers.
    * There are no added costs to this solution.
    * If you give access to users outside of your AWS, then you can't use IAM permissions obviously.
- **Lambda Authorizer (Formerly `Custom Authorizers`):**
    * Uses `AWS Lambda` to validate the token passed in the header.
    * Option to cache result of authentication. For e.g. Say you wanna cache authentication for 1 hour.
    * Helps to use `OAuth/SAML/3rd party type of authentication`.
    * Based on the token passed in header, Lambda must return an `IAM Policy` for the user.
- **Cognito User Pools:**
    * Cognito fully manages user lifecycle.
    * API Gateway verifies identity automatically from AWS Cognito.
    * No custom implementation required.
    * **Cognito only helps with authentication, not authorization.**
- **Summary:**
    * `IAM`:
        - Great for users/roles already within your AWS account.
        - Handle authentication + authorization.
        - Leverages `Sig v4`.
    * `Lambda Authorizers (Custom Authorizer)`:
        - Great for 3rd party tokens.
        - Very flexible in terms of what IAM policy is returned.
        - Handle Authentication + Authorization.
        - Pay per `Lambda Invocation`.
    * `Cognito User Pools`:
        - You manage your own user pool (can be backed by Facebook, Google login etc..)
        - No need to write any custom code.
        - Must implement authorization in the backend.

### AWS Cognito
- We want to give our users an identity so that they can interact with our application.
- `Cognito User Pools`:
    * Sign in functionality for app users.
    * Integrate with API Gateway.
    * Creates a serverless database of users for your mobile apps.
    * Simple login: Username (or Email)/Password combination.
    * Possibility to verify emails/phone numbers and add `MFA (Multi Factor Authentication)`.
    * Can enable `Federated Identities` (Facebook, Google, SAML etc..)
    * After authentication, we receive `JSON Web Tokens (JWT)`.
    * **Can be integrated with API Gateway for authentication.**
- `Cognito Identity Pools (Federated Identity)`:
    * Provide AWS credentials to users so they can access AWS resources directly.
    * Integrate with `Cognito User Pools` as an identity provider.
    * **Goal:**
        - To provide direct access to AWS Resources from the `Client Side`.
    * **How?**
        - Log into `Federated Identity Provider (Facebook, Google, SAML etc..)` or remain anonymous.
        - Get temporary AWS credentials back from the `Federated Identity Pool`.
        - These credentials come with a pre-defined IAM policy stating their permissions.
    * **Example:**
        - Provide (temporary) access to write to S3 bucket using Facebook login.
- `Cognito Sync`:
    * Synchronize data from devide to Cognito.
    * May be deprecated and replaced by **AppSync**.
    * Store preferences, configuration, state of app.
    * Cross device synchronization (any platform - IOS, Android, etc..)
    * Offline capability (Synchronization when back online).
    * **Requires `Federated Identity Pool` in Cognito (not `User Pool`).**
    * Store data in `datasets`. Each `dataset` can be up to `1 mb`.
    * Up to 20 `datasets` to synchronise.

### SAM 101
- `Serverless Application Model (SAM)`.
- `SAM` is a framework for developing and deploying serverless applications.
- All the configuration is in `SAM YAML` file.
- It generates complex CloudFormation from simple `SAM YAML` file.
- Supports anything from CloudFormation: Outputs, Mappings, Parameters, Resources, etc..
- Only 2 commands to deploy to AWS.
- `SAM` can use CodeDeploy to deploy `Lambda Functions`.
- **`SAM` allows you to run `Lambda, API Gateway, DynamoDB` locally.**
- **How `SAM` works? `SAM Recipe`:**
    * There's this `Transform Header` that indicates it's a `SAM template`. Header:
        ```
        Transform: 'AWS::Serverless-2016-10-31'
        ```
    * Following are the 3 resources types we can use in our `SAM template` code:
        ```
        AWS::Serverless::Function //Lambda
        AWS::Serverless::Api //Api Gateway
        AWS::Serverless::SimpleTable //DynamoDB
        ```
    * For `Packaging`, we can use `AWS CloudFormation Package` or `SAM Package`.
    * For `Deployment`, we can use `AWS CloudFormation Deploy` or `SAM Deploy`.

### Encryption 101
- **Encryption in Flight (SSL):**
    * Data is encrypted before sending and decrypted after receiving it on server.
    * SSL certificates help with encryption.
    * Encryption in flight protects us from `MITM (Man In The Middle Attack)`.
- **Server Side Encryption At Rest:**
    * Data is encrypted after being received by the server.
    * Data is decrypted before being sent.
    * It is stored in an ecrypted form, thanks to a key (usually a data key).
    * The encryption/decryption keys must be managed somewhere and the server must have access to it.
- **Client Side Encryption:**
    * Data is encrypted by the client and never decrypted by the server.
    * Data will be decrypted by a receiving client.
    * The server should not be able to decrypt the data.
    * For this we could use `Envelop Encryption`.

### KMS - Key Management System
- Anytime you hear `encryption` for an AWS service, it's most likely `KMS`.
- Easy way to control access to your data, AWS manages keys for us.
- Fully integrated with `IAM` for `Authorization`.
- Seamlessly integrated into:
    * `Amazon EBS`: Encrypt volumes.
    * `Amazon S3`: Server side encryption of objects.
    * `Amazon Redshift`: Encryption of data.
    * `Amazon RDS`: Encryption of data.
    * `Amazon SSM`: Parameter store.
    * Etc..
- But you can also use the `CLI/SDK`.
- **KMS 101:**
    * Anytime you need to share sensitive information, use `KMS`. Sensitive information such as:
        - Database Passwords.
        - Credentials to external service.
        - `Private Key` of SSL certificates.
    * The value in `KMS` is that the CMK (`Customer Master Key`) used to encrypt data can never be retrieved by the user, and the CMK can be rotated for extra security.
    * **Never ever store your secrets in plaintext, especially in your code!**
    * Encrypted secrets can be stored in the code/environment variables.
    * **KMS can only help in encrypting up to 4kb of data per call.**
    * If data is `>4kb`, use `Envelop Encryption`.
    * To give access to `KMS` to someone:
        - Make sure the `Key Policy` allows the user.
        - Make sure the `IAM Policy` allows the `API Calls`.
- **KMS (Key Management Service):**
    * Able to fully manage Keys and Policies:
        - Create Keys.
        - Rotation Policies (To rotate keys).
        - Disable Keys.
        - Enable Keys.
    * We get to fully manage the Keys but we never ever see them.
    * Able to Audit key usage using `CloudTrail`.
    * There are 3 types of `CMK (Customer Master Keys)`:
        - `AWS Managed Service Default CMK`: **Free.**
        - `User Created CMK in KMS`: **$1 per month.**
        - `User Created CMK imported into KMS (Must be 256-bit Symmetric Key)`: **$1 per month.**
    * Every time you call `KMS` for doing `Encryption/Decryption` or any `KMS API Call`, you will be charged: **$0.03 per 10,000 calls.**

### Encryption SDK
- What if you want to encrypt data over `4kb` using `KMS`?
- For this, we will have to use `Envelop Encryption`.
- `Envelop Encryption` is a bit cumbersome to implement.
- The `AWS Encryption SDK` helps us to use `Envelop Encryption`.
- **NOTE: It is totally different from the `S3 Encryption SDK`.**
- The `Encryption SDK` also exists as `CLI Tool` that we can install.
- 1 line conclusion:
    * **Anything over `4kb` of data that needs to be encrypted using `KMS` must use the `Encryption SDK` i.e. `Envelop Encryption` and it uses `GenerateDataKey API`.**
    * For `Envelop Encryption`,  Encryption & Decryption both happens at `Client Side`.

### SSM Parameter Store
- It allows us to **Securly** store our `Secrets` and `Configurations`.
- **Optional** seamless encryption using `KMS`.
- It's `Serverless`, `Scalable`, `Durable`, **FREE** and there is an easy SDK to use it.
- You are able to do `Version Tracking` of `Secrets` and `Configurations`.
- Configuration options using `Path` and `IAM`. For e.g. Using `IAM`, we can control who can view which database passwords.
- Notification with `CloudWatch Events`.
- Has an integration with `CloudFormation`.
- For e.g. CLI command to retrieve parameters with decryption:
    ```
    // Get parameters by path
    aws ssm get-parameters-by-path --path /my-app/ --recursive --with-decryption

    // Get parameters by name
    aws ssm -get-parameters --names /my-app/dev/db-url /my-app/dev/db-password --with-decryption

    ```

### IAM Best Practices - General
- Never use `Root Credentials`.
- Enable `MFA (Multi Factor Authentication)` for `Root Account`.
- Grant least privileges to your `Lambda Functions` and `IAM Roles`.
    * Each `Group`, `User`, `IAM Role` should only have the minimum level of permission it needs.
    * Never grant a policy with **`*`** access to a service.
    * Monitor API calls made by user in `CloudTrail` (especially `Denied` ones).
- Never ever ever store `IAM` key credentials on any machine but a personal computer or on-premise server.
- On premise server best practice is to call `STS` to obtain temporary security credentials.
- **`IAM Roles` Best Practices:**
    * `EC2` machines should have their own roles.
    * `Lambda Functions` should have their own roles.
    * `ECS Tasks` should have their own roles:
        ```
        ECS_ENABLE_TASK_IAM_ROLE=true
        ```
    * `CodeBuild` should have its own service role.
    * **Overall, you should always create least-privileged role for any service that requires it.**
    * **Create a role per application/lambda function. Do not reuse roles.**
- **`Cross Account Access` Best Practices:**
    * Define an `IAM Role` for another account to access.
    * Define which accounts can access this `IAM Role`.
    * Use `AWS STS (Security Token Service)` to retrieve credentials and impersonate the `IAM Role` you have access to (**`AssumeRole API`**).
    * Temporary credentials can be valid between 15 minutes to 1 hour.

### CloudFront
- AWS CloudFront is a `Content Delivery Network (CDN)`.
- Improves read performance, content is cached at the edge (edge = locations around the world).
- Currently there are 146 `Point of Presence (Edge Locations)` globally.
- Very popular with `S3` but also works with `EC2` and `Load Balancing`.
- Can help you protect against network attacks (e.g. DDoS).
- Can provide SSL encryption (HTTPS) at the edge using `ACM (Amazon Certificate Manager)`.
- CloudFront can use SSL encryption (HTTPS) to talk to your applications.
- Supports `RTMP Protocol` for videos and media.

### Step Functions
- Build a serverless visual workflow to orchestrate your `Lambda Functions`.
- All the flow represent flow as a `JSON State Machine`.
- Features:
    * Sequence Of Lambda Functions.
    * Parallel Lambda Functions.
    * Conditions.
    * Timeout.
    * Error Handling.
    * Etc..
- Can also integrate with EC2, ECS, On Premise Servers, API Gateway.
- Maximum execution time of `1 Year`.
- Use Cases:
    * Order fulfillment.
    * Data processing.
    * Web applications.
    * Any workflow.

### SWF - Simple Workflow Service
- Coordinate work amongst applications.
- Code runs on EC2 (not serverless).
- `1 Year` maximum runtime.
- SWF is older (legacy) than Step Functions and it is less supported now.
- Concept of `Activity Step` and `Decision Step`.
- Has built-in `Human Intervention Step`.
- Example: Order fulfillment from web to warehouse to delivery.
- **`Step Functions` are recommended to be used for new applications, except:**
    * If you need external signals to intervene in the processes.
    * If you need child processes that return values to parent processes.

### Docker
- Docker is `Container Technology`.
- Run a containerized application on any machine with Docker installed.
- **Containers allows our application to work the same way anywhere (Portability).**
- Containers are isolated from each other.
- Control how much memory/CPU is allocated to your container.
- Ability to restrict network rules.
- More efficient than Virtual Machines.
- Scame containers up and down very quickly (seconds).

### ECS - Elastic Container Service
- `ECS (Elastic Container Service)` is a container orchestration service.
- `ECS` helps you run `Docker Containers` on `EC2` machines.
- `ECS` is made of:
    * `ECS Core`: Running `ECS` on user-provisioned `EC2 Instances`.
    * `Fargate`: Running `ECS Tasks` on `AWS Provisioned Compute` **(Serverless)**.
    * `EKS`: Running `ECS` on `AWS Powered Kubernetes` **(Running on EC2)**.
    * `ECR`: `Docker Container Registry` hosten by AWS.
- ECS & Docker are very popular for **microservices**.
- `IAM Security & Roles` at the `ECS Task Level`.
- **`ECS` Use Cases:**
    * Run `Microservices`:
        - Ability to run multiple docker containers on the same machine.
        - Easy service discovery features to enhance communication.
        - Direct integration with `Application Load Balancers`.
        - Auto scaling capability.
    * Run batch processing/scheduled tasks:
        - Schedule `ECS` containers to run on `On-Demand`, `Reserved` or `Spot` EC2 instances.
    * Helps you migrate applications to the Cloud.
        - Dockerize legacy applications running on premise.
        - Move Docker containers to run on `ECS`.
- **`ECS` Concepts:**
    * `ECS Cluster`: Set of EC2 instances.
    * `ECS Service`: Applications definitions running on `ECS Cluster`.
    * `ECS Tasks + Definition`: Containers running to create the application.
    * `ECS IAM Roles`: Roles assigned to tasks to ineract with AWS.
- **`ECS (Elastic Container Service)` Integration Into `ALB (Application Load Balancer)`:**
    * `Application Load Balancer (ALB)` has a direct integration feature with ECS called `Port Mapping`.
    * This allows you to run multiple instances of the same application on the same EC2 machine.
    * Use Cases:
        - Increased resiliency even if running on 1 EC2 instance.
        - Maximize utilization of CPI/cores.
        - Ability to perform rolling upgrades without impacting application uptime.
- **`ECS` Setup And Config File:**
    * Run an EC2 instance, install the `ECS Agent` along side ECS Config file.
    * Or use an `ECS-ready Linux AMI` (**Still need to modify config file**).
    * `ECS Config File` is located at:
        ```
        /etc/ecs/ecs.config
        ```
    * Following are the 4 main config settings under `ecs.config` file:
        ```
        ECS_CLUSTER=MyCluster                   #Assign EC2 instance to an ECS cluster.
        ECS_ENGINE_AUTH_DATA={...}              #To pull images from private registries.
        ECS_AVAILABLE_LOGGING_DRIVERS={...}     #CloudWatch container logging.
        ECS_ENABLE_TASK_IAM_ROLE=true           #Enable IAM roles for ECS tasks.
        ```

### ECR - Elastic Container Registry
- Store, manage and deploy your containers on AWS.
- Fully integrated with `IAM & ECS`.
- Sent over HTTPS (Encryption in flight) and encrypted at rest.
- You can push containers to ECR using CLI or `CodeBuild` (for your `CICD` to automate this task).

### SES - Simple Email Service
- Send emails to people using:
    * `SMTP` interface.
    * `AWS SDK`.
- Ability to receive emails.
- Integrates with:
    * `S3`.
    * `SNS`.
    * `Lambda Functions`.
- Integrated with `IAM` for allowing to send emails.