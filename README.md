# DevOps 

## What is DevOps?
DevOps is a culture and way of working that improves application delivery by focusing on:

- **Automation**
- **Quality**
- **Continuous Monitoring**
- **Continuous Testing**

**Main goal:** Deliver applications faster, reliably, and with less manual effort.

## Why DevOps?
Traditional software delivery involved multiple teams and many manual steps, making releases slow.

DevOps helps to:

- Reduce manual work
- Improve collaboration between teams
- Automate the delivery process
- Release features and bug fixes faster
- Maintain application quality
- Detect issues through monitoring and testing

## DevOps Delivery Flow

Developer → Code Repository → Build/Release → Testing → Staging → Production → Customer

## Four Important Pillars

1. **Automation:** Automate repetitive tasks and deployments.
2. **Quality:** Maintain application and code quality.
3. **Monitoring:** Track application health and detect failures.
4. **Testing:** Continuously test the application to find bugs early.

## DevOps Interview Definition
> DevOps is a process of improving application delivery by ensuring proper automation, maintaining quality, and implementing continuous monitoring and testing.


# DevOps  — Software Development Life Cycle (SDLC)

## What is SDLC?
SDLC stands for **Software Development Life Cycle**.

It is a standard process used to **plan, design, develop, test, and deploy** high-quality software.

**Goal:** Deliver a high-quality product that meets customer expectations.

## SDLC Phases

Planning & Requirements → Defining → Designing → Building → Testing → Deployment

The process is repeated for every new feature.

## 1. Planning & Requirements
- Collect customer feedback and business requirements.
- Understand what users need.
- Decide whether the feature is useful.
- Main participants: **Product Owner, Business Analyst, and senior members**.

### SRS Document
**SRS = Software Requirement Specification**

It contains the collected and clearly defined software requirements.

## 2. Designing
Designers and architects decide how the software will work.

### HLD — High-Level Design
Describes the overall system architecture, such as:
- Scalability
- High availability
- Database choice
- Number of application replicas

### LLD — Low-Level Design
Describes detailed implementation, such as:
- Modules and functions
- Database calls
- Function arguments
- Expected responses
- Programming-level details

## 3. Building / Development
- Developers write the application code.
- Code is reviewed by team members.
- Code is pushed to a source-code repository such as **Git**.

## 4. Testing
- The application is tested for quality and correctness.
- QA/QE engineers usually perform testing.
- The application may be deployed to a testing or staging server.

## 5. Deployment
- The tested application is promoted to the **production environment**.
- The final application becomes available to customers.

## DevOps Role in SDLC
A DevOps engineer primarily focuses on automating and improving:

1. **Building**
2. **Testing**
3. **Deployment**

### Main Responsibilities
- Automate repetitive processes.
- Reduce manual intervention.
- Speed up software delivery.
- Improve efficiency and reliability.

**Important:** A DevOps engineer may collaborate in all SDLC phases, but the primary focus is automation of build, test, and deployment.

## Agile Methodology
- Agile follows SDLC phases in short, repeated **Sprints**.
- Small features are developed, tested, and delivered incrementally.

## Interview Answer
> SDLC is a standard process used to plan, design, develop, test, and deploy high-quality software. As a DevOps engineer, I primarily focus on automating the build, testing, and deployment phases to improve delivery efficiency.



## Day 3 — Organization Roles, SDLC and Jira

### 1. Requirement Flow

Customers → Business Analyst → Product Manager → Product Owner → Solutions Architect → Scrum Team

### 2. Important Roles

- **Customer:** Gives feedback and requirements.
- **Business Analyst (BA):** Collects requirements and prepares the BRD.
- **Product Manager (PM):** Defines product vision and prioritizes requirements.
- **Product Owner (PO):** Converts requirements into epics and stories; manages the backlog.
- **Solutions Architect (SA):** Creates the technical design using HLD and LLD.
- **Developers:** Write and implement application code.
- **DevOps Engineer:** Provides infrastructure, tools, automation, and CI/CD pipelines.
- **QA/QE Engineer:** Tests application quality and correctness.
- **DBA:** Manages databases.
- **SRE:** Maintains reliability, availability, monitoring, dashboards, and alerts.
- **Technical Writer:** Documents features and technical information.

### 3. Scrum Team

A Scrum team can include developers, DevOps engineers, QA engineers, database administrators, and technical writers. They work together to complete requirements.

### 4. SDLC Phases

1. **Planning:** Gather requirements.
2. **Analysis:** Check feasibility and priority.
3. **Design:** Prepare HLD and LLD.
4. **Implementation:** Developers, DevOps, and QA work together.
5. **Testing and Integration:** Test and integrate the application.
6. **Maintenance:** Maintain reliability and availability.

### 5. DevOps Engineer's Role

- Create infrastructure and required tools.
- Automate manual processes.
- Build CI/CD pipelines.
- Integrate automated testing.
- Add security to pipelines.
- Identify SDLC gaps.
- Improve delivery speed and efficiency.

### 6. Jira

**Jira** is a project-management and task-tracking tool.

It helps teams to:

- Create epics, stories, and tasks.
- Assign work to team members.
- Track task progress.
- Update daily status.
- Identify blocked tasks.
- Help management monitor projects.

### 7. Jira Terms

- **Epic:** A large feature or requirement.
- **Story:** A smaller task under an epic.
- **Backlog:** List of pending work.
- **Sprint:** Planned work for usually 2–3 weeks.
- **Sprint Planning:** Meeting to plan sprint tasks.
- **Sprint Retrospective:** Meeting to review completed and remaining work.
- **Task Flow:** To Do → In Progress → In Review → Done.

### 8. Key Interview Point

A DevOps engineer usually does not receive requirements directly from customers. Requirements pass through different roles and reach the Scrum team. DevOps engineers provide infrastructure, automate processes, and improve the software delivery lifecycle.


## — Virtual Machines and Virtualization

### 1. What Is a Server?

A server is a computer system used to host applications so users can access them over a network or the internet.

Examples:
- Google
- Amazon
- Other websites and applications

### 2. The Problem with Physical Servers

Suppose an organization buys a physical server with:

- 100 GB RAM
- 100 CPU cores

But an application needs only:

- 4 GB RAM
- 4 CPU cores

Most of the server's resources remain unused. This causes resource wastage and inefficient usage.

### 3. Virtualization

**Virtualization** is the process of dividing one physical server into multiple logical virtual machines.

These virtual machines share the resources of the physical server while working as separate computer systems.

### 4. Hypervisor

A **hypervisor** is software that creates and manages virtual machines on a physical server.

It performs logical separation of the physical server's resources.

Examples of hypervisors:
- VMware
- Xen

### 5. Virtual Machine (VM)

A **Virtual Machine** is a logical computer system created inside a physical server.

A VM has:
- Its own allocated CPU
- Its own allocated memory
- Its own storage and operating system
- Logical isolation from other VMs

Multiple teams can use different VMs on the same physical server without directly interfering with each other.

### 6. Physical Server vs Virtual Machine

| Physical Server | Virtual Machine |
|---|---|
| Real hardware | Software-based logical system |
| Uses physical resources directly | Uses allocated shared resources |
| Usually supports one main environment | Multiple VMs can run on one server |
| Resource utilization may be low | Improves resource utilization |

### 7. Virtual Machines in Cloud Platforms

Cloud providers such as AWS, Microsoft Azure, and Google Cloud use physical servers inside data centers.

The general process is:

1. Cloud provider installs physical servers in a data center.
2. Hypervisors are installed on these physical servers.
3. A user requests a VM with specific CPU and RAM.
4. The cloud platform selects a suitable physical server.
5. The hypervisor creates the VM.
6. The user receives access details such as an IP address and key.

### 8. AWS Example

In AWS, a virtual machine is commonly called an **EC2 instance**.

A user can select:
- Region, such as Mumbai or Singapore
- CPU configuration
- RAM
- Storage
- Operating system

The user gets logical access to the VM but does not physically own or access the underlying server.

### 9. Regions and Latency

A cloud region is a geographical location where cloud data centers are available.

Choosing a region closer to users generally reduces **latency**, which means less delay in communication.

### 10. Benefits of Virtualization

- Better resource utilization
- Reduced hardware wastage
- Multiple environments on one physical server
- Isolation between virtual machines
- Flexible resource allocation
- Supports cloud computing
- Reduces infrastructure cost

### 11. Key Interview Answer

A virtual machine is a software-based computer system created on a physical server using a hypervisor. It has its own allocated CPU, memory, storage, and operating system. Virtualization improves resource utilization by allowing multiple isolated VMs to run on one physical server.



## Day 4 — Virtual Machines 

### 1. Creating Virtual Machines

Virtual machines can be created using cloud providers such as AWS, Azure, Google Cloud, and DigitalOcean.

In AWS, a virtual machine is called an **EC2 instance**.

### 2. Manual Creation

A VM can be created through the cloud console:

1. Sign in to the cloud console.
2. Select the required service.
3. Choose the operating system.
4. Select CPU and memory.
5. Configure authentication.
6. Launch the instance.
7. Get the IP address and instance details.

Manual creation is suitable for a few resources but becomes slow and repetitive for many requests.

### 3. Automation

Automation uses scripts or tools to create resources without repeated manual work.

Benefits:
- Saves time
- Reduces human errors
- Creates multiple resources quickly
- Improves efficiency
- Provides consistency

### 4. AWS API

AWS provides APIs for its services.

Examples:
- **EC2 API:** Manage virtual machines.
- **S3 API:** Manage storage.
- **EBS API:** Manage volumes.

An API request must be:

- **Valid:** Follows the expected format.
- **Authenticated:** The user is verified.
- **Authorized:** The user has permission.

### 5. Methods to Automate AWS

| Method | Purpose |
|---|---|
| **AWS CLI** | Manage AWS using terminal commands |
| **AWS API** | Directly send requests programmatically |
| **Boto3** | Python SDK for AWS automation |
| **CloudFormation** | Create infrastructure using templates |
| **AWS CDK** | Define infrastructure using programming languages |
| **Terraform** | Automate infrastructure across multiple cloud providers |

### 6. Terraform

Terraform is an **Infrastructure as Code (IaC)** tool.

It is useful when an organization uses:
- AWS
- Azure
- Google Cloud
- Multiple cloud providers
- Hybrid-cloud infrastructure

### 7. Hybrid Cloud

A hybrid-cloud model uses infrastructure from multiple cloud platforms or combines cloud and on-premise infrastructure.

Example:
- AI/ML workloads on Google Cloud
- Other services or databases on AWS

Terraform is useful because it can manage resources across different platforms.

### 8. AWS CDK

AWS CDK means **Cloud Development Kit**.

It is closely integrated with AWS and allows infrastructure to be written using programming languages.

For an AWS-focused organization, CDK can be a good choice.

### 9. Creating an EC2 Instance

Basic AWS steps:

1. Open AWS Console.
2. Search for **EC2**.
3. Click **Launch Instance**.
4. Enter an instance name.
5. Select an OS, such as Ubuntu.
6. Select a free-tier eligible instance.
7. Create or select a key pair.
8. Configure required settings.
9. Click **Launch Instance**.
10. Wait until the instance is running.

### 10. Key Pair

A key pair is used to securely access an EC2 instance.

- The public key is attached to the instance.
- The private key is downloaded to the local computer.
- The private key must be stored safely.
- Losing it may prevent login access.

### 11. Free Tier

Free-tier instances have limited resources and usage.

Always check:
- Instance type
- Free-tier eligibility
- Storage usage
- Running resources
- Billing details

Paid or excessive usage may cause charges.

### 12. Azure VM

The Azure process is similar:

1. Open Azure Portal.
2. Sign in or create an account.
3. Select **Virtual Machines**.
4. Click **Create**.
5. Choose OS and machine size.
6. Configure authentication.
7. Review and create the VM.

### 13. Interview Points

- AWS EC2 is a virtual machine service.
- VMs can be created manually or through automation.
- Boto3 is used to automate AWS with Python.
- CloudFormation creates infrastructure using templates.
- AWS CDK defines AWS infrastructure using programming languages.
- Terraform is useful for multi-cloud and hybrid-cloud infrastructure.
- Automation improves speed, consistency, and efficiency.

# DevOps Zero to Hero — Short Notes

## Day 5 — EC2 Login and AWS Automation

### 1. Connecting to an EC2 Instance

An AWS EC2 instance can be accessed in two main ways:

- Through the AWS Console
- Through a local terminal using SSH

The AWS Console is easy for beginners, but it is not efficient when managing many virtual machines.

### 2. Connecting Through AWS Console

1. Open the AWS Console.
2. Go to the EC2 Dashboard.
3. Select the running instance.
4. Click the Instance ID.
5. Click **Connect**.
6. Select the browser-based connection option.
7. Click **Connect** again.

This opens a terminal session inside the EC2 instance.

### 3. Connecting Through a Local Terminal

A local terminal is useful for DevOps engineers because it allows faster and repeated access to servers.

Examples:

- Windows Terminal
- PuTTY
- MobaXterm
- NoMachine
- iTerm for macOS

### 4. Public IP and Private IP

- **Public IP:** Used to connect to the EC2 instance from an external computer.
- **Private IP:** Used for communication within the AWS network or VPC.

For connecting from a personal laptop, the public IP is generally used.

### 5. SSH Connection

SSH means **Secure Shell**. It is used to securely connect to a remote server.

```bash
ssh ubuntu@<PUBLIC-IP>
```

To use a private key:

```bash
ssh -i <path-to-key.pem> ubuntu@<PUBLIC-IP>
```

Here, `-i` specifies the identity/private key file.

### 6. PEM File Permissions

A `.pem` file contains sensitive private-key information. Its permissions must be restricted.

```bash
chmod 600 <path-to-key.pem>
```

If the permissions are too open, SSH may reject the connection.

**Never share your private key.**

### 7. Testing the Connection

After connecting to the instance, Linux commands can be executed remotely.

```bash
ls
touch example.txt
```

The file is created inside the EC2 instance, not on the local computer.

### 8. Stop vs Terminate

- **Stop:** Temporarily stops the instance. It can usually be started again.
- **Terminate:** Deletes the instance permanently.

Stop or terminate unused resources to avoid unnecessary charges. Also check storage and other related costs.

### 9. AWS CLI

AWS CLI means **Amazon Web Services Command Line Interface**.

It allows users to interact with AWS services through terminal commands instead of the AWS Console.

It can manage services such as:

- EC2
- S3
- EBS
- IAM
- Many other AWS services

### 10. Installing and Verifying AWS CLI

Install AWS CLI according to the operating system:

- Windows: MSI installer
- macOS: Official installer or package manager
- Linux: Official installation method

Verify the installation:

```bash
aws --version
```

### 11. AWS Access Keys

AWS CLI requires authentication.

The credentials include:

- **Access Key ID**
- **Secret Access Key**

These keys are sensitive and must never be shared publicly.

### 12. Configuring AWS CLI

Run:

```bash
aws configure
```

It asks for:

1. AWS Access Key ID
2. AWS Secret Access Key
3. Default region
4. Default output format

Example:

```text
Default region: us-east-1
Default output format: json
```

After configuration, AWS CLI can communicate with the AWS account.

### 13. Useful AWS CLI Commands

List S3 buckets:

```bash
aws s3 ls
```

Create an S3 bucket:

```bash
aws s3 mb s3://<unique-bucket-name>
```

S3 bucket names must be globally unique.

EC2 commands can be found in the AWS documentation. Creating an instance requires details such as:

- AMI ID
- Instance type
- Key pair
- Security group
- Subnet ID

### 14. AWS CloudFormation

AWS CloudFormation is an **Infrastructure as Code (IaC)** service.

It uses templates to create and manage AWS resources automatically.

Templates can define:

- EC2 instances
- S3 buckets
- VPCs
- Security groups
- Other AWS services

Basic process:

1. Prepare a CloudFormation template.
2. Open CloudFormation in AWS Console.
3. Create a stack.
4. Upload or select the template.
5. Review and create the stack.

### 15. Boto3

Boto3 is the AWS SDK for Python.

It allows Python programs to interact with AWS services and automate tasks.

Use cases include:

- Listing EC2 instances
- Creating or deleting resources
- Reading S3 buckets
- Automating infrastructure operations

Boto3 can use credentials configured through `aws configure`.

### 16. Automation Methods

AWS resources can be automated using:

- AWS CLI
- AWS API
- AWS CloudFormation
- AWS CDK
- Terraform
- Python Boto3
- Shell scripts

### 17. Assignment

1. Install AWS CLI.
2. Configure AWS credentials.
3. List S3 buckets using the CLI.
4. Explore EC2 commands in AWS documentation.
5. Connect to an EC2 instance using SSH.
6. Learn the basics of CloudFormation and Boto3.

### 18. Interview Points

- SSH is used to securely connect to remote servers.
- The public IP is used for external access to an EC2 instance.
- A PEM file contains the private key used for authentication.
- AWS CLI manages AWS services from the terminal.
- `aws configure` sets up AWS CLI credentials and default settings.
- CloudFormation is AWS Infrastructure as Code.
- Boto3 is the Python SDK for AWS automation.
- Stopping an instance is temporary, while terminating it deletes the instance.

