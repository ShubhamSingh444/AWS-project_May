AWS VPC Deployment Project
**Overview**
This project demonstrates how to create a highly resilient and secure Virtual Private Cloud (VPC) in AWS to support production-level applications. The setup includes multiple Availability Zones, public and private subnets, NAT gateways, an Application Load Balancer, and an Auto Scaling group.

Architecture Diagram

![vpc-example-private-subnets](https://github.com/ShubhamSingh444/AWS-project_May/assets/97628683/9b3e06a5-3e3b-4fa7-80b9-5ed4d152e188)
Picture taken from AWS

**Project Components**
1. VPC Setup
Created a VPC spanning two Availability Zones for high availability and fault tolerance.
2. Subnets Configuration
Public Subnets: Configured in each Availability Zone to host NAT gateways and load balancer nodes.
Private Subnets: Configured in each Availability Zone to host application servers.
3. NAT Gateways
Deployed NAT gateways in each Availability Zone to provide secure outbound internet connectivity for instances in private subnets.
4. Application Load Balancer
Implemented an Application Load Balancer to distribute incoming traffic across multiple EC2 instances, ensuring even load distribution and high availability.
5. Auto Scaling Group
Configured an Auto Scaling group to dynamically adjust the number of EC2 instances based on demand, ensuring optimal performance and cost-efficiency.
6. Security Enhancements
Set up Security Groups to control inbound and outbound traffic, allowing only necessary communication to and from the instances.
7. Gateway VPC Endpoint
Added an S3 Gateway Endpoint to enable secure and efficient access to Amazon S3 from the private subnets.

**Routing**
Public Subnets Route Table: Includes routes to the internet gateway.
Private Subnets Route Table: Includes routes to the NAT gateway and S3 gateway endpoint.

**Security Groups**
Configured to allow traffic from the load balancer over the listener port and protocol, and to allow health check traffic.
Deployment Steps
Create the VPC
Open the Amazon VPC console.
Choose Create VPC and configure:
Name tag
IPv4 CIDR block
IPv6 CIDR block (if required)
Number of Availability Zones: 2
Number of public subnets: 2
Number of private subnets: 2
NAT gateways: 1 per AZ
VPC endpoints: S3 Gateway (optional)
DNS options: Enable DNS hostnames (optional)
Click Create VPC.
Deploy Your Application
Create a Launch Template:
Specify configuration information needed to launch EC2 instances using Amazon EC2 Auto Scaling.
Create an Auto Scaling Group:
Define the minimum, maximum, and desired number of instances.
Create a Load Balancer:
Distribute traffic evenly across instances and attach it to the Auto Scaling group.
Testing and Validation
Ensure that the instances in the private subnets can connect to the internet via the NAT gateways.
Verify that the load balancer distributes traffic evenly across the instances.
Check security group rules to confirm that only necessary traffic is allowed.
Clean Up
Terminate resources and delete the VPC to avoid incurring costs when no longer needed.
What We Learned
High Availability Architecture: Designing applications for high availability using multiple Availability Zones.
Network Security: Implementing network security best practices with NAT gateways and security groups.
Scalability: Utilizing auto-scaling for handling varying loads.
AWS Services Integration: Effective integration of AWS services like VPC, EC2, Auto Scaling, Load Balancers, and S3.
Conclusion
This project was a significant step in mastering cloud infrastructure design and deployment. The skills and knowledge gained will be valuable for future projects and further exploration of AWS capabilities.
