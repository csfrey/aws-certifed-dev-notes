# Connecting to EC2 with SSH from Mac

- SSH is one of the most important functions. It allows you to control a remote machine using the command line.
- must `chmod 0400 demoinstancekeys.pem` to protect the key file before the connection will work
- `ssh -i <filename>.pem ec2-user@<public IP3 address>`
- running AWS Configure to configure your credientials is a TERRIBLE IDEA - anyone with SSH access will be able to see them!!!!
- attach an IAM role to the EC2 instance instead (Instance > Actions > Security > Modify IAM role)

## Alternative: EC2 Instance Connect

- just click "connect" on the instance in the AWS console and it will open a terminal in a new browser window
