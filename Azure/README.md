# Azure:

### These are a collection of my Notes, for detailed information refer to [F5 Documentation](http://clouddocs.f5.com/cloud/public/v1/) directly as this repo my not contain all information.

Azure Started with 12.0.0

Current Supported [TMOS](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-bigip-version-matrix.md):
BIG-IP
- 13.1.0700
- 12.1.303000
BIG-IQ
- 6.0

Current Supported throughputs [Market Place](https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=F5%20Networks&page=1):
- 25Mbps to 3000Mbps

Instance Size Change: supported starting beginning with 12.0.0

Software Upgrades: supported starting beginning with 12.0.0

### GitHub:

Every release (6-8 weeks) is tagged for [historical reference](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-bigip-version-matrix.md)

### ARM Templates:

We use [Build Scripts](https://github.com/F5Networks/f5-azure-arm-templates/tree/master/build) to Create the ARM Templates

You can  [Modify](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-update-bigip-image.md) the ARM Template to specify
a required image

All ARM Templates have a **AzureCLI** and **PowerShell** equivalents

[Template Definitions](https://github.com/F5Networks/f5-azure-arm-templates/tree/master/supported):
- "existing_stack": more aligned with whats seen, adds BIP-IP to and existing Resource Group
- "new_stack": creates a full example deployment (resource group, networks, user defined route, network security groups and a BIG-IP) so you can quickly have a complete working environment from scratch to explore.
- "prod_stack": similar to a "new_stack" however this will **not** contain a public address for the BIG-IP
- "learning_stack": this is used for learning within the environment, it contains a BIGIP and a webserver to work with


### Azure Features:

- [168.63.129.16](https://blogs.msdn.microsoft.com/mast/2015/05/18/what-is-the-ip-address-168-63-129-16/), this address can be thought of as an IP Helper Address for Azure worldwide, this address is used to bring an instance online passing information, it is also used to communicate from Azure to an instance. Denying this address to/from an instance ***will*** break all kinds of things and cause ARM templates to fail.
- [waagent](http://clouddocs.f5.com/cloud/public/v1/azure/Azure_waagent.html) is used to interact with Azure API, and is only updated when a new BIG-IP is loaded into Azure, you should **not** install this on your own
- [customConfig](http://clouddocs.f5.com/cloud/public/v1/azure/Azure_solutions101.html) you have the ability to add TMSH calls directly into the ARM template with customConfig
- [Cloud-Libs](https://github.com/F5Networks/f5-cloud-libs) have different use cases (Licensing, etc), however they are pulled down during the build of the BIG-IP which means the BIG-IP ***MUST*** be able to reach this repo during build. The Build may complete however it might not be in the desired configuration state specified in the ARM template.


### iApps:

- [Service Discovery](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-service-discovery) - [Video](https://devcentral.f5.com/articles/onboarding-f5-in-cloud-part-2-service-discovery-27486)
  - Tag a VM resource: The BIG-IP VE will discover the primary public or private IP addresses for the primary NIC configured for the tagged VM.
  - Tag a NIC resource: The BIG-IP VE will discover the primary public or private IP addresses for the tagged NIC. Use this option if you want to use the secondary NIC of a VM in the pool.
  - Tag a Virtual Machine Scale Set resource: The BIG-IP VE will discover the primary private IP address for the primary NIC configured for each Scale Set instance. Note you must select Private IP addresses in the iApp template if you are tagging a Scale Set.

- The iApp first looks for NIC resources with the tags you specify. If it finds NICs with the proper tags, it does not look for VM resources. If it does not find NIC resources, it looks for VM resources with the proper tags. In either case, it then looks for Scale Set resources with the proper tags.
- [Cloud_logger](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-cloud-logger) - [Video](https://www.youtube.com/watch?v=X3B_TOG5ZpA&feature=youtu.be)
  - OMS Formatted logs for Modules (ASM/APM/AFM and LTM)

### Solutions

- [Azure Security Center](https://devcentral.f5.com/articles/deploying-f5s-web-application-firewall-in-microsoft-azure-security-center-26785)
  - [Add more Applications to ASC WAF](https://github.com/F5Networks/f5-azure-arm-templates/tree/master/experimental/reference/scripts)
- [Office 365 Federation (SAML)](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/f5-networks.f5-o365-federation-payg?tab=Overview)

### Training

- [The Hitchhiker’s Guide to BIG-IP in Azure](https://devcentral.f5.com/articles/the-hitchhikers-guide-to-big-ip-in-azure-26852)
- [The Hitchhiker’s Guide to BIG-IP in Azure – “Deployment Scenarios”](https://devcentral.f5.com/articles/the-hitchhikers-guide-to-big-ip-in-azure-deployment-scenarios-26853)
- [The Hitchhiker’s Guide to BIG-IP in Azure – “High Availability”](https://devcentral.f5.com/articles/the-hitchhikers-guide-to-big-ip-in-azure-high-availability-26962)
- [The Hitchhiker’s Guide to BIG-IP in Azure – “Life Cycle Management”](https://devcentral.f5.com/articles/the-hitchhikers-guide-to-big-ip-in-azure-life-cycle-management-26988)
