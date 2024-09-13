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
