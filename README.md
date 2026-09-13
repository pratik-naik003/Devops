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


