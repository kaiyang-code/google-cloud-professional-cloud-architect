# Notes

## Resource Manager

- **super admin:** the user that you used to sign up for Google Cloud
  - the user has the permission to do absolutely anything
  - when creating our first google user account, we are creating our organization, and the email used is the super admin

## Identity and Access Management

- **custom roles:** we need to remember to keep the custom role updated
  - for example, when a released service gets new features, the predefined role for the service is updated with the required permissions to use the new feature. However, we need to mannually add permissions to the custom role in order to use the service
- **service account impersonation:** refers to the ability of a service account to act on behalf of another user or service account, effectively assuming their identity and permissions for performing authorized actions
- **Google Cloud Directory Sync (GCDS):** automatically provisions users and groups from Active Directory to Cloud Identity or Google workspaces and implements a synchronization process that can be run on Google Cloud or in your on-premises environment
- **Active Directory:** a directory service developed by Microsoft and is a cornerstone in most corporate on-premises environments. It authenticates and authorizes all users and computers in a Windows environment

## Networking

- **SNAT (Source Network Address Translation):** SNAT is used when a network device needs to modify the source IP address of outgoing packets
- **DNAT (Destination Network Address Translation):** DNAT is used to modify the destination IP address of incoming packets
- **Cloud NAT:**
  - cloud NAT replies on custom static route whose next hop is the **default internet gateway**
  - must hold **compute.networkAdmin** role to create the NAT gateway on Cloud Router
  - instances with public IP addresses can not use Cloud NAT
  - <kbd><img width="666" alt="Screen Shot 2023-07-10 at 10 01 06 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/3f2adc8e-8e41-43f5-9195-a3204c4843b4"></kbd>
  - **Private Google Access enabled automatically**
  - we CAN use Cloud NAT with Shared VPC - setup in host project
  - we CAN NOT user Cloud NAT with VPC peering
  - we can only use Cloud NAT in GKE for nodes and pods in **private cluster**
- **Cloud CDN (Content Delivery Network):** used for caching objects like web content to serve content closer to users accelerating your websites and applications
  - only static content is cached
  - deliver content on GCP, another cloud, or on-premises network
  - <kbd><img width="666" alt="Screen Shot 2023-07-10 at 10 33 47 AM" src="https://github.com/kaiyang-code/google-cloud-professional-cloud-architect/assets/57576013/623209c7-a739-46ee-8739-bb0f2c8ea2de"></kbd>
  - the three cache modes offered by Cloud CDN:
    - CACHE_ALL_STATIC
    - USE_ORIGIN_HEADERS
    - FORCE_CACHE_ALL
- **[VPC Best Practices and Architectures](https://app.exampro.co/student/material/gcp-architect/4375)**

## Hybrid Networking

- **[Cloud Router](https://app.exampro.co/student/material/gcp-architect/4376):** a networking service by GCP that enables dynamic routing and connectivity between VPC networks and on-premises networks or other networks in the cloud
  - Cloud Router dynamically exchanges routes between your VPC and on-premises networks by using BGP

# Google Cloud Professional Cloud Architect

Course Files for Google Cloud Professional Cloud Architect Course by Antoni Tzavelas

If you feel that something should be corrected or updated please reach out and let me know at antoni@antonit.com

If you are looking to help me with a fix, feel free to submit a PR with your suggested fixes and I will kindly review it.

