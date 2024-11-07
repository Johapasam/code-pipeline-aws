This README provides the steps for deploying a User Information Form using index.html and appspec.yml with AWS EC2, RDS MySQL, IAM, CodeDeploy, and CodePipeline.

Steps to Deploy

1. Create IAM Roles
EC2 Role
CodeDeploy Role

2. Launch EC2 Instance
Choose Amazon Linux 2 as the AMI.
Select an instance type like t2.micro (free tier eligible).
Attach the EC2 IAM role created earlier to this instance.
Configure User Data to install Apache and PHP on launch.
Configure a Security Group to allow HTTP (port 80) and SSH (port 22).

3. Set Up RDS MySQL Database
Create a new RDS MySQL instance in the same region as EC2.
Configure RDS Security Group to allow connections from the EC2 instance on port 3306.
Use MySQL Workbench or AWS RDS management console to set up the database and create the necessary tables.

4. Prepare GitHub Repository
Create a repository on GitHub and push the following files:
index.html: The HTML form that collects user data.
appspec.yml: Defines deployment instructions for CodeDeploy.

5. Set Up CodeDeploy
Create a CodeDeploy application in the AWS Management Console.
Create a Deployment Group that links the EC2 instance(s) where the code will be deployed.
Ensure the CodeDeploy IAM role has the correct permissions to interact with EC2 instances.

6. Set Up CodePipeline
Source Stage: Link the GitHub repository where the code is stored.
Deploy Stage: Set the deploy provider to CodeDeploy to deploy the application to the EC2 instance.

7. Deploy the Application
Trigger the CodePipeline to deploy the code from GitHub to the EC2 instance.
Monitor the progress of the deployment in the AWS Management Console.

8. Test the Application
After the deployment is successful, access the application through the EC2 instance’s public IP address.
Ensure that the form is visible and that user data can be successfully submitted and stored in the RDS MySQL database.
License

MIT License.
