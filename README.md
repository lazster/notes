# notes
#----This is a quick guide on how to set up sessions manager on your EC2 instance and enable SSH connections through SSM.--


Setting up sessions manager on EC2 instance
1. Create IAM instance profile to allow Sessions Manager to connect to your instance (this is not enabled by default)
You can do that either by creating a new IAM role with Session Manager permissions or by adding inline policy permissions to an existing role already attached to our instance.

To create/add instance profile:

Go to IAM and click on Create role
Select EC2 as trusted entity.EC2 truested entity
Add AmazonSSMManagedInstanceCore policy to your role or AmazonSSMFullAccess if you require to grant all Systems Manager permissions and click next.Adding AmazonSSMManagedInstanceCore permission to a new role
Add tags and then click Create role.

To add SSM permissions to an existing role, find the role that is attached to the instance, and then add SSM permissions as an inline policy.

2. Next add newly created role as your instance profile:
Go to EC2 instances, select the instance you would like to enable SSM on.
Click on Actions, select Security, and then Modify IAM roleModifying IAM role
Next select IAM role we have created in the previous stepSelecting IAM role
3. You can now connect to your instance through Session Manager.Connect to your instance!

#----start session manager--------------------------
1. navigate to instance
2. click connect button then make sure to use **session manager** tab (not EC2 instance connect)
3. 

-------------
to sort a sandbox db that wasnt accessable over web i did this 
edited subnet to flip Auto-assign public IPv4 address= Yes
edited route table to add this route: "destination= 0.0.0.0/0	target= <insert your internet gateway name here> eg igw-0143349a4be19dde2"
