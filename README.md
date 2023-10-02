# Deployment 4 Docmentation

## Purpose:
The purpose of deployment 4 was to set up a monitoring solution for the Amazon EC2 instance running our application. The primary objective was to continuously monitor real-time metrics of our EC2 instance, which may include CPU, memory, or RAM. This allows us to detect issues early while optimizing EC2 resources, as well as increasing the reliability of our application. Additionally, we configured a notification system that would allow us to be alert of any critical performance issues with our application with the EC2. This deployment motivates us to proactively address server-related issues ensuring a resilient application.

## Steps:
Before we started, we created our VPC with two available zones. Within each of those available zones, we have one public subnet and one private subnet (2 AZ, 2 public subnet, and 2 private subnet). We're also using a t2.medium EC2 instance within the public subnet of AZ A. This EC2 instance will also have a security attached to it To see the VPC diagram, click [here!](https://github.com/auzhangLABS/Deployment4/blob/main/images/vpcdiagram.drawio.png)
#### Replicating an online repository into our repository.
- `git clone {online repo url}`: Cloning an online repository into our local workspace. <br>
- `cd repo name`: Going into the repository folder. <br>
- `cd .git`: Going into the .git folder. <br>
- `nano config`: Here we are going to change the config file to push this repo to our remote repository by changing the `[remote = "origin"] url = {our remote repo url}`. <br>
- `git config --global user.name "Your Name"` `git config --global user.email "Your email"`: This allows us to set the global variable as your name and email.
- `git push`: Pushing it to our remote repository. <br>

Keep in mind, once you push it will prompt you to enter your username and password (token) for your GitHub.

#### Creating a Branch and making edits
- `git branch {branch name}`: Creating a branch. <br>
- `git switch {branch name}`: Change into that branch. <br>
- `nano Jenkinsfile`: Changing the Jenkins file within the text editor. <br>
- `git add Jenkinsfile`: adding Jenkins files to the stage area. <br>
- `git commit -m "you commit message" `" committing the file with a commit message. <br>
- `git switch main`: Changing back to main. <br>
- `git merge {branch name}`: Merging changes done on {branch name} onto main. <br>
- `git push`: Pushing to our remote repository. <br>

To see the updated Jenkinsfile click [here!](https://github.com/auzhangLABS/Deployment4/blob/main/Jenkinsfile)

#### Download Jenkins and other additional Packages
- `sudo apt-get update`: Update the repository information. <br>
To see the steps to install Jenkins, Python Virtual Environment, or Python package manager and installer, click [here!]( ) <br>
- `sudo apt-get install nginx`: Install the NGINX package. <br>
- `sudo nginx -v`: To verify the installation. <br>

Once, we downloaded NGINX, we configured our configuration found at this path: `/etc/nginx/sites-enabled/default` to change the port from 80 to 5000 as well as, changing the location block that handles requests to the root location. <br>
Put photo 1 here

#### Installing Monitoring tool onto EC2
To install Cloudwatch, we had to make sure that we had created an IAM role that allows us to use CloudWatch agent on Amazon EC2. Here, I'm showing how to use the command line to install the CloudWatch agent on Amazon EC2.
- `wget https://amazoncloudwatch-agent.s3.amazonaws.com/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb`: To download the Cloudwatch agent for the Ubuntu platform. <br>
- `sudo dpkg -i -E ./amazon-cloudwatch-agent.deb`: To install CloudWatch agent from the Debian Package. <br>
- `sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard`: Launch a CloudWatch Agent using the configuration wizard. <br>
- `cat file_config.json`: To see what you have configured. You must be within `/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.d/` folder. <br>

Here is what I configured for CloudWatch, see [here!]( ). Once you finish configuring it will show up in metrics within CloudWatch.

#### Running on Jenkins and server performance
For this deployment, we're creating a Multibranch Pipeline project. This allows Jenkins to create a set of Pipeline projects according to the branches in the repository. From examining the CloudWatch metrics on this EC2 instance, I was able to tell that the T2.medium was able to handle everything installed on it. Additionally, the CPU would increase once we're starting another build. For this application, we can also use T2.micro however it would perform much slower due to the fact the T2.micro has 1 vCPUs whereas the T2.medium has 2 vCPUs. Additionally, a T2.medium also comes with more memory (RAM) and better network performance for a higher price. 

#### Setting Monitoring Alarms
- To set up a Cloudwatch alarm, we go into Alarms and create an alarm. Next, you choose the metric you want to track and set the threshold, you want the alarm to trigger.
Put 1 photo here:

## System Design Diagram
To view the System Design Diagram, click [here!] (     )

## Issues/ Troubleshooting

## Optimization:













