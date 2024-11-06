# my-custom-webpage

##Automating Website Deployment On An EC2 Server Using Bash Script

##Use Case

You are a Cloud Engineer for Tatenda TECH tasked with creating an Amazon EC2 Instance on AWS to host the organizations new website. Traditionally, Tatenda TECH hosts their websites on premise which involves purchasing very expensive infrastructure in a data center. The organization now wants to migrate to the cloud to decrease costs of capital expenditure and increase efficiency.

##Step 1: Configure and Launch Amazon EC2 Instance

Navigate to EC2 configuration page

Before we can configure the Amazon EC2 Instance, we need to first sign into your AWS IAM Account. After signing into your AWS account, navigate to the top of dashboard to search for the EC2 Service, click on “EC2”, then “Launch instance”, as seen below.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/0a32e8ba594149359319eeaf87ac9aa557fd3e01/aa.png)

##Configure and Launch EC2

The first field allows you to name your EC2 Instance. We also have the option to add tags. Tags act as a label which can be used to group resources in AWS, but for now, we will not add any.

Continue to select the desired Amazon AMI 

We will choose the “Amazon Linux 2 AMI” of the latest 5.10 Kernel with a 64-bit (x86) architecture, as seen below.

Proceed to the Instance Type options 

We will choose the “t2.micro” which is part of the AWS free tier. This instance type offers 750 hours free use of Linux and Windows instances each month for one year for new AWS customers.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/fd9f84c40e730f657c32f93cd53ef3de5ff286ef/ab.png)

Proceed to the Key pair option 

Click on the “Create new key pair” to create a new key pair, then enter your desired key pair name. Select “RSA” for key pair type and “.pem” for private key file format.

Click on “Create key pair”, as show below. The “.pm” file should automatically start downloading on your local system. Locate the file after the download is complete and store it in a safe directory. Later, we will use this key pair to connect to our EC2 Instance through ssh.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/1724dc69370a1e7401a41a2a226d1feb0382fdba/ac.png)

Continue to the Network settings 

Each custom AWS account network is automatically preconfigured with a default VPC when an EC2 Instance in launched. Also, we will keep “Auto-assign public IP” enabled, as this allows our EC2 Instance to automatically receive a public IP address to enable it to connect to the internet upon launch.

We will leave these setting in the default state, as seen below.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/0400917b7ca9fcd59d02d804031d3f5d625baee0/bb.png)

Continue to the Firewall (Security Group) settings 

As stated below, Security Groups serve as a set of Firewall rules that you can use to control traffic to your instance. We are going to allow “SSH” traffic to enable us to securely connect to our EC2 Instance and also “HTTPS” and “HTTP” so we can send requests and be served our Webpage in our browser over the internet.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/72b9fcf87ee1f4888b4ade9a57aa06cd296eebad/dc.png)

Make sure all configurations align with our previous steps, then click “Launch instance”, as seen below.
![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/7bb126e8bf2eeeeca3a0f864a7badc697f471366/dd.png)

##Step 2: SSH into Amazon EC2 Instance
Verify EC2 is running and navigate to options to connect to instance

Navigate to your EC2 Instances and verify that the new EC2 Instance we just launched is running.

Once we’ve verified our EC2 Instance is running, navigate to the top right pane, click “Actions” and select “Connect” as seen below.
![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/d9fec3957067457a1af3f76318334663a2f39b23/ff.png)

Click on the “SSH Client tab”, as show below. AWS is helpful enough to suggest some instructions on how we connect to the EC2 Instance, however, I will walk you through the whole process.
![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/036249615701c3bf9ceed6108c3a4b927d30083c/pp.png)

Use Key pair to ssh into EC2 Instance from CLI on local system
Locate the directory path where the downloaded key pair is stored and run the following command to change into that working directory 

To prevent others who may access your system from having unauthorized access to the key pair file, we need to modify the permissions of the file so only the user can read it.

Modify the permissions and verify the modifications were made by running the following two separate commands respectively

##Run ssh command passing in key pair file to authenticate into the EC2 Instance
We need to run the ssh command in your CLI and in addition, add the “-i” option to pass the key pair file at the same time to authenticate into your EC2 Instance.

![image alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/37fcda98fd0446efc964339a8fd9e3d1f4d0524f/ii.png)

###Step 3: Create Bash Script to automate Website deployment
Create new script directory and use nano to create and edit script file
Create a directory for the script and change your working directory into it by running the following separate commands respectively

![imagee alt](https://github.com/Tatenda-Prince/my-custom-webpage-/blob/36b2cc637d6b7a65690abbb67b2d8b0db7b1dcf6/ww.png)

The bash script below updates all yum package repositories then installs an Apache Web Server to serve content to our browsers. The server is then started and then enabled. The last line adds html code to an “index.html” file which enables our Server to serve our custom Website through our EC2 Instance.

c





