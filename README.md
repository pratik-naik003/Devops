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


# Linux Operating System and Bash Shell Scripting

## 1. Overview

This lesson introduces Linux operating-system fundamentals and basic shell scripting concepts used in DevOps.

Topics covered:
- Hardware and software
- Operating systems
- Linux advantages and distributions
- Linux architecture
- Kernel and its responsibilities
- Shell and Bash
- Linux file and directory commands
- CPU, memory, and disk monitoring

---

## 2. Hardware and Software

### Hardware

Hardware means the physical components of a computer or server.

Important components include:

- **CPU:** Executes instructions and performs calculations.
- **RAM:** Temporarily stores data and programs currently in use.
- **Disk/Storage:** Stores the operating system, applications, and files.
- **I/O devices:** Input and output devices such as keyboards, disks, and network devices.

Examples include laptops, physical servers, cloud infrastructure, and Raspberry Pi devices.

### Software

Software is a collection of programs that run on hardware.

Examples:
- Jenkins
- Java
- Python
- Databases
- Web servers
- Office applications
- DevOps tools

Applications need CPU, RAM, storage, and other hardware resources. They use the operating system to access those resources.

---

## 3. What Is an Operating System?

An **Operating System (OS)** is system software that acts as a bridge between applications and hardware.

It manages hardware resources and provides an environment in which applications can execute.

Examples:
- Linux
- Windows
- macOS
- Unix-based operating systems

### Communication Flow

```text
User
  ↓
Application
  ↓
Operating System
  ↓
Hardware
  ↓
Operating System
  ↓
Application
  ↓
User
```

### Example

When a Jenkins pipeline runs:

1. The user starts a pipeline.
2. Jenkins requests resources from the operating system.
3. The operating system communicates with the CPU, RAM, disk, or network.
4. Hardware performs the operation.
5. The result returns to the operating system.
6. The operating system provides the result to Jenkins.
7. Jenkins displays the result to the user.

### Main Responsibilities of an OS

- CPU management
- Memory management
- Process management
- File and storage management
- Device management
- Security and permissions
- Networking
- Providing interfaces for applications

Without an operating system, applications cannot conveniently and safely use hardware resources.

---

## 4. Why Linux Is Popular

Linux is widely used in development, testing, staging, production, cloud, and DevOps environments.

### 4.1 Free and Open Source

Linux is open-source software. Its source code is available for inspection, modification, and distribution according to its license.

Benefits:
- No traditional proprietary license cost for many distributions
- Can be customized
- Supported by a large community
- Flexible for organizations

Windows, in comparison, is a proprietary operating system developed by Microsoft.

### 4.2 Security

Linux provides strong security features such as:

- User and group management
- File permissions
- Process isolation
- Access control
- Security updates
- Reduced unnecessary components on servers

Linux is not automatically 100% secure. Security depends on correct configuration, updates, firewall rules, permissions, and monitoring.

### 4.3 Performance

Linux can be lightweight and efficient, especially when used without a graphical user interface.

This makes it suitable for:
- Cloud servers
- Web servers
- Databases
- CI/CD systems
- Containers
- Production workloads

### 4.4 Stability

Linux is commonly used for long-running services because it can provide reliable and stable performance when properly maintained.

### 4.5 Linux Distributions

A Linux distribution combines the Linux kernel with system libraries, utilities, package managers, and applications.

Popular distributions include:

- Ubuntu
- Debian
- Fedora
- CentOS
- Red Hat Enterprise Linux (RHEL)
- Alpine Linux

Distributions may differ in package managers, default configurations, and system tools, but many basic shell commands are similar.

---

## 5. Linux Architecture

A simplified Linux architecture is:

```text
User Applications
Compilers
System Software
User Processes
        ↓
System Libraries
        ↓
Linux Kernel
        ↓
Hardware
CPU | RAM | Disk | I/O
```

### Main Layers

1. **Hardware:** Physical resources such as CPU, RAM, disk, and devices.
2. **Kernel:** Core component that manages hardware and system resources.
3. **System Libraries:** Reusable functions used by applications to communicate with the kernel.
4. **System Software:** Utilities and services that help operate the system.
5. **Compilers and Runtimes:** Support execution of programs written in languages such as C, Java, or Python.
6. **User Processes:** Running applications and services.

---

## 6. Linux Kernel

The **kernel** is the core or heart of the operating system.

It provides a controlled communication layer between applications and hardware.

```text
Application
    ↓
System Library / System Call
    ↓
Kernel
    ↓
Hardware
```

### Primary Responsibilities

#### 6.1 Device Management

The kernel manages hardware devices such as:

- Disks
- Network cards
- USB devices
- Keyboards
- Display devices
- Input/output devices

It uses appropriate drivers to communicate with hardware.

#### 6.2 Memory Management

The kernel manages RAM and memory allocation.

It:
- Allocates memory to processes
- Releases memory
- Tracks memory usage
- Supports virtual memory
- Prevents improper memory access between processes

#### 6.3 Process Management

A process is a running instance of a program.

The kernel manages:
- Process creation
- Process scheduling
- CPU allocation
- Process execution
- Process termination
- Process communication

#### 6.4 System Calls

A system call is a controlled request from an application to the operating system.

Applications use system calls for operations such as:
- Reading files
- Writing files
- Creating processes
- Allocating memory
- Accessing devices
- Network communication

### Interview Definition

> The kernel is the core component of an operating system. It manages hardware resources and provides services to applications. Its major responsibilities are device management, memory management, process management, and handling system calls.

---

## 7. System Libraries

System libraries provide reusable functions that applications can call.

They act as an intermediate layer between applications and the kernel.

```text
Application
    ↓
System Library
    ↓
Kernel
    ↓
Hardware
```

For example, an application can use a library function to read a file instead of directly controlling the disk.

One important Linux system library is **glibc**, also called the GNU C Library.

---

## 8. Shell and Command-Line Interface

A **shell** is a command-line interface used to communicate with the operating system.

Instead of using menus and a mouse, the user types commands.

```text
User
  ↓
Shell Command
  ↓
Shell
  ↓
Operating System / Kernel
  ↓
System Resource
```

### Why Shell Is Important in DevOps

Production servers often do not have a graphical user interface because a GUI consumes additional resources and is not necessary for server administration.

DevOps engineers use shell commands to:

- Navigate directories
- Create and edit files
- Read logs
- Install software
- Start and stop services
- Manage processes
- Check system resources
- Troubleshoot servers
- Execute deployments
- Automate repetitive tasks

### GUI vs Shell

| GUI | Shell |
|---|---|
| Uses windows, menus, and mouse | Uses typed commands |
| Easy for beginners | Efficient for repeated operations |
| Uses more resources | Lightweight |
| Less convenient for automation | Excellent for automation |
| Common on personal computers | Common on Linux servers |

---

## 9. Bash Shell

**Bash** stands for **Bourne Again Shell**.

It is one of the most widely used shells in Linux environments.

Bash can:
- Execute commands
- Navigate the file system
- Manage files
- Use variables
- Apply conditions
- Run loops
- Execute scripts
- Automate tasks

Other shells include:
- sh
- zsh
- ksh
- fish

For DevOps beginners, Bash is a useful shell to learn because it is widely used in Linux servers and automation.

---

## 10. Connecting to a Linux Server Using SSH

SSH means **Secure Shell**. It is used to securely access a remote server.

Example:

```bash
ssh -i <private-key.pem> ubuntu@<public-ip>
```

Explanation:
- `ssh`: Secure Shell command
- `-i`: Specifies the identity/private-key file
- `<private-key.pem>`: Private key used for authentication
- `ubuntu`: Username for an Ubuntu instance
- `<public-ip>`: Public IP address of the server

After login, commands execute on the remote server.

---

## 11. Basic Linux Commands

### 11.1 `pwd` — Present Working Directory

Displays the current directory.

```bash
pwd
```

Example output:

```text
/home/ubuntu
```

Use it to understand your current location.

### 11.2 `ls` — List Files and Directories

Lists files and directories in the current location.

```bash
ls
```

### 11.3 `ls -l` — Long Listing

Displays detailed information:

```bash
ls -l
```

Information includes:
- File type
- Permissions
- Owner
- Group
- File size
- Modification timestamp
- File or directory name

The first character generally indicates:
- `d`: Directory
- `-`: Regular file

### 11.4 `ls -ltr`

```bash
ls -ltr
```

Meaning:
- `-l`: Detailed listing
- `-t`: Sort by modification time
- `-r`: Reverse the order

This is useful for viewing files with their properties and time information.

### 11.5 `cd` — Change Directory

Changes the current directory.

```bash
cd bundle
```

Absolute path example:

```bash
cd /home/ubuntu/bundle
```

Relative path example:

```bash
cd test
```

### 11.6 `cd ..` — Parent Directory

Moves one level up.

```bash
cd ..
```

Move up two levels:

```bash
cd ../..
```

### 11.7 `touch` — Create a File

Creates an empty file.

```bash
touch example.txt
```

Verify it using:

```bash
ls
```

### 11.8 `vi` — Create or Edit a File

Opens or creates a file using the vi editor.

```bash
vi test.txt
```

Basic vi workflow:

1. Open the file using `vi`.
2. Press `i` to enter insert mode.
3. Type the content.
4. Press `Esc` to return to normal mode.
5. Type `:wq`.
6. Press Enter to save and exit.

Useful vi commands:

| Command | Meaning |
|---|---|
| `i` | Insert mode |
| `Esc` | Normal mode |
| `:w` | Save |
| `:q` | Quit |
| `:q!` | Quit without saving |
| `:wq` | Save and quit |

### 11.9 `cat` — Read File Contents

Displays the contents of a file.

```bash
cat test.txt
```

It is useful for reading small files and checking written content.

### 11.10 `mkdir` — Create a Directory

Creates a directory.

```bash
mkdir project
```

Create parent directories when needed:

```bash
mkdir -p project/src/app
```

### 11.11 `rm` — Remove Files

Remove a file:

```bash
rm example.txt
```

Remove a directory and its contents:

```bash
rm -r project
```

Be careful because `rm` can permanently delete data. Verify the path before using recursive or force options.

---

## 12. Checking System Resources

DevOps engineers regularly check server health and performance.

Important resources:
- CPU
- RAM / Memory
- Disk space
- Running processes

### 12.1 `free` — Memory Usage

Displays memory information.

```bash
free
```

For readable values in megabytes:

```bash
free -m
```

It commonly displays:
- Total memory
- Used memory
- Free memory
- Buffers/cache
- Available memory
- Swap

### 12.2 `nproc` — CPU Count

Displays the number of processing units available.

```bash
nproc
```

Example output:

```text
1
```

This is useful for quickly checking the CPU count of a server.

### 12.3 `df -h` — Disk Usage

Displays file-system disk usage in human-readable form.

```bash
df -h
```

Information includes:
- File system
- Total size
- Used space
- Available space
- Usage percentage
- Mount point

Example:

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       7.6G  1.9G  5.8G  25% /
```

A full disk can cause applications and services to fail, so disk monitoring is important.

### 12.4 `top` — Live System Monitoring

Displays a live view of system performance.

```bash
top
```

It can show:
- CPU usage
- Memory usage
- Running processes
- Process IDs
- System load
- Resource-consuming processes

It is useful for finding processes that consume excessive CPU or memory and for troubleshooting slow servers.

---

## 13. Practical Linux Workflow

After logging into a server, use this workflow:

```bash
# 1. Check current location
pwd

# 2. List files and directories
ls

# 3. View detailed listing
ls -ltr

# 4. Change directory
cd <directory-name>

# 5. Create a file
touch notes.txt

# 6. Edit the file
vi notes.txt

# 7. Read the file
cat notes.txt

# 8. Create a directory
mkdir practice

# 9. Check memory
free -m

# 10. Check CPU count
nproc

# 11. Check disk usage
df -h

# 12. Monitor processes
top
```

---

## 14. Shell Scripting in DevOps

Shell scripting means placing multiple shell commands inside a script file so they can be executed automatically.

### Manual Example

```bash
mkdir backup
cp app.log backup/
echo "Backup completed"
```

These commands can be placed into a script and executed as one repeatable task.

### Benefits

- Saves time
- Reduces manual errors
- Makes tasks repeatable
- Improves consistency
- Supports deployments
- Helps with server maintenance
- Works well in CI/CD pipelines
- Automates repetitive operations

Common DevOps uses:
- Application deployment
- Log cleanup
- Backup tasks
- Service management
- Environment setup
- Monitoring checks
- Build and release automation

---

## 15. Linux in DevOps

Linux is commonly used to host and operate tools such as:

- Jenkins
- Docker
- Kubernetes
- Git
- Ansible
- Terraform
- Prometheus
- Grafana
- Nginx
- Apache

Linux knowledge helps DevOps engineers perform:
- Server administration
- Application deployment
- Log analysis
- Configuration
- Monitoring
- Troubleshooting
- CI/CD automation
- Infrastructure management

---

## 16. Interview Questions

### What is an operating system?

An operating system is system software that acts as a bridge between hardware and software. It manages resources and provides services to applications.

### Why is Linux widely used in DevOps?

Linux is open source, efficient, customizable, stable, and well suited for servers, cloud platforms, automation, and production workloads.

### What is the kernel?

The kernel is the core component of an operating system. It manages hardware resources and provides services to applications.

### What are the main responsibilities of the kernel?

1. Device management
2. Memory management
3. Process management
4. Handling system calls

### What is a shell?

A shell is a command-line interface used to communicate with the operating system by executing commands.

### What is Bash?

Bash means Bourne Again Shell. It is a popular shell used to execute Linux commands and write shell scripts.

### Difference between `pwd`, `ls`, and `cd`

- `pwd`: Shows the current directory.
- `ls`: Lists files and directories.
- `cd`: Changes the current directory.

### How do you create a file?

```bash
touch filename.txt
```

### How do you check memory?

```bash
free -m
```

### How do you check CPU count?

```bash
nproc
```

### How do you check disk usage?

```bash
df -h
```

### Which command gives an overall live view of CPU, memory, and processes?

```bash
top
```

---

## 17. Quick Command Reference

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files and directories |
| `ls -l` | Show detailed listing |
| `ls -ltr` | Show detailed time-sorted listing |
| `cd` | Change directory |
| `cd ..` | Move to parent directory |
| `touch` | Create an empty file |
| `vi` | Create or edit a file |
| `cat` | Display file contents |
| `mkdir` | Create a directory |
| `rm` | Remove a file |
| `rm -r` | Remove a directory recursively |
| `free -m` | Show memory usage |
| `nproc` | Show CPU count |
| `df -h` | Show disk usage |
| `top` | Monitor processes and system resources |

---

## 18. Final Summary

This lesson covered the fundamentals of Linux and shell usage:

- Hardware contains CPU, RAM, storage, and I/O resources.
- Software uses hardware through the operating system.
- The operating system acts as a bridge between applications and hardware.
- Linux is popular because it is open source, efficient, secure when properly maintained, and stable.
- Linux distributions include Ubuntu, Debian, Fedora, CentOS, RHEL, and Alpine.
- The kernel is the heart of Linux.
- The kernel manages devices, memory, processes, and system calls.
- System libraries provide reusable functions for applications.
- A shell provides command-line access to the operating system.
- Bash is a popular shell used in Linux and DevOps.
- Commands such as `pwd`, `ls`, `cd`, `touch`, `vi`, `cat`, `mkdir`, and `rm` manage files and directories.
- Commands such as `free`, `nproc`, `df`, and `top` help monitor server resources.
- Shell scripting combines commands into reusable automation workflows.


# DevOps Day 7: AWS Resource Tracker Using Bash, AWS CLI, Cron, and jq

## 1. Overview

This lesson introduces a practical shell scripting project commonly used by DevOps engineers working with cloud infrastructure.

The project is an **AWS Resource Tracker**. Its purpose is to collect information about AWS resources and generate a readable report that can be shared with a manager, team, or reporting system.

The script uses:

- **Bash** for scripting
- **AWS CLI** for communicating with AWS
- **Linux commands** for execution and output handling
- **jq** for extracting useful information from JSON
- **Cron jobs** for scheduling the script automatically

The resources tracked in this project are:

1. Amazon S3 buckets
2. Amazon EC2 instances
3. AWS Lambda functions
4. IAM users

> This is a basic version of a resource-tracking project. In real organizations, similar information is often sent to dashboards, monitoring systems, cost-management tools, or reporting platforms.

---

## 2. Why Organizations Move to Cloud Infrastructure

Organizations commonly move from physical infrastructure to cloud providers such as AWS or Azure for several reasons.

### 2.1 Manageability

In a traditional data center, an organization must manage its own infrastructure.

This can include:

- Purchasing physical servers
- Setting up a data center
- Installing operating systems
- Managing networking equipment
- Applying security patches
- Replacing failed hardware
- Monitoring server health
- Upgrading hardware
- Managing cooling and electricity
- Maintaining dedicated infrastructure teams

This creates significant **maintenance overhead**.

Cloud providers manage much of the underlying infrastructure, allowing organizations to focus more on applications and business requirements.

For example, instead of purchasing a physical server, a company can create an EC2 instance through AWS.

### 2.2 Cost Effectiveness

Cloud providers generally follow a **pay-as-you-go** model.

This means the organization pays based on the resources it uses and the billing model of the selected service.

In physical infrastructure:

- Hardware must be purchased in advance.
- The company pays for the infrastructure even when it is underutilized.
- Hardware may remain idle for long periods.

In cloud infrastructure:

- Resources can be created when needed.
- Resources can be stopped or deleted when no longer required.
- Capacity can be adjusted based on demand.
- Organizations can avoid some large upfront infrastructure costs.

However, cloud does not automatically mean low cost. Unused cloud resources can continue generating charges.

---

## 3. Why Cloud Resource Tracking Is Important

Suppose a company named `example.com` has 100 developers, and all developers have access to AWS.

Each developer may create resources such as:

- EC2 instances
- EBS volumes
- S3 buckets
- Lambda functions
- Databases
- Load balancers
- Elastic IP addresses
- Snapshots

Over time, some resources may become unused.

### Example: Unused EC2 Instances

A developer may create 100 EC2 instances for testing, but nobody may be using them anymore.

If these instances remain active, they may continue generating costs.

### Example: Unused EBS Volumes

A developer may create an EBS volume and later terminate the EC2 instance associated with it.

The EBS volume may remain available even though no EC2 instance is using it.

AWS does not automatically assume that an unused volume should be deleted. The volume may continue to incur charges.

### DevOps Responsibility

One responsibility of a DevOps engineer or AWS administrator is to help maintain cloud cost effectiveness.

This includes:

- Tracking resource usage
- Identifying unused resources
- Monitoring active infrastructure
- Reviewing resource ownership
- Reporting resource counts
- Supporting cost optimization
- Removing resources only after proper approval

> Resource tracking is not the same as automatically deleting resources. Deletion should be handled carefully because a resource that appears unused may still be required.

---

## 4. Project Objective

The objective is to create a Bash script that collects information about AWS resources and writes the information into a report.

The report may include:

- List of S3 buckets
- List of EC2 instances
- List of Lambda functions
- List of IAM users

The report can be:

- Printed in the terminal
- Redirected to a file
- Shared with a manager
- Used by another reporting system
- Integrated with a dashboard
- Generated automatically at a fixed time every day

For this learning project, the report is treated as information that can be given to a manager.

In a real-world implementation, the output would commonly be sent to a dashboard, monitoring system, email workflow, or centralized reporting platform.

---

## 5. High-Level Project Workflow

```text
Bash Script
    |
    v
AWS CLI Commands
    |
    v
AWS Account
    |
    v
Resource Information
    |
    v
jq / Output Formatting
    |
    v
Report File
    |
    v
Manager / Dashboard / Reporting System
```

The script communicates with AWS using AWS CLI commands. AWS returns information, often in JSON format. The script then displays or filters the information and stores it in a report.

---

## 6. Why Bash Is Used

Bash is a popular shell and scripting language on Linux systems.

It is useful for DevOps because it can:

- Execute Linux commands
- Run AWS CLI commands
- Store command output in variables
- Redirect output to files
- Connect commands using pipes
- Use conditions and loops
- Automate repetitive tasks
- Work well with cron
- Integrate with other command-line tools

Although the same project could be implemented using Python, Boto3, AWS Lambda, or another automation method, Bash is useful because DevOps engineers frequently work with Linux servers and command-line tools.

### Other Possible Implementation Options

The same resource-tracking requirement could be implemented using:

- Bash shell scripting
- Python with Boto3
- AWS Lambda with Python
- AWS SDKs
- AWS CDK
- Terraform data sources
- CloudFormation-related automation
- Monitoring or cost-management platforms

The important point is to achieve the required operational goal. The programming language is selected based on the team's skills, maintainability requirements, and infrastructure design.

---

## 7. Project Prerequisites

### 7.1 Linux or Linux-Compatible Environment

The script is designed to run on Linux.

Possible environments include:

- An AWS EC2 Linux instance
- Ubuntu
- Amazon Linux
- A local Linux machine
- macOS terminal
- Windows with WSL or another Linux-compatible environment

### 7.2 Bash

Check the Bash version:

```bash
bash --version
```

### 7.3 AWS CLI

Check whether AWS CLI is installed:

```bash
aws --version
```

### 7.4 AWS Credentials

Configure AWS CLI using:

```bash
aws configure
```

The command generally asks for:

1. AWS Access Key ID
2. AWS Secret Access Key
3. Default AWS Region
4. Default output format

Example:

```text
AWS Access Key ID: <your-access-key>
AWS Secret Access Key: <your-secret-key>
Default region name: ap-south-1
Default output format: json
```

Use the region appropriate for your AWS resources.

### Important Security Note

Do not:

- Hardcode access keys inside scripts
- Upload access keys to GitHub
- Share secret keys publicly
- Put credentials in screenshots
- Commit AWS credential files into repositories

For EC2 instances, an IAM role attached to the instance is generally preferable to storing long-term access keys on the server.

### 7.5 jq

Check whether jq is installed:

```bash
jq --version
```

For Ubuntu/Debian-based systems:

```bash
sudo apt update
sudo apt install jq
```

---

## 8. AWS CLI Authentication

AWS CLI needs to authenticate with AWS before it can retrieve resource information.

Authentication answers:

> Who is making the request?

Authorization answers:

> What is this identity allowed to do?

The configured identity must have permission to call the required AWS APIs.

For this project, permissions may be needed for actions such as:

- Listing S3 buckets
- Describing EC2 instances
- Listing Lambda functions
- Listing IAM users

A command may fail if:

- Credentials are missing
- Credentials are incorrect
- The region is incorrect
- The IAM identity lacks permission
- The AWS CLI is not installed
- The account or resource does not contain the requested resources

---

## 9. Creating the Script File

The script is named:

```text
aws_resource_tracker.sh
```

Create the file:

```bash
touch aws_resource_tracker.sh
```

Open it in Vim:

```bash
vim aws_resource_tracker.sh
```

Alternatively:

```bash
nano aws_resource_tracker.sh
```

---

## 10. Shebang

The first line of the script should identify the interpreter:

```bash
#!/bin/bash
```

This line is called the **shebang**.

- `#!` tells the operating system that the file should be executed using an interpreter.
- `/bin/bash` specifies Bash as the interpreter.

### Why Not Always Use `/bin/sh`?

A common alternative is:

```bash
#!/bin/sh
```

However, `/bin/sh` may be a symbolic link to different shells depending on the Linux distribution. It may point to Bash, Dash, or another POSIX-compatible shell.

Bash and Dash have syntax and feature differences. A script written using Bash-specific features may fail if executed with Dash.

Therefore, if the script is written specifically for Bash, use:

```bash
#!/bin/bash
```

---

## 11. Script Documentation and Comments

A script should explain its purpose and ownership.

Example:

```bash
#!/bin/bash

# Author: Abhishek
# Date: 11-Jan
# Version: v1
# Description: This script reports AWS resource usage.
```

### Why Add a Header?

A script header helps future users understand:

- Who created the script
- When it was created
- What the script does
- Which version they are using
- Who they can contact for clarification

This is useful when a script is maintained by multiple engineers, stored in Git, shared across teams, or being troubleshot.

In professional projects, version tracking is usually handled through Git, but a short version or change description can still be useful.

---

## 12. Resources Tracked by the Script

The project tracks four AWS resource categories.

### 12.1 Amazon S3

Amazon S3 is an object storage service. An S3 bucket is a container used to store objects such as files, images, logs, backups, application artifacts, and data files.

### 12.2 Amazon EC2

Amazon EC2 provides virtual servers in the cloud. EC2 instances may run web applications, APIs, databases, build servers, monitoring tools, DevOps tools, and development environments.

### 12.3 AWS Lambda

AWS Lambda is a serverless compute service. Lambda functions execute code in response to events or requests without requiring users to manage traditional servers.

### 12.4 IAM Users

AWS Identity and Access Management (IAM) controls access to AWS resources. An IAM user represents an identity in an AWS account.

The script lists IAM users. IAM users are account-level identities, while some other AWS resources are region-specific.

---

## 13. AWS CLI Command Reference

The official AWS CLI documentation should be used whenever the exact command is unknown.

Documentation helps identify:

- Service names
- Available operations
- Required parameters
- Optional parameters
- Output formats
- Examples
- Permissions
- Pagination behavior

Instead of memorizing every command, learn how to search the documentation and understand the command structure.

---

## 14. AWS CLI Command: List S3 Buckets

Command:

```bash
aws s3 ls
```

### Explanation

- `aws` is the AWS CLI executable.
- `s3` identifies the Amazon S3 service.
- `ls` means list.

This command lists S3 buckets accessible to the configured AWS identity.

Example output:

```text
2026-09-14 10:00:00 example-bucket
2026-09-14 10:05:00 project-logs
```

Script usage:

```bash
echo "List of S3 buckets"
aws s3 ls
```

---

## 15. AWS CLI Command: Describe EC2 Instances

Command:

```bash
aws ec2 describe-instances
```

This command retrieves detailed information about EC2 instances.

The response may include:

- Instance ID
- Instance type
- Image ID
- State
- Private IP address
- Public IP address
- Availability Zone
- Security groups
- Subnet ID
- VPC ID
- Tags
- Block device mappings

The response is usually large and nested JSON. A manager may not need every field, so jq can be used to extract only instance IDs.

---

## 16. AWS CLI Command: List Lambda Functions

Command:

```bash
aws lambda list-functions
```

This retrieves Lambda functions available in the selected AWS region.

The response may contain:

- Function name
- Function ARN
- Runtime
- Handler
- Memory size
- Timeout
- Last modified time
- Role
- Code size

Example:

```bash
echo "List of Lambda functions"
aws lambda list-functions
```

---

## 17. AWS CLI Command: List IAM Users

Command:

```bash
aws iam list-users
```

This retrieves IAM users in the AWS account.

The response may include:

- User name
- User ID
- ARN
- Creation date
- Password last-used information, where available

Example:

```bash
echo "List of IAM users"
aws iam list-users
```

---

## 18. Initial Script Structure

A basic version of the script may look like this:

```bash
#!/bin/bash

# Author: Abhishek
# Date: 11-Jan
# Version: v1
# Description: This script reports AWS resource usage.

# List S3 buckets
aws s3 ls

# List EC2 instances
aws ec2 describe-instances

# List Lambda functions
aws lambda list-functions

# List IAM users
aws iam list-users
```

This version works as a starting point, but its output is not very readable because:

- There are no section headings.
- EC2 output is very large.
- The user cannot easily identify which output belongs to which service.
- The output is not yet formatted as a report.

---

## 19. Making the Script Executable

Add execute permission:

```bash
chmod +x aws_resource_tracker.sh
```

Execute the script:

```bash
./aws_resource_tracker.sh
```

### Meaning

- `chmod` changes file permissions.
- `+x` adds execute permission.
- `./` means execute the file from the current directory.

### About chmod 777

The lecture temporarily uses:

```bash
chmod 777 aws_resource_tracker.sh
```

However, `777` is generally not recommended. It grants read, write, and execute permissions to the owner, group, and others.

Safer options may include:

```bash
chmod 700 aws_resource_tracker.sh
```

or:

```bash
chmod 750 aws_resource_tracker.sh
```

The correct permission depends on the operational requirement.

---

## 20. Why Print Statements Are Important

When multiple commands run one after another, their output can become confusing.

Use `echo` to print descriptive headings.

Example:

```bash
echo "========== S3 Buckets =========="
aws s3 ls

echo "========== EC2 Instances =========="
aws ec2 describe-instances

echo "========== Lambda Functions =========="
aws lambda list-functions

echo "========== IAM Users =========="
aws iam list-users
```

Print statements improve:

- Readability
- Debugging
- User experience
- Report organization
- Troubleshooting
- Log interpretation

Comments explain the code to someone reading the script, while `echo` statements provide information while the script is running.

---

## 21. Bash Debug Mode

### 21.1 set -x

```bash
set -x
```

This enables execution tracing. Bash prints commands before executing them.

Example:

```bash
#!/bin/bash

set -x

echo "Listing S3 buckets"
aws s3 ls
```

This helps identify:

- Which command is running
- The order of execution
- Whether variables are expanded correctly
- Where a script begins to fail

### 21.2 set +x

```bash
set +x
```

This disables execution tracing.

Example:

```bash
set -x
echo "Debugging enabled"
aws s3 ls
set +x
echo "Debugging disabled"
```

### Security Warning

Debug mode can expose sensitive information in logs or terminal output. Avoid enabling tracing around commands that print passwords, tokens, secret keys, or sensitive environment variables.

---

## 22. set -e and Error Handling

The lecture also mentions:

```bash
set -e
```

This generally causes the script to exit when a command returns a non-zero status, subject to Bash's error-handling rules and context.

It can help prevent a script from continuing after an important command fails.

Example:

```bash
#!/bin/bash

set -e

echo "Starting script"
aws s3 ls
echo "The previous command completed"
```

In production scripts, error handling should be designed carefully because Bash has special cases around `set -e`.

A commonly seen combination is:

```bash
set -euo pipefail
```

These options should be used only after understanding their behavior.

---

## 23. Understanding jq

### 23.1 What Is jq?

`jq` is a command-line JSON processor.

It is used to:

- Read JSON
- Filter JSON
- Extract fields
- Transform JSON
- Format JSON
- Select values from nested structures
- Convert complex API responses into readable output

AWS CLI frequently returns JSON, so jq is highly useful for DevOps engineers.

### 23.2 Why jq Is Needed

The command:

```bash
aws ec2 describe-instances
```

may return a large JSON response. The report may only require instance IDs.

Instead of displaying the complete response, jq can extract the required field.

### 23.3 Pipe Operator

The pipe symbol is:

```bash
|
```

It sends the output of one command as input to another command.

General structure:

```bash
command1 | command2
```

Example:

```bash
aws ec2 describe-instances | jq
```

Here:

1. AWS CLI produces JSON.
2. The pipe sends the JSON to jq.
3. jq processes the JSON.

---

## 24. Extracting EC2 Instance IDs with jq

An EC2 response generally contains a nested structure similar to:

```json
{
  "Reservations": [
    {
      "Instances": [
        {
          "InstanceId": "i-0123456789abcdef0"
        }
      ]
    }
  ]
}
```

To extract instance IDs:

```bash
aws ec2 describe-instances | jq -r '.Reservations[].Instances[].InstanceId'
```

### Explanation of the jq Expression

```text
.Reservations[].Instances[].InstanceId
```

- `.Reservations` accesses the `Reservations` field.
- The first `[]` iterates through the reservations array.
- `.Instances` accesses the instances field inside each reservation.
- The second `[]` iterates through the instances array.
- `.InstanceId` extracts the instance ID.

### Example Output

```text
i-0123456789abcdef0
i-0abcdef1234567890
```

The `-r` option means **raw output**, so the IDs are printed without JSON quotation marks.

---

## 25. Arrays and jq Brackets

If a field contains a single object, it can be accessed directly.

Example:

```json
{
  "user": {
    "name": "Alex"
  }
}
```

Command:

```bash
jq '.user.name'
```

For an array:

```json
{
  "users": [
    {"name": "Alex"},
    {"name": "Sam"}
  ]
}
```

Command:

```bash
jq '.users[].name'
```

The `[]` tells jq to process each element in the array.

---

## 26. jq and yq

| Tool | Purpose |
|---|---|
| `jq` | Parse and process JSON |
| `yq` | Parse and process YAML |

DevOps engineers frequently work with JSON and YAML in:

- Cloud API responses
- Kubernetes manifests
- CI/CD pipelines
- Infrastructure-as-code files
- Application configuration
- Cloud service configuration

Therefore, familiarity with both tools is useful.

---

## 27. Improved Script with Readable Output

```bash
#!/bin/bash

# Author: Abhishek
# Date: 11-Jan
# Version: v1
# Description: This script reports AWS resource usage.

echo "========== List of S3 Buckets =========="
aws s3 ls

echo "========== List of EC2 Instance IDs =========="
aws ec2 describe-instances | jq -r '.Reservations[].Instances[].InstanceId'

echo "========== List of Lambda Functions =========="
aws lambda list-functions

echo "========== List of IAM Users =========="
aws iam list-users
```

This version is easier to read because:

- Each resource category has a heading.
- EC2 output is filtered.
- The report is organized into sections.
- The manager can understand the output more easily.

---

## 28. Region Considerations

Many AWS services are region-specific.

For example:

- EC2 instances are associated with a region.
- Lambda functions are generally regional.
- S3 operations have global and region-related behavior.
- IAM users are account-level identities.

If the AWS CLI default region is incorrect, commands may show no resources even though resources exist in another region.

Specify a region explicitly:

```bash
aws ec2 describe-instances --region ap-south-1
```

Or configure the default region:

```bash
aws configure
```

A production resource tracker may need to:

- Track only one region
- Loop through multiple regions
- Produce a separate report for each region
- Aggregate regional results into one report

The lecture focuses on a simple version rather than multi-region reporting.

---

## 29. Redirecting Output to a File

### 29.1 Overwrite a File with >

```bash
./aws_resource_tracker.sh > resource_tracker.txt
```

The `>` operator redirects standard output into a file. If the file exists, its previous content is overwritten.

### 29.2 Append to a File with >>

```bash
./aws_resource_tracker.sh >> resource_tracker.txt
```

The `>>` operator appends output to the end of the file.

### 29.3 View the Report

```bash
cat resource_tracker.txt
```

or:

```bash
less resource_tracker.txt
```

| Operator | Behavior |
|---|---|
| `>` | Creates or overwrites a file |
| `>>` | Creates or appends to a file |

---

## 30. Standard Output and Standard Error

A script may produce:

- Standard output: normal command results
- Standard error: error messages

Redirect standard output:

```bash
./aws_resource_tracker.sh > resource_tracker.txt
```

Redirect standard error:

```bash
./aws_resource_tracker.sh 2> errors.txt
```

Redirect both output and errors:

```bash
./aws_resource_tracker.sh > resource_tracker.txt 2>&1
```

This is useful for scheduled jobs because errors should be captured and reviewed.

---

## 31. Cron Jobs

### 31.1 What Is Cron?

Cron is a Linux-based job scheduling mechanism.

A cron job allows a command or script to run automatically at a specified time or interval.

A script can be scheduled to run:

- Every minute
- Every hour
- Every day
- Every week
- On a specific day
- At a specific time

### 31.2 Why Cron Is Useful

Suppose a manager needs an AWS resource report every day at 6 PM.

Manually running the script is unreliable because:

- The engineer may be unavailable.
- The engineer may forget.
- The engineer may not be able to log in.
- The report may be delayed.
- Manual execution is repetitive.

Cron automates this process.

The Linux system runs the script at the scheduled time without requiring the engineer to execute it manually.

---

## 32. Cron Analogy

A creator may upload a video earlier and configure a platform to publish it at a specific time. The creator does not need to log in exactly at the publishing time.

Cron works similarly:

1. The script is prepared in advance.
2. A schedule is configured.
3. The Linux scheduler waits for the specified time.
4. The script is executed automatically.

---

## 33. Cron Syntax

Cron entries generally contain five time fields followed by the command.

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week
│ │ │ └──── Month
│ │ └────── Day of month
│ └──────── Hour
└────────── Minute
```

The five fields are:

1. Minute: `0–59`
2. Hour: `0–23`
3. Day of month: `1–31`
4. Month: `1–12`
5. Day of week: commonly `0–7`

### Example: Every Day at 6 PM

```cron
0 18 * * * /path/to/aws_resource_tracker.sh
```

### Example: Every Day at 7 AM

```cron
0 7 * * * /path/to/aws_resource_tracker.sh
```

### Example: Every Five Minutes

```cron
*/5 * * * * /path/to/aws_resource_tracker.sh
```

---

## 34. Editing the Crontab

Edit the current user's cron schedule:

```bash
crontab -e
```

Add an entry such as:

```cron
0 18 * * * /home/ubuntu/aws_resource_tracker.sh > /home/ubuntu/resource_tracker.txt 2>&1
```

This runs the script every day at 6 PM and writes the output to a report file.

### Use Absolute Paths

Cron jobs should generally use absolute paths because cron may run with a limited environment and a different working directory.

Prefer:

```cron
/home/ubuntu/aws_resource_tracker.sh
```

instead of:

```cron
./aws_resource_tracker.sh
```

---

## 35. Cron Permissions and Environment

When a script works manually but fails under cron, common causes include:

- Incorrect file path
- Missing execute permission
- Different `PATH` environment variable
- Missing AWS credentials
- Missing AWS region
- Missing jq path
- Incorrect working directory
- Permission problems
- Output file permission issues

To make cron execution reliable:

- Use absolute paths.
- Use a correct shebang.
- Ensure the script is executable.
- Confirm AWS authentication works for the cron user.
- Use explicit region settings when necessary.
- Redirect output and errors to a log file.
- Test the script manually before scheduling it.

---

## 36. Example Report-Generating Script

```bash
#!/bin/bash

# Author: DevOps Team
# Version: 1.0
# Description: Reports selected AWS resources.

REPORT_FILE="/tmp/aws_resource_tracker.txt"

echo "========================================" > "$REPORT_FILE"
echo "AWS Resource Tracker Report" >> "$REPORT_FILE"
echo "Generated at: $(date)" >> "$REPORT_FILE"
echo "========================================" >> "$REPORT_FILE"

echo "" >> "$REPORT_FILE"
echo "========== S3 Buckets ==========" >> "$REPORT_FILE"
aws s3 ls >> "$REPORT_FILE" 2>&1

echo "" >> "$REPORT_FILE"
echo "========== EC2 Instance IDs ==========" >> "$REPORT_FILE"
aws ec2 describe-instances   | jq -r '.Reservations[].Instances[].InstanceId' >> "$REPORT_FILE" 2>&1

echo "" >> "$REPORT_FILE"
echo "========== Lambda Functions ==========" >> "$REPORT_FILE"
aws lambda list-functions >> "$REPORT_FILE" 2>&1

echo "" >> "$REPORT_FILE"
echo "========== IAM Users ==========" >> "$REPORT_FILE"
aws iam list-users >> "$REPORT_FILE" 2>&1

echo "Report generated at $REPORT_FILE"
```

This is an educational example. A production implementation should improve error handling, credential management, region handling, pagination, logging, file rotation, security, and report formatting.

---

## 37. Possible Improvements

### 37.1 Track More Resources

Additional resources may include:

- EBS volumes
- Elastic IP addresses
- RDS databases
- Load balancers
- Auto Scaling groups
- ECR repositories
- CloudWatch alarms
- NAT gateways
- Snapshots
- VPCs
- Security groups

### 37.2 Detect Unused Resources

The script can be enhanced to identify:

- Stopped EC2 instances
- Unattached EBS volumes
- Unused Elastic IP addresses
- Old snapshots
- Empty or stale S3 buckets
- Lambda functions that have not been invoked recently

These checks must be designed carefully because “unused” depends on business context.

### 37.3 Add Resource Tags

Tags can identify:

- Owner
- Team
- Environment
- Application
- Cost center
- Project
- Department

Example:

```text
Environment=dev
Owner=platform-team
Application=payment-service
```

### 37.4 Generate Different Report Formats

The script can generate:

- CSV
- JSON
- HTML
- Markdown
- Email-friendly reports

### 37.5 Send Reports Automatically

The report can be integrated with:

- Email
- Slack
- Microsoft Teams
- Amazon SNS
- S3
- Dashboards
- Monitoring systems

### 37.6 Use AWS Lambda and EventBridge

Instead of using cron on an EC2 instance, the process can be implemented using AWS Lambda and Amazon EventBridge Scheduler.

This can reduce the need to maintain a server only for scheduling.

---

## 38. Bash Functions and Modularity

The initial lesson intentionally avoids shell functions to keep the script simple.

In larger projects, functions separate responsibilities.

Example:

```bash
list_s3_buckets() {
    aws s3 ls
}

list_ec2_instances() {
    aws ec2 describe-instances       | jq -r '.Reservations[].Instances[].InstanceId'
}

list_lambda_functions() {
    aws lambda list-functions
}

list_iam_users() {
    aws iam list-users
}
```

Functions improve:

- Reusability
- Readability
- Testing
- Maintenance
- Modularity

For beginners, a linear script may be easier to understand. As the project grows, functions become more valuable.

---

## 39. Common Errors and Troubleshooting

### Error: aws: command not found

Possible causes:

- AWS CLI is not installed.
- AWS CLI is not in the `PATH`.

Check:

```bash
aws --version
```

### Error: Unable to locate credentials

Possible causes:

- AWS CLI is not configured.
- Credentials are unavailable.
- The script runs under a different user.

Try:

```bash
aws configure
```

For EC2, verify that the instance has an appropriate IAM role.

### Error: AccessDenied

Possible cause:

- The IAM user or role lacks permission.

Review the required IAM permissions.

### Error: jq: command not found

Possible cause:

- jq is not installed.

Check:

```bash
jq --version
```

### Error: Permission denied

Possible cause:

- The script does not have execute permission.

Try:

```bash
chmod +x aws_resource_tracker.sh
```

### Script Works Manually but Not Through Cron

Check:

- Absolute script path
- Absolute output path
- AWS credentials
- Region
- PATH
- File permissions
- Cron logs
- User executing the cron job

---

## 40. Important Security Practices

When automating AWS resources:

1. Use IAM roles where possible.
2. Follow the principle of least privilege.
3. Do not use the root account for automation.
4. Never hardcode secrets in scripts.
5. Do not commit credentials to Git.
6. Avoid `chmod 777` unless there is a specific, justified requirement.
7. Protect report files if they contain sensitive infrastructure details.
8. Avoid exposing secrets when using `set -x`.
9. Rotate credentials according to organizational policy.
10. Review scripts before allowing destructive operations.

---

## 41. Assignment

The assignment is:

1. Create an AWS resource tracker shell script.
2. Track:
   - S3 buckets
   - EC2 instances
   - Lambda functions
   - IAM users
3. Add readable print statements.
4. Use jq to extract only EC2 instance IDs.
5. Redirect the output into a report file.
6. Integrate the script with a Linux cron job.
7. Schedule it to run automatically every day.

Example cron requirement:

```text
Run the resource tracker every day at 6 PM.
```

Example cron entry:

```cron
0 18 * * * /absolute/path/aws_resource_tracker.sh > /absolute/path/resource_tracker.txt 2>&1
```

---

## 42. Interview Questions and Answers

### Q1. Why do organizations move to cloud infrastructure?

Organizations move to cloud infrastructure mainly to reduce infrastructure-management overhead, improve scalability, and use flexible pay-as-you-go pricing.

### Q2. What is cloud resource tracking?

Cloud resource tracking is the process of monitoring resources created in a cloud account, such as EC2 instances, S3 buckets, Lambda functions, and EBS volumes.

### Q3. Why is resource tracking important?

It helps organizations understand resource usage, identify unused resources, improve visibility, and control cloud costs.

### Q4. What is AWS CLI?

AWS CLI is a command-line tool used to interact with AWS services and perform operations through terminal commands.

### Q5. What does `aws s3 ls` do?

It lists S3 buckets accessible to the configured AWS identity.

### Q6. What does `aws ec2 describe-instances` do?

It retrieves detailed information about EC2 instances.

### Q7. What does `aws lambda list-functions` do?

It lists Lambda functions available in the selected AWS region.

### Q8. What does `aws iam list-users` do?

It lists IAM users in the AWS account.

### Q9. What is jq?

jq is a command-line JSON processor used to extract and transform values from JSON output.

### Q10. Why is jq useful with AWS CLI?

Many AWS CLI commands return JSON. jq helps extract only the required fields from large, nested responses.

### Q11. Explain this command:

```bash
aws ec2 describe-instances | jq -r '.Reservations[].Instances[].InstanceId'
```

It retrieves EC2 instance information, pipes the JSON response to jq, navigates through the Reservations and Instances arrays, and extracts each instance ID as plain text.

### Q12. What is a cron job?

A cron job is a scheduled task in Linux that automatically executes a command or script at a configured time or interval.

### Q13. Why use cron for this project?

Cron ensures that the resource report is generated automatically at a fixed time without requiring manual execution.

### Q14. What is the difference between > and >>?

- `>` overwrites a file.
- `>>` appends output to a file.

### Q15. What does set -x do?

It enables Bash execution tracing and displays commands before they are executed.

### Q16. What does set +x do?

It disables Bash execution tracing.

### Q17. Why should /bin/bash be used instead of /bin/sh for a Bash script?

Because `/bin/sh` may point to a different shell such as Dash, and Bash-specific syntax may not work in that shell.

### Q18. Why should chmod 777 generally be avoided?

It gives all users read, write, and execute permissions, which can create security risks.

---

## 43. Quick Command Reference

| Purpose | Command |
|---|---|
| Check Bash version | `bash --version` |
| Check AWS CLI | `aws --version` |
| Configure AWS CLI | `aws configure` |
| Check jq | `jq --version` |
| Create script | `touch aws_resource_tracker.sh` |
| Open script in Vim | `vim aws_resource_tracker.sh` |
| Add execute permission | `chmod +x aws_resource_tracker.sh` |
| Run script | `./aws_resource_tracker.sh` |
| List S3 buckets | `aws s3 ls` |
| Describe EC2 instances | `aws ec2 describe-instances` |
| List Lambda functions | `aws lambda list-functions` |
| List IAM users | `aws iam list-users` |
| Extract EC2 IDs | `aws ec2 describe-instances \| jq -r '.Reservations[].Instances[].InstanceId'` |
| Enable debug mode | `set -x` |
| Disable debug mode | `set +x` |
| Edit cron jobs | `crontab -e` |
| Redirect output | `command > file.txt` |
| Append output | `command >> file.txt` |
| Redirect errors | `command 2> errors.txt` |
| Redirect output and errors | `command > output.txt 2>&1` |

---

## 44. Final Summary

This lesson created the foundation of a practical AWS resource-tracking automation project.

The major concepts covered were:

- Why organizations move to cloud infrastructure
- Manageability and maintenance overhead
- Pay-as-you-go cloud pricing
- The importance of tracking cloud resources
- Bash scripting for DevOps automation
- AWS CLI authentication and configuration
- AWS CLI commands for S3, EC2, Lambda, and IAM
- Script documentation using comments
- Bash shebang
- File permissions and script execution
- Readable output using echo
- Bash debugging with set -x
- JSON processing with jq
- Pipe operators
- Extracting EC2 instance IDs
- Redirecting output to report files
- Scheduling scripts with cron
- Troubleshooting and security practices

The core idea is:

> Use Bash and AWS CLI to collect AWS resource information, use tools such as jq to make the output readable, save the result as a report, and schedule the script with cron so the process runs automatically.

