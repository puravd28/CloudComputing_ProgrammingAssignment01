# CloudComputing_ProgrammingAssignment01
Steps to perform and complete the assignment 

Log In to AWS: Use the link from  professor to access  AWS account. Sign up with  NJIT email if you don’t have an account. You'll also need the free AWS credits provided.

Start  AWS Lab: Go to the AWS Academy course created by  professor. In the lab section, click “Start Lab.” Make sure the lab status is green, indicating it’s active.

Set Up Credentials: Copy  AWS access key, secret key, and session token from the lab details. Paste them into  ~/.aws/credentials file. Also, download the PEM file for SSH access to  EC2 instances.

Create EC2 Instances:
Go to the EC2 dashboard.

Launch two instances:
Choose the Amazon Linux 2 AMI.
Select the t2.micro instance type.
Use the pre-populated key pair.
Create a security group allowing SSH, HTTP, and HTTPS traffic from  IP only.
Name  instances (e.g., EC2-A and EC2-B).

Add IAM Roles:
Select each instance, go to "Actions" > "Security" > "Modify IAM role," and attach the LabInstanceProfile.
Ensure the role has access to S3, SQS, and Rekognition. If not, go to IAM roles and attach the necessary permissions.

Prepare  Java Programs:
You’ll have two Java programs: one for detecting objects (run on EC2-A) and one for detecting text (run on EC2-B). Ensure you have JAR files for both programs.

Upload JAR Files: Use a file transfer tool (like Cyberduck for Mac or WinSCP for Windows) to upload  JAR files to the respective EC2 instances. Connect using the username ec2-user.

SSH into EC2 Instances:
Open a terminal and navigate to where  PEM file is saved.
Change permissions on the PEM file with chmod 400 labsuser.pem.
Copy the public IP address of  instance from the AWS console.
SSH into the instance using ssh -i <filename>.pem ec2-user@<public-ip>.

Run Programs:
Configure AWS CLI on  terminal with aws configure (set the region to us-east-1).
Run the object detection program on EC2-A with java -jar <JAR_FILE>.jar.
Run the text detection program on EC2-B and direct output to a file using java -jar <JAR_FILE>.jar > output.txt.

Check Results:
After running the programs, check the SQS queue for messages pushed by the object detection program.
The text detection program on EC2-B will create an output.txt file with details about images containing both cars and text.
This process will help you set up and run  Java applications on AWS effectively!
