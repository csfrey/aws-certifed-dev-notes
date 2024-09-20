# Intro to security groups

- fundamental unit of network security in AWS
- control how traffic is allowed into or out of our EC2 Instances.
- only contain `allow` rules
- rules can reference by IP or by security group
- act as a "firewall" on EC2 instances
- security groups regulate:
  - access to ports
  - authorized IP ranges
  - control of inbound network
  - control of outbound network
- Good to know

  - can be attached to multiple instances
  - locked down to a region/VPC combination
  - lives "outside" the EC2. if traffic is blocked, the EC2 instance won't see it at all
  - it's good to maintain one separate security group for SSH access
  - if you application is not accessible (time out) then it's a security group issue
  - if your application gives a "connection refused" error, then it's an application error or it's not launched
  - all inbound traffi is BLOCKED by default
  - all outtbound traffic is AUTHORIZED by default

### Some ports to know

| port | usage                         |
| ---- | ----------------------------- |
| 22   | SSH & SFTP                    |
| 21   | FTP                           |
| 80   | HTTP                          |
| 443  | HTTPS                         |
| 3389 | RDP (Remote Desktop Protocol) |
