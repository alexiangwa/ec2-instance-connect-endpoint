Today we launched Amazon EC2 Instance Connect (EIC) Endpoint, a new feature that allows you to connect securely to your instances and other VPC resources from the Internet. With EIC Endpoint, you no longer need an IGW in your VPC, a public IP address on your resource, a bastion host, or any agent to connect to your resources.

Only one endpoint is required per VPC

connect to your linux instance using AWS CLI

1. Create a VPC with public and private subnets.  

2. Install the latest version of the AWS CLI on your computer.
Link: https://awscli.amazonaws.com/AWSCLIV2.msi

3. Create an IAM policy that allows users to create, describe, and delete EC2 Instance Connect Endpoints.
Link: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/permissions-for-ec2-instance-connect-endpoint.html

4. Create an IAM policy that allows users to use the EC2 Instance Connect Endpoints.
Link:  https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/permissions-for-ec2-instance-connect-endpoint.html

5. Create an IAM user that has an access key and secret access key, and attach the policies to the user.

6. Run the "aws configure" command to configure the IAM user's credentials on your computer.

7. Verify that the OpenSSH client is installed on your computer.
Command: ssh -V

8. Create security groups in your VPC.
- eic-endpoint-sg: Open outbound traffic on port 22 and use the VPC CIDR for the source destination.
- ec2-instance-sg: Open inbound traffic on port 22 and use the eic-endpoint-sg for the source destination.
Link: https://docs.aws.amazon.com/AWSEC2/la...

9. Create the EC2 Instance Connect Endpoints.

10. Launch an EC2 instance in the private subnet in your VPC.

12. Connect to the instance.
Command: aws ec2-instance-connect ssh --instance-id [your-instance-id]

 aws ec2-instance-connect ssh --instance-id i-06be27a2c88341351



























