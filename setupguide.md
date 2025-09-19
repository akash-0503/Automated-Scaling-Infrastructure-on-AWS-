step 1 : first we should have the AWS account created or with IAM User you can login.
=
<img width="1920" height="949" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/fb7c1be8-0e0b-4aba-960a-a02d622ec559" />

Step 2.AMI creation.
=

An EC2 instance was launched using Amazon Linux 2023. After connecting via SSH, necessary software such as Apache (httpd) was installed and configured to display a basic webpage. Once the instance was set up, it was converted into an Amazon Machine Image (AMI) to enable consistent replication of the configured environment.
<img width="1896" height="917" alt="image" src="https://github.com/user-attachments/assets/3113e2c7-fa92-4f8e-a7bc-2eb818480710" />

Step 3. Security Group Configuration:
=


A security group was created to control access to the instance. Inbound rules were added to allow HTTP (port 80) from anywhere and SSH (port 22) from a specific IP. Outbound rules were left at default to permit all traffic. This ensured secure and functional access for both web and administrative purposes.
: Inbound rules showing HTTP and SSH
<img width="1890" height="916" alt="image" src="https://github.com/user-attachments/assets/6eed13a2-cd14-4181-8c54-6f64e36d5cb0" />

Step 4. Launch Template Configuration.
=
Next, a Launch Template was created using the previously configured AMI. This template specified the instance type, key pair, and other configurations such as startup scripts (if any). The Launch Template serves as a reference for<img width="1895" height="917" alt="image" src="https://github.com/user-attachments/assets/e817497a-7d27-440b-921b-6aa8a515e00e" />
the Auto Scaling Group (ASG) to launch new instances based on the same settings, allowing for consistency and scalability in the infrastructure

Step 5. Auto Scaling Group Setup:
=
An Auto Scaling Group (ASG) was configured with the Launch Template. It was set with a minimum of 1, desired capacity of 2, and a maximum of 3 instances. Health checks and a target tracking scaling policy were configured to maintain optimal performance based on CPU usage.
: ASG creation page with minimum, maximum, and desired capacity settings.
<img width="1892" height="910" alt="image" src="https://github.com/user-attachments/assets/c352877b-5090-4f0b-9f71-28ddd04623ac" />
<img width="1895" height="917" alt="image" src="https://github.com/user-attachments/assets/92d5b2db-4d32-4006-9af7-93f15d8ed10e" />

Step 6. Load Balancer and Target Group
=
An Application Load Balancer (ALB) was created and linked to a Target Group. The ASG was associated with this Target Group to ensure traffic was distributed evenly across healthy instances.

<img width="1887" height="908" alt="image" src="https://github.com/user-attachments/assets/5508f2bd-3ff6-4e99-8e18-6d97d96b9f45" />
<img width="1906" height="557" alt="image" src="https://github.com/user-attachments/assets/ea496db5-a811-43a3-953e-0f691db3626e" />

Step 7. Testing and Scaling Verification.
=
The final step involved testing the setup by simulating a scaling event. This was done by generating CPU load on the instances, triggering the ASG to scale in or out. The ALB’s traffic distribution was verified to ensure that requests were being appropriately routed to healthy instances. The scaling policies worked as expected, confirming that the system could handle varying levels of load and scale automatically as needed
<img width="1734" height="801" alt="Screenshot 2025-09-19 165505" src="https://github.com/user-attachments/assets/23463f4b-2c7a-480e-a5ab-1bc1da72f0b6" />
