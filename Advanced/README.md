# Advanced Configurations

Some of the advanced options within **Fleet Manager** require an encrypted connection to SSM. I have included a new **01-VPCEndpoint.yaml** file that creates an endpoint for KMS [Note: I've often forgotten this step and wondered why I my KMS wasn't working]. The other file **02-KMS-SSM-key.yaml** creates the KMS CMK with appropriate permissions to allow SSM access.

The KMS access is configured within **Session Manager** Preferences.

![alt text](../Images/Advanced-01-SessionMgr-Edit.png "Session Manager preferences screen")

Select Edit, check the **Enable KMS** option, then select the key **alias/SSMKey**.

![alt text](../Images/Advanced-02-SessionMgr-AddKMS.png "Preferences screen with KMS options")

Finally, remember to **Save**

![alt text](../Images/Advanced-03-SessionMgr-Save.png "Save button for preferences")

After this, your shell sessions will now be encrypted.
```
% 
% aws ssm start-session \
    --target $INSTANCE \
    --region ap-southeast-2

Starting session with SessionId: <user>-01bc24f3b95e34a7e
This session is encrypted using AWS KMS.
sh-4.2$ 
sh-4.2$ whoami
ssm-user
sh-4.2$ 
sh-4.2$ exit
exit


Exiting session with sessionId: <user>-01bc24f3b95e34a7e.

jasonwood@Faramir .aws %
```

Now is also an excellent time to look at **Fleet Manager** and see what you can do with KMS disabled. The base functionality will still work, but some connection items require KMS. The KMS requirement is more prevalent with Windows tools.


```
aws ssm start-session \
    --target $INSTANCE \
    --region ap-southeast-2 \
    --document-name AWS-StartPortForwardingSessionToRemoteHost \
    --parameters '{"host":["my-rds-instance.cyr2kwgetcxa.ap-southeast-2.rds.amazonaws.com"],"portNumber":["3306"], "localPortNumber":["3306"]}'
```
