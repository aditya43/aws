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

---

### AWS Regions
Each availability `z`one is a physical data center in the region, but separated from the other ones (so that they're isolated from disasters).

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