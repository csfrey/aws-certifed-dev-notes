# EC2

- one of the most popular AWS services
- "Elastic Compute Cloud"
- Infrastructure as a Service
- Mainly consists of
  - renting virual machines (EC2 "instances")
  - storing data on virtual drives (EBS)
  - distributing laod across machines (ELB)
  - scaling the servies using an auto-scaling group (ASG)
- fundamental to understand how the Cloud works

### EC2 sizing and configuration options

- Operating system: Linux/Windows/MacOS
- amount of computer power and cores
- amount of ram
- amount of storage
  - network-attached (EBS & EFS)
  - hardcware (EC2 instance store)
- network card: speed of the card, public IP address
- firewall rules: security group
- bootstrap script (configure at first launch): EC2 User Data

### EC2 User Data script

- it's possible to bootstrap our instances using an EC2 User Data script
- script is only run one at the instance first start
- used to automate boot tasks such as:
  - installing updates
  - installing software
  - downloading common files from the internet
  - anything you can think of
- runs with the **root user**

### EC2 Instance Types

- naming example: "m5.2xlarge"
  - m = instance class
  - 5 = generation, updated/incremented over time
  - 2xlarge = size
- General Purpose
  - greate for a diversity of workloads
  - balance between compute, memory, networking
- Compute Optimized
  - optimized for compute-intensive tasks with high-performance preocessors
    - batch processing workloads
    - media transcoding
    - high performance web servers
    - high performance computing (HPC)
    - scientific modeling & machine learning
    - dedicated gaming servers
- Memory Optimized
  - fast performance for workloads that process large data sets in memory
  - use cases:
    - high performance, reltational/non-relatioal databases
    - distributed web scale cache stores
    - in-memory databases optimized for BI (business intelligence)
    - applications performing real-time processing of big unstructure data
- Storage Optimized
  - grewate for storage intensive task that requrie high, sequential read and write access to large data sets on local storage
  - use cases:
    - high frequency online transaction processing (OLTP) systems
    - relational and NoSQL databases
    - cache for in-memory databases (e.g. Redis)
    - data warehousing applications
    - distributed file systems
- find a complete list of instances on http://ec2instances.info

### Purchasing Options

- On-Demand Instances
  - short workloads
  - predictable pricing, pay by the second after the first minute
  - highest cost, but no upfront payment
  - no long-term commitment
  - recommended for short-term and uninterrupted workloads where you can't predict how the application will behave
- Reserved (1 & 3 year terms)
  - Convertable Reserved Instances
    - long workloads with flexible instances
    - Can change the EC2 instance type, instance family, OPS, scope, and tenancy
    - up to 66% discount
  - Reserved Instances - long workloads
  - Up to 72% discount compared to on-demand
  - reserve specific instance attributes (Instance Type, Region, Tenancy, OS)
  - payment options - no upfront, partial upfront, all upfront
  - reserved isntance scope - regional or zonal
  - recommended for stead-state usage applications (think DBs)
  - you can buy and sell in the Reserved Instance Marketplace
- Savings Plans (1 & 3 year terms)
  - commitment to an amount of usage
  - long workloads
  - get a discount based on long-term usage
  - commit to a certain type of usage
  - Locked to a specific instance family & AWS region
  - flexible across instance size, OS, tenancy
- Spot Instances
  - short workloads, cheap, can lose instances
  - discounts up to 90%
  - define a max price you're willing to pay
  - MOST cost efficient
  - good for things that are resilient to failure
  - NOT suitable for critical jobs or databases
- Dedicated Hosts
  - book an entire physical server,
  - control instance placement
  - allows you to address compliance requirements anduse your existing server-bound software licenses (per-socket, per-core, per-VM software licenses)
  - purcasing options
    - dedicated host
    - reserved for 1 or 3 years
  - MOST expensive options
- Dedicated instances
  - no other customers will share your hardware
  - may share hardware with other instances in the smae account
  - no control over instance placement
- Capacity reservations
  - reserve capacity in a specific Availability Zone for any duration
  - always have access to EC2 capacity when you need it
  - not time commitment, no billing discounts
  - combine with Regional Reserved Instances and Savings Plans to benefit from billing discounts
  - charged at on-demand rate whether you run instances or not
  - suitable for short-term, uninterrupted workloads that needs to be in a specific AZ

### Which to pick

Think of it like this

- On-Demand = coming and staying in a resort whenever we like, we pay the full price
- Reserved = planning ahead, and if we plan to stay for a long time we may get a discount
- Savings Plans = pay for a certain amount per hour for a certain period and stay in any room type
- Spot Instances = the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms. You can get kicked out at any time.
- Dedicated Hosts = book an entire building of the resort
- Capacity Reservations = book a room for period for full price even if you don't stay in it

# EC2 Instance Storage

- EBS = Elastic Block Store
- an EBS Volume is a network drive you can attach to your instances while they run
- it allows your instances to persist data even after they terminate
- they can only be mounted to one instance at a time (at the CCP level)
- they are bound to a specific availability zone
- free tier: 30 GB of free EBS general purpose SSD or magnetic per month
- network drive not a physical drive so there can be latency
- volumes are locked to an AZ
- moving a volume requries taking a snaphot
- Delete on Termination attribute
  - defaults to ON at root volume
  - defaults to OFF on other volumes
- make a backup (snapshot) of our EBS volume at a point in time
- not necessary to detach volume to do a snapshot but it is recommended
- can copy snapshots across AZ or region
- EBS Snapshot Archive
  - move a shanp shot to an "archive tier" that is 75% cheaper
  - takes 24-72 hours to restore
- Recycle Bin for EBS snapshots
  - set up rules to retain deleted snapshots so you can recover them after an accidental deletion
- fast snapshot restore (FSR)
  - force full initialization of snapshot to have no latency on the first use ($$$)
