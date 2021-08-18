# aws
Creating Server at AWS
&
SSHing into an AWS instance

1.log in AWS Management Console
2.under All services click->EC2->click->Launch Instance
3.select Amazon linux 2 AMI
4.click Review & launch
5.click Launch
Create Key pairs to ssh into our server to make changes
6.select -> Create new key pair
key pair name
7.my-blog-key
8.click Download key Pair
9.Launch Instances
ssh into our new server
10.move downloaded key pair file to .ssh folder
Now our instance should be done launching
11.goto aws console and click Services->EC2
12.we should see 1 Running Instances ->click it!
13.click on the running instance you created!
14.and find the public DNS property and copy it.

Change permissions for our .pem file in local console
15. chmod 400 ~/.ssh/my-blog-key.pem

Now ssh into our instance
16. ssh -i ~/.ssh/my-blog-key.pem ec2-user@_____paste copied DNS____
17. hit ENter!
SUccessfully ssh'ed into our running aws instance
