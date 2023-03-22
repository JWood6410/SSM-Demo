# Why this project?
I was asked by the [Melbourne AWS Programming and Tools Meetup](https://www.meetup.com/melbourne-aws-programming-and-tools-meetup/) to give them a demo. Since I've done a few talks on SSM, I decided to adapt my talk to a demo. 

I've broken the demo into three sections:
- **Basics** - This will get you started and focuses on the AWS console
- **Intermediate** - This section focuses on using the CLI
- **Advanced** - It's not too advanced, but adds KMS and shows how to access an RDS instance.

Each section has it's own **README.md** that will walk you through the steps. 

# What is SSM
Simple Systems Manager or Systems Manager or SSM is a suite of tools to allow management of EC2 instances. This demo will focus on the core component of secure server access. And you don't even need inbound or outbound internet access!

## Cost
This demo simulates a secure environment where there is no direct outbound access. To connect to AWS services, VPC Endpoints are used. We also spin up 2 x T3.Micro servers, a MySQL RDS instance and use a KMS key. 

| Description   | Hourly Cost | Monthly Cost |
|---------------|-------------|--------------|
| EC2 Linux     | $0.0132     | $9.636       |
| EC2 Windows   | $0.0224     | $16.352      |
| VPC Endpoints | $0.052      | $37.97       |
| KMS Key       | N/A         | $1.03        |
| RDS Instance  | $0.026      | $18.98       |

**NOTE 1:** Some aspects don't work as well in Melb right now (March 2023). While you can do most things, you may want to run this demo from Syd.

**NOTE 2:** You will need to have an existing account and a CLI profile. Since there are multiple ways to configure the previous, I will leave that up to you.

