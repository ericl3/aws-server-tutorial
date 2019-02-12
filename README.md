# AWS Tutorial CS308
## AWS EC2
EC2, which stands for Elastic Compute Cloud, is a service which provides virtual machines for users to run their own applications on the cloud. It forms the bedrock for many other AWS services, such as AWS Elastic Beanstalk, which will be used later in the tutorial. 
### Getting started with EC2
#### Creating an instance
Navigate to the [AWS Console](console.aws.amazon.com) and click on EC2 from the "Compute" menu. Then click Launch Instance to begin. First you will be prompted to choose an OS, for this tutorial keep the default selection of Amazon Linux 2 AMI, click Select. Then you will be prompted to choose an instance type, once again keep the deafult of t2.micro, which will provide enough storage and performance. Then click "Launch". You will then be prompted to create a new key pair to authenticate yourself to the servers. This will allow you to access the servers from your local machine's console, while not allowing anyone without the private key access. Download your key pair, and wait for your server to launch.  
#### Connecting to your EC2 instance
Now that the server is up and running, you will connect to it from your local machine. Ensure you have SSH by typing ssh into the command line of your preferred console (the default being Terminal for Mac users). Change directories to the folder containing the .pem file with the key pair (do this by typing `<cd Documents/Tutorial>` for example). You will need to change permissions of the private key so you can read it, do this by typing `<chmod 400 _______.pem>` Then you are ready to connect to your instance! Then on your command line you must type ssh -i /path/my-key-pair.pem user_name@public_dns_name. Plug in the proper values. For user_name it is probably ec2-user, and you can find the public_dns_name in the EC2 console. The console may respond asking if you wish to continue connecting because authenticity can't be established, type yes. Now you are connected to your EC2 instance, and can use it just as you use your local machine.
## Elastic Beanstalk
Now that you are familiar with the standard EC2 instance that AWS offers, let's get more robust. Elastic Beanstalk (EBS) is an AWS PaaS that allows you to upload and deploy applications, and run them on top of an EC2 instance. 
>By using Docker with Elastic Beanstalk, you have an infrastructure that automatically handles the details of capacity provisioning, load >balancing, scaling, and application health monitoring.
### Getting Started
#### Updating the Webapp
Before you can upload your webapp to the cloud, a file must be added 
Open up the AWS Elastic Beanstalk console. 
#### Deploying to EBS 
Once you have your Dockerfile and Dockerrun.aws.json files ready for use, uploading the webapp to the cloud is very simple. Open the AWS EBS console, and click Create New Application. Put in an application name like "AWS-Tutorial" and click Create. Then create a new environment in this application. Choose web server environment, and choose Docker from the preconfigured platform. In the Application code section, choose "upload your code", and select the .zip file containing your web app. Then click create. It will take a few minutes to launch, but once complete, you should be able to return to the environment page, and click on the url that now has the live version of your webapp! 
