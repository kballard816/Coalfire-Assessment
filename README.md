DESCRIPTION:
I have created Terraform for a simple VPC as outlined in my scenario including:

  • 1 VPC – 10.1.0.0/16
  - 4 subnets (spread evenly across two availability zones)
  - Sub1 – 10.1.0.0/24 (should be accessible from internet)
  - Sub2 – 10.1.1.0/24 (should be accessible from internet)
  -Sub3 – 10.1.2.0/24 (should NOT be accessible from internet)
  - Sub4 – 10.1.3.0/24 (should NOT be accessible from internet)
  • 1 EC2 instance running Red Hat Linux in subnet sub2
  - 20 GB storage
  - t2.micro
  - 1 auto scaling group (ASG) that will spread out instances across subnets sub3 and sub4
  - Use Red Hat Linux
  - 20 GB storage
  - Script the installation of Apache web server (httpd) on these instances
  - Add an IAM role to your ASG hosts that can read from the "images" bucket
  - 2 minimum, 6 maximum hosts
  - t2.micro
  • 1 application load balancer (ALB) that listens on TCP port 80 (HTTP) and forwards traffic to the ASG in subnets sub3 and sub4 on port 443
  • Security groups should be used to allow necessary traffic
  • An IAM role that can write to the logs to log bucket from ALL EC2s provisioned.
  • 1 S3 bucket: “Images” with a folder called archive
  - “Memes” folder - move objects older than 90 days to glacier.
  • 1 S3 bucket: “Logs” with two folders and the following lifecycle policies
  - “Active folder” - move objects older than 90 days to glacier.
  - “Inactive folder” - delete objects older than 90 days.

Terraform V.1.6.0

GENERAL NOTES: 

This Terraform architecture has been created using some made up and generic names for this assessment (Example is Web Load Balancer being named "web_lb").

LucidChart diagram: Exact names left of the diagram as those are made up and for brevity sake.

LucidChart invite link: https://lucid.app/lucidchart/45bbe232-b69c-4583-bb09-5cc1f507f91f/edit?viewport_loc=-1140%2C-660%2C2155%2C1093%2C0_0&invitationId=inv_0d816d29-8453-463e-8dd7-f2615918349e



RESOURCES AND REFERENCES USED:

https://github.com/Coalfire-CF

https://github.com/orgs/Coalfire-CF/repositories?type=public&q=terraform-aws

https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/terraform-aws-provider-best-practices/terraform-aws-provider-best-practices.pdf

deepseek.com
