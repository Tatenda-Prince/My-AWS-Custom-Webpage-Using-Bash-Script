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

Continue to select the desired Amazon AMI —

We will choose the “Amazon Linux 2 AMI” of the latest 5.10 Kernel with a 64-bit (x86) architecture, as seen below.

Proceed to the Instance Type options —

We will choose the “t2.micro” which is part of the AWS free tier. This instance type offers 750 hours free use of Linux and Windows instances each month for one year for new AWS customers.
