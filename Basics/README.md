# SSM Connectivity Requirements
SSM has several requirements before it will connect. Firstly, the EC2 instances need to have a role with permissions to connect to the SSM service. Secondly, the EC2 instances need to have the SSM agent installed. This comes default with several AMIs, including Windows and Amazon Linux 2. Finally, the instances need to talk to the SSM service. This can be done either via outbound internet \(Internet Gateway or NAT Gateway\) or using VPC Endpoints. 

## Instance Profile/Role
This one is fairly easy thanks to an AWS managed policy, AmazonSSMManagedInstanceCore. Either create an Instance Profile or a Role and attach that to your EC. 

## Endpoints
There are three endpoints needed for full SSM access: SSM, SSMMessages, and EC2Messages. In this example, I am using a single AZ for all endpoints, along with a single Security Group. We don't need any HA for this demo.

## EC2 Instances
There is no specific requirement for EC2 instances other than having an agent installed. The agent is installed by default on most Windows, Amazon Linux, Amazon Linux 2, SUSE, Ubuntu, macOS, & EKS-Optimized Amazon Linux AMIs.