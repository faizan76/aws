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

Setting up an AWS instance
1.//install git
sudo yum install git
2.y (Enter)
3.//Install npm node->from below
4.https://lnkd.in/gEZS9yU
5.follow and copy and run the above commands
//check your node -v and install
6.nvm install 10.15.3
7.//install latest npm
npm install -g npm@latest
8.//Install mongodb
https://lnkd.in/gip77i8
click -> Amazon Linux 2
follow and copy and run
sudo nano /etc/yum...
copy pasta...
ctrl+o to save
Enter
ctrl+x to close
9.sudo yum install -y mongodb-org

//Now make sure mongodb is running on our instance.
10.sudo service mongod start
//run mongo shell
11.mongo
12.insert some documents
>use my-blog
>db.articles.insert([
{
name:'learn-react',
upvotes:0,
comments:[],
},
{
name:'learn-node',
upvotes:0,
comments:[],
},
])

39.
//Running a full-stack app on AWS
1.clone git Project repo
git clone https://...
2.ls
3.cd my-blog
4.npm install
5.npm start //or
npm install -g forever
5.1 forever start -c "npm start" .
5.2 //check if running
>forever list

//Since our app is running on port 8000 but we want to access it on http port which is 80.
so run..
6. sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8000


//To access the running instance of our app through a browser
goto
1.https//aws.amazon.com
2.click on the running instance
3.scroll down to security groups
4.note down the first value 
5.e.g(launch-wizard-2)
6.in side pane - scroll down to Security groups
7.select the security group your app belongs to.
8.Now at the bottom click on Inbound tab.
9.click Edit
10.click Add Rule
11.select Type:HTTP
12.select Source -> Anywhere
13.click save
14.Now goto instances from side pane
15.Select the running instance and copy Public DNS 
16.Paste it in Browser new tab
Done!
