# Extras

If you want to play around more with SSM, have a look at **State Manager** and **Associations**.
**Associations** combine **Documents** with cron expressions to manage instances. My favourite use is to stop & start EC2 instances by tag. It's much easier than using **lambdas** or **Event Bus**. The only trick is that the cron doesn't quite act as you'd expect. Mainly, you can't do day ranges, e.g. MON-FRI. You can do a wildcard.

Have a look at the 01-State-Manager template and modify the time so you can see it work during the demo. The EC2 template adds a tag to the Linux instance.

## Default Host Management Configuration
In mid-Feb, AWS announced Default Host Management Configuration \(DHMC\). This lets you automatically add servers to Fleet Manager without needing the SSM policy in your instance profile. You do need an instance with IMDSv2 enabled and SSM agent v3.2.582.0 or later.

If you want to test this out, run up an Amazon Linux 2023 instance ... but don't use a t3a. The AMD instances don't currently have the right agent version.