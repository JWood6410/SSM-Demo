# What is SSM
put some descriptive text here

## Cost
This demo simulates a secure environment where there is no direct outbound access. To connect to AWS services, VPC Endpoints are used. We also spin up 2 x T3.Micro servers and use a KMS key. 

| Description   | Hourly Cost | Monthly Cost |
|---------------|-------------|--------------|
| EC2 Linux     | $0.0132     | $9.636       |
| EC2 Windows   | $0.0224     | $16.352      |
| VPC Endpoints | $0.052      | $37.97       |
| KMS Key       | N/A         | $1.03        |

# SSM Connectivity Requirements
SSM has several requirements before it will connect. Firstly, the EC2 instances need to have a role with permissions to connect to the SSM service. Secondly, the EC2 instances need to have the SSM agent installed. This comes default with several AMIs, including Windows and Amazon Linux 2. Finally, the instances need to talk to the SSM service. This can be done either via outbound internet \(Internet Gateway or NAT Gateway\) or using VPC Endpoints. 

## Instance Profile/Role
This one is fairly easy thanks to an AWS managed policy, AmazonSSMManagedInstanceCore. Either create an Instance Profile or a Role and attach that to your EC. 

## Endpoints
There are three endpoints needed for full SSM access: SSM, SSMMessages, and EC2Messages. In this example, I am using a single AZ for all endpoints, along with a single Security Group. We don't need any HA for this demo.

Deploy Endpoints from the VPCEndpoint.yaml.

**Include a screenshot** 



## EC2 Instances
There is no specific requirement for EC2 instances other than having an agent installed. The agent is installed by default on most Windows, Amazon Linux, Amazon Linux 2, SUSE, Ubuntu, macOS, & EKS-Optimized Amazon Linux AMIs.

The included EC2-Instances.yaml creates:
- A Security Group with no inbound access
- An instance profile and role for SSM access
- A basic Linux instance
- A basic Windows instance

## Console connectivity
Once all the above has been met and your servers are running, you can now use SSM to connect. You can even RDP to Windows servers.

**Include some screenshots**

## Additional
I will be assuming that you have configured CLI access. There are various methods depending on whether you have SSO or not, so I won't be providing examples of that. If you need any assistance, please ask.