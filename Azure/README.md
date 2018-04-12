# Azure:

### These are a collection of my Notes, for detailed information refer to [F5 Documentation](http://clouddocs.f5.com/cloud/public/v1/) directly as this repo my not contain all information.

Azure Started with 12.0.0

Current Supported [TMOS](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-bigip-version-matrix.md):
- 13.1.0200

Current Support Throughputs in [Market Place](https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=F5%20Networks&page=1):
- 25Mbps to 3000Mbps

Instance Size Change: supported starting beginning with 12.0.0

Software Upgrades: supported starting beginning with 12.0.0

### GitHub:

Every release (6-8 weeks) is tagged for [historical reference](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-bigip-version-matrix.md)

### ARM Templates:

We use [Build Scripts](https://github.com/F5Networks/f5-azure-arm-templates/tree/master/build) to Create the ARM Templates

If there as an available image you can [Modify](https://github.com/F5Networks/f5-azure-arm-templates/blob/master/azure-update-bigip-image.md) the ARM Template to specify
a required image

All CFT's have Outputs

awscli examples (deploy_via_bash)
[convenience scripts](https://github.com/F5Networks/f5-aws-cloudformation/tree/master/deploy) for stitching two CFTs for outputs

[Template Definitions](https://github.com/F5Networks/f5-azure-arm-templates/tree/master/supported):
- "existing_stack": more aligned with whats seen, adds BIP-IP to and existing Resource Group
- "new_stack": creates a full example deployment (resource group, networks, user defined route, network security groups and a BIG-IP) so you can quickly have a complete working environment from scratch to explore.
- "prod_stack": similar to a "new_stack" however this will **not** contain a public address for the BIG-IP


### Azure Features:

- [waagent](http://clouddocs.f5.com/cloud/public/v1/azure/Azure_waagent.html) is only updated when a new BIG-IP is loaded into Azure, you should **not** install this on your own
- [customConfig](http://clouddocs.f5.com/cloud/public/v1/azure/Azure_solutions101.html) you have the ability to add TMSH calls directly into the ARM template with customConfig
- [Cloud-Libs](https://github.com/F5Networks/f5-cloud-libs) have different use cases (Licensing, etc), however they are pulled down during the build of the BIG-IP which means the BIG-IP ***MUST*** be able to reach this repo during build. The Build may complete however it might not be in the desired configuration state specified in the ARM template.


### iApps:

- [Service Discovery](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-service-discovery)
  - Tag a VM resource: The BIG-IP VE will discover the primary public or private IP addresses for the primary NIC configured for the tagged VM.
  - Tag a NIC resource: The BIG-IP VE will discover the primary public or private IP addresses for the tagged NIC. Use this option if you want to use the secondary NIC of a VM in the pool.
- [Cloud_logger](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-cloud-logger) - OMS Formatted

### Logging

- [ELK - (E)lasticsearch (L)ogstash and (K)ibana](https://johntuckner.me/2017/02/20/elk-integrating-f5-ltm-and-asm/)
- [Cloud_logger](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-cloud-logger)

### Training

- [Part 1 : AWS Networking Basics](https://devcentral.f5.com/articles/f5-in-aws-part-1-aws-networking-basics)
- [Part 2: Running BIG-IP in an EC2 Virtual Private Cloud](https://devcentral.f5.com/articles/f5-in-aws-part-2-running-big-ip-in-an-ec2-virtual-private-cloud)
- [Part 3: Advanced Topologies and More on Highly-Available Services](https://devcentral.f5.com/articles/part-3-of-big-ip-in-ec2-advanced-topologies-and-more-on-highly-available-services)
- [Part 4: Orchestrating BIG-IP Application Services with Open-Source Tools](https://devcentral.f5.com/articles/f5-in-aws-part-4-orchestrating-big-ip-application-services-with-open-source-tools)
- [Part 5: Cloud-init, Single-NIC, and Auto Scale Out of BIG-IP in v12](https://devcentral.f5.com/articles/f5-in-aws-part-5-cloud-init-single-nic-and-scale-out-of-big-ip-in-v12-21476)
