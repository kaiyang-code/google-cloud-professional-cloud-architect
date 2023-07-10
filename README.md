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
- **Anthos Clusters:**  provides a unified way to work with Kubernetes Clusters as part of Anthos, extending GKE to work in multiple environments. It gives a consistent, unified, and secure infrastructure, as well as cluster, and container management
- **User Cluster:**  where you deploy and run your containerized workloads and services
- **Admin Cluster:** An admin cluster in Anthos serves as the control plane for managing and orchestrating multiple user clusters
- **Anthos on VMWare:** the software that brings GKE to on-premises data centers and allows the creation, management, and upgrades of Kubernetes clusters in your on-premises environment
- **Anthos on Bare-metal:** allows take advantage of your existing infrastructure and offers the flexibility of running Anthos with no hypervisor. It gives the ability to deploy applications directly on your hardware infrastructure
- **Anthos on AWS:** hybrid cloud software that extends GKE to AWS
- 



# Google Cloud Professional Cloud Architect

Course Files for Google Cloud Professional Cloud Architect Course by Antoni Tzavelas

If you feel that something should be corrected or updated please reach out and let me know at antoni@antonit.com

If you are looking to help me with a fix, feel free to submit a PR with your suggested fixes and I will kindly review it.

