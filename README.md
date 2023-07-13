# Notes

## Resource Manager

- **super admin:** the user that you used to sign up for Google Cloud
  - the user has permission to do absolutely anything
  - when creating our first Google user account, we are creating our organization, and the email used is the super admin

## Identity and Access Management

- **custom roles:** we need to remember to keep the custom role updated
  - for example, when a released service gets new features, the predefined role for the service is updated with the required permissions to use the new feature. However, we need to manually add permissions to the custom role in order to use the service
- **service account impersonation:** refers to the ability of a service account to act on behalf of another user or service account, effectively assuming their identity and permissions for performing authorized actions
- **Google Cloud Directory Sync (GCDS):** automatically provisions users and groups from Active Directory to Cloud Identity or Google workspaces and implements a synchronization process that can be run on Google Cloud or in your on-premises environment
- **Active Directory:** a directory service developed by Microsoft and is a cornerstone in most corporate on-premises environments. It authenticates and authorizes all users and computers in a Windows environment

## Networking

- **SNAT (Source Network Address Translation):** SNAT is used when a network device needs to modify the source IP address of outgoing packets
- **DNAT (Destination Network Address Translation):** DNAT is used to modify the destination IP address of incoming packets
- **Cloud NAT:**
  - cloud NAT relies on a custom static route whose next hop is the **default internet gateway**
  - must hold **compute.networkAdmin** role in creating the NAT gateway on Cloud Router
  - instances with public IP addresses can not use Cloud NAT
  - <kbd><img width="666" alt="Screen Shot 2023-07-10 at 10 01 06 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/3f2adc8e-8e41-43f5-9195-a3204c4843b4"></kbd>
  - **Private Google Access enabled automatically**
  - we CAN use Cloud NAT with Shared VPC - setup in the host project
  - we CAN NOT use Cloud NAT with VPC peering
  - we can only use Cloud NAT in GKE for nodes and pods in **private cluster**
- **Cloud CDN (Content Delivery Network):** used for caching objects like web content to serve content closer to users, accelerating your websites and applications
  - only static content is cached
  - deliver content on GCP, another cloud, or an on-premises network
  - <kbd><img width="666" alt="Screen Shot 2023-07-10 at 10 33 47 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/623209c7-a739-46ee-8739-bb0f2c8ea2de"></kbd>
  - the three cache modes offered by Cloud CDN:
    - CACHE_ALL_STATIC
    - USE_ORIGIN_HEADERS
    - FORCE_CACHE_ALL
- **[VPC Best Practices and Architectures](https://app.exampro.co/student/material/gcp-architect/4375)**

## Hybrid Networking

- **[Cloud Router](https://app.exampro.co/student/material/gcp-architect/4376):** a networking service by GCP that enables dynamic routing and connectivity between VPC networks and on-premises networks or other networks in the cloud
  - Cloud Router dynamically exchanges routes between your VPC and on-premises networks by using BGP
 
## Compute Engine

- **sole tenant node:** a physical compute engine server that is dedicated to hosting only your project’s VMs. This can be used to keep your VMs physically separated from VMs in other projects **or to group your VMs together on the same host hardware**
  - best for the following scenarios:
    - performance
    - security and compliance
    - Windows license requirements
    - machine learning and data processing
  - **node template：** this is a regional resource that defines the properties of each node in a node group

## High Availability and Autoscaling

- **cloud run:** this is a serverless managed compute platform that enables you to run stateless containers that are invocable by requests or events
  - [cloud run I](https://app.exampro.co/student/material/gcp-architect/4378)
  - [cloud run II](https://app.exampro.co/student/material/gcp-architect/4379)
  - Each revision is automatically scaled to the number of container instances needed to handle all incoming requests
  - **traffic surges:** this term is used when Cloud Run may create slightly more container instances than the specified max instances value

## Anthos

- **Anthos:** allows organizations to build, deploy, and manage applications across different environments, including on-premises data centers, Google Cloud, and other public cloud providers
- <kbd><img width="666" alt="Screen Shot 2023-07-10 at 10 52 51 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/b647c131-e9d9-4106-a982-6156ee8f9912"></kbd>
- **Environ：** this is Google Cloud's concept for logically organizing clusters and other resources to let you use and manage multi-cluster capabilities and apply consistent policies across your systems, thus making administration of infrastructure easier
  - all attached clusters must be registered to Environ
  - <kbd><img width="666" alt="Screen Shot 2023-07-10 at 11 55 13 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/bf148982-ed78-431f-844d-2b709d322fb8"></kbd>
- **Anthos Clusters:**  provides a unified way to work with Kubernetes Clusters as part of Anthos, extending GKE to work in multiple environments. It gives a consistent, unified, and secure infrastructure, as well as cluster, and container management
- **User Cluster:**  where you deploy and run your containerized workloads and services
- **Admin Cluster:** An admin cluster in Anthos serves as the control plane for managing and orchestrating multiple user clusters
- **Anthos on VMWare:** the software that brings GKE to on-premises data centers and allows the creation, management, and upgrades of Kubernetes clusters in your on-premises environment
- **Anthos on Bare-metal:** allows take advantage of your existing infrastructure and offers the flexibility of running Anthos with no hypervisor. It gives the ability to deploy applications directly on your hardware infrastructure
- **Anthos on AWS:** hybrid cloud software that extends GKE to AWS

## Big Data and Machine Learning

- **Big Data:** refers to massive amounts of data that would typically be too expensive to store, manage and analyze using traditional database systems
- **Dataflow:** a fully-managed service for building and executing data processing pipelines
- **Tensoflow:** a free and open-source software library for machine learning and artificial intelligence. It can be used across a range of tasks but has a particular focus on training and inference of deep neural networks
- **Data Lifecycle**
  - Ingest, Store, Process & Analyze, Explore and Visualize
  - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 6 12 53 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/517c644f-67b4-4835-a9a8-ee917c16448b"></kbd>

## Infrastructure Automation DevOps

- **DevOps:**
  - It combines software development (Dev) and information technology operations (Ops) to enhance collaboration, communication, and efficiency in delivering software and service.
  - Traditionally, software development and operations were separate siloed functions within organizations. Developers focused on writing code and creating new features, while operations teams focused on deploying and managing the infrastructure required to run the software. This siloed approach often led to delays, miscommunication, and inefficiencies in the software delivery process.
  - DevOps aims to bridge the gap between development and operations by promoting collaboration, automation, and continuous integration and delivery. It encourages developers and operations teams to work closely together throughout the entire software lifecycle, from planning and development to deployment and maintenance.
  - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 6 34 06 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/c38c395d-b01b-4c61-956a-91cdc5e9b99c"></kbd>
  - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 6 35 58 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/bef08f1e-63da-4749-8e1c-b00feaf2d55b"></kbd>
- **Agile Software Development Life Cycle (SDLC):**
  - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 6 31 59 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/1ea6537f-5140-41a9-aa7b-3809b2046e6f"></kbd>
- **Continuous Integration (CI):** developers merge their code changes frequently, usually several times a day, into a central code repository. This triggers an automated build and testing process, where the integrated code is compiled, deployed, and tested against a predefined set of tests
- **Continuous Delivery (CD):**
  - It is a software development practice that enables teams to deliver software in a frequent, reliable, and automated manner. It extends the principles of Continuous Integration (CI) by automating the entire software delivery pipeline, from code changes to production deployment
  - In Continuous Delivery, the goal is to ensure that software is always in a releasable state, ready to be deployed to production at any time. The focus is on reducing the time and effort required to deliver new features, bug fixes, and enhancements while maintaining a high level of quality and stability
- **Continuous Integration (CI) vs Continuous Delivery (CD):**
  - <img width="666" alt="Screen Shot 2023-07-12 at 6 54 47 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/e7061f54-b430-4c09-9dd1-da07131d1f78">
- **Configuration Management:** the process of maintaining systems, such as computer software in a desired and consistent state
  - Puppet is an example tool of Configuration Management
- **Deployment Strategies:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 7 30 16 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/3bf2f606-9180-4538-8926-1f1f1352355a"></kbd>
  - **Recreate:** completely delete version one and create version two. **It involves downtime**
  - **Rolling update:** slowly replace the version on each node. **It does not involve downtime**
  - **Blue/Green:** it has **no downtime**
  - **A/B testing:** also known as split testing or bucket testing, is a method used to compare two or more variations of a webpage, app interface, or other elements to determine which one performs better in terms of user engagement or desired outcomes. It is a data-driven approach to make informed decisions and optimize the user experience.
  - **Shadow Testing:**
    - <kbd><img width="666" alt="Screen Shot 2023-07-12 at 7 26 17 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/b80819b2-bd0e-4da4-916f-8b11534ed4f4"></kbd>
- **Cloud Build:**
  - CI/CD tool executes your builds on GCP as a series of steps including importing source code, executing a build, and producing artifacts
  - each build step runs inside a Docker container
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 1 23 05 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/a5acd80f-24ff-48ef-bb4d-366ccae2f575"></kbd>
- **Container Registry:**
  - a single private repository to manage Docker images, **perform vulnerability analysis** and **enable CI/CD integrations** for setting up fully automated Docker pipelines

## Migration to Google Cloud

- **Lift and Shift:** requires the least amount of time to migrate
- **Google Cloud Adoption Framework:**
  - to guide organizations in their adoption and implementation of Google Cloud services. It provides a structured approach and methodology for organizations to plan, execute, and optimize their cloud adoption journey with Google Cloud
  - **Tactical:** you can achieve the short-term business objective of optimizing costs within your existing IT solutions and you look to execute projects with minimal change to your people, technology, and process
  - **Strategic:** expands the adoption of Google Cloud by migrating more workloads and applications. It involves defining a comprehensive cloud strategy aligned with business objectives and identifying the appropriate tools, services, and architectures for the organization's specific needs. The goal is to achieve scalability, efficiency, and cost optimization through the strategic use of Google Cloud services
  - **Transformational:** to drive significant business transformation and innovation. It involves exploring advanced capabilities and services offered by Google Cloud, such as artificial intelligence, machine learning, big data analytics, and Internet of Things (IoT). The goal is to unlock new business opportunities, drive innovation, and gain a competitive edge through the transformative power of Google Cloud technologies
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 1 41 28 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/4f9295c0-a429-46a8-adbe-0f1cc907e7a9"></kbd>
- **Migration Path**
  - **Migration Phase 1: Access** your job is to gather all the information about the workloads you want to migrate and their current runtime environments and take inventory of what applications exist in your environment
  - **Migration Phase 2: Plan:** where you start to configure and provision cloud infrastructure and services that will support your workloads on Google Cloud
  - **Migration Phase 4: Optimize** where you train your development and operations team to take full advantage of the new cloud environment as well as monitor everything to ensure everything in the environment is working as expected
  - **Proof of Concept (PoC):** is a small-scale project or experiment designed to validate the feasibility, viability, and potential of a concept, idea, or technology. It is typically conducted to demonstrate the practicality and benefits of a solution before committing to full-scale implementation
- **Storage Transfer Service:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 2 13 35 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/5945663f-809e-41da-ab65-b5796f88bca3"></kbd>
- **Transfer Appliance**
  - a high-capacity storage device that enables you to transfer and securely ship your data to a Google upload facility, where data is uploaded to your Cloud Storage
  - good for when your data is more than 10TB or needs more than a week to upload
  - good for when Transfer Appliance is available in your area
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 2 17 00 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/eaf4dd7c-99fc-4f26-bbda-06a59d975aef"></kbd>
- **one-off transfer:** an one-time transaction that is not expected to be repeated on a regular basis
- **Migrate for Compute Engine:**  
  - continously replicate disk data from the source VMs to GCP without causing any downtime on the source
  - will replicate data unitl you perform a final cut over to you migrated VMs
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 2 23 49 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/5ee3f3ea-7762-4e31-9c18-a5b6cffa4b64"></kbd>
- **Database Migration Service:**
  - **one-time migration:**
    - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 2 29 05 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/39b39bfe-b055-48ac-b1a3-4777658ecb21"></kbd>
  - **continous migration:**
    - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 2 31 05 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/9462c257-dda5-477d-8917-ddcbe1ed7a39"></kbd>
  - serverless

## System Design Consideration

- **Error Budget:** a concept used in software development and operations to quantify the acceptable level of errors or failures that can occur in a system or service over a defined period of time. It is a quantitative measure that sets a limit on the amount of errors or downtime that can be tolerated within a specific period while still meeting the service level objectives (SLOs) or service level agreements (SLAs) of the system
- **Development velocity:** refers to the rate at which a software development team can deliver new features, fixes, or improvements to a product or software system
- **Altering Delay:**
  - refers to the practice of intentionally delaying the response or feedback to a user or system in order to achieve a desired outcome or improve the user experience
  - For example, a system that handles a large volume of requests may introduce a delay between requests to prevent the system from becoming overloaded and to ensure that all requests are processed in a timely manner
- **RPO and RTO:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 4 42 29 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/3ed22c7f-29a4-473c-9d01-2ff460162563"></kbd>
  - The lower the RPO and RTO, the higher the cost
  - the higher the RPO and RTO, the lower the cost
- **Warm Disaster Recovery Pattern:** implemented to keep RTO and RPO values as small as possible without the effort and expense of a **fully** redundant environment

## Security and Compliance

- **Encryption by default:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 6 54 43 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/dfaca61b-c9f8-4ab0-a0ac-97bd62318402"></kbd>
- **DEK:** data encryption key
- **KEK:** key encryption key
- **Envelope Encryption:**  In envelope encryption, a data encryption key (DEK) is used to encrypt the data and a master encryption key (MEK) is used to encrypt the DEK. This creates an "envelope" of encryption around the data, which provides an additional layer of security
- **Encryption Key Hierarchy:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 7 01 12 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/964aacf8-83b9-4e7b-8f8f-8ac157f2a088"></kbd>
- **key rotation:** key rotation is a security practice that involves periodically replacing cryptographic keys used to protect sensitive data or systems with new ones. The purpose of key rotation is to limit the amount of time that a compromised key can be used to access sensitive data or systems, in case the key is ever compromised
- **object hierarchy:**
  - how Cloud Key Management Service (KMS) stores keys
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 7 15 07 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/17385525-c5e0-464f-851a-b295aa1944d1"></kbd>
- **key state:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 7 17 52 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/0becb26a-c3f4-48b2-b161-f2fbf34b2d1e"></kbd>
- **key management:**
  - <kbd><img width="666" alt="Screen Shot 2023-07-13 at 7 20 54 PM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/7af2e2de-8576-4638-aaca-018b0ff80df9"></kbd>
- **cloud HSM (Hardware Security Module):** a dedicated device or service that provides secure cryptographic key storage and management in a cloud environment. HSMs are designed to protect and manage the cryptographic keys used to encrypt and decrypt sensitive data, such as financial transactions, personal information, and intellectual property
- **EKM:** External Key Management
- **Secret:** secure objects that store sensitive data, such as password, OAuth tokens, and API keys
- **Secret Manager:** store, manage, access, and audit secrets across GCP
  - no need to setup, encryption by default (using TLS/AES-256 by default), and secret can be viewed with permissions
  - adding secrets are strongly consistent, while all other operations are eventually consistent
  - replication policy: **automatic** (default and recommended) and **user-managed**
- **Identity-Aware Proxy (IAP):**
  -  








# Google Cloud Professional Cloud Architect

Course Files for Google Cloud Professional Cloud Architect Course by Antoni Tzavelas

If you feel that something should be corrected or updated please reach out and let me know at antoni@antonit.com

If you are looking to help me with a fix, feel free to submit a PR with your suggested fixes and I will kindly review it.

