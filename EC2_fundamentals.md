### EC2

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
