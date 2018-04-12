# AWS:

### These are a collection of my Notes, for detailed information refer to [F5 Documentation](http://clouddocs.f5.com/cloud/public/v1/) directly as this repo my not contain all information.

Started with 11.4.1

Current Supported TMOS is [AMI's](https://github.com/F5Networks/f5-aws-cloudformation/tree/master/AMI%20Maps):

- 11.5.4
- 11.6.2
- 12.1.2
- 13.0.0
- 13.1.0.2

Current Support Throughputs in [Market Place](https://aws.amazon.com/marketplace/seller-profile?id=74d946f0-fa54-4d9f-99e8-ff3bd8eb2745):
- 25Mbps to 5000Mbps

Instance Size Change: supported starting in 11.6 for BYOL, in Badger for utility licenses.

Software Upgrades: supported starting 11.5.1 HF8 +  11.6.0 HF4 for BYOL and Utility

### GitHub:

Every release (6-8 weeks) is tagged for [historical reference](https://github.com/F5Networks/f5-aws-cloudformation/blob/master/aws-bigip-version-matrix.md)

### CloudFormation Templates:

We use [troposphere project](https://github.com/cloudtools/troposphere) to build our [CFT's](https://github.com/F5Networks/f5-aws-cloudformation/tree/master/build)

All CFT's have Outputs

awscli examples (deploy_via_bash)
[convenience scripts](https://github.com/F5Networks/f5-aws-cloudformation/tree/master/deploy) for stitching two CFTs for outputs

[Template Definitions](https://github.com/F5Networks/f5-aws-cloudformation/tree/master/deploy#deploy):
- "existing-stack": more aligned with whats seen, adds BIP-IP to VPC, subnet, route-tables, webserver, and security groups
- "full-stack": creates a full example deployment (VPC, subnets, route-tables, security groups, sample webserver and a Big-IP) so you can quickly have a complete working environment from scratch to explore.
- "infra-only": creates a VPC, subnet, route-tables, webserver, and security groups.
- "network-only": creates a VPC, subnets, route-tables.
- "security-groups": creates reference security groups.

### AWS Features:

- IAM Roles to EC2 instance 12.1
- [Cloud-init](http://clouddocs.f5.com/cloud/public/v1/cloudinit.html)
- [Cloud-Libs](https://github.com/F5Networks/f5-cloud-libs)


### iApps:

- HA setup
- [Service Discovery](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-service-discovery)
  - Tag a VM resource: The BIG-IP VE will discover the primary public or private IP addresses for the primary NIC configured for the tagged VM.
  - Tag a NIC resource: The BIG-IP VE will discover the primary public or private IP addresses for the tagged NIC. Use this option if you want to use the secondary NIC of a VM in the pool.
- [Cloud_logger](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-cloud-logger) - Cloudwatch Format

### Logging

- [ELK - (E)lasticsearch (L)ogstash and (K)ibana](https://johntuckner.me/2017/02/20/elk-integrating-f5-ltm-and-asm/)
- [Cloud_logger](https://github.com/F5Networks/f5-cloud-iapps/tree/master/f5-cloud-logger)

### Training

- [Part 1 : AWS Networking Basics](https://devcentral.f5.com/articles/f5-in-aws-part-1-aws-networking-basics)
- [Part 2: Running BIG-IP in an EC2 Virtual Private Cloud](https://devcentral.f5.com/articles/f5-in-aws-part-2-running-big-ip-in-an-ec2-virtual-private-cloud)
- [Part 3: Advanced Topologies and More on Highly-Available Services](https://devcentral.f5.com/articles/part-3-of-big-ip-in-ec2-advanced-topologies-and-more-on-highly-available-services)
- [Part 4: Orchestrating BIG-IP Application Services with Open-Source Tools](https://devcentral.f5.com/articles/f5-in-aws-part-4-orchestrating-big-ip-application-services-with-open-source-tools)
- [Part 5: Cloud-init, Single-NIC, and Auto Scale Out of BIG-IP in v12](https://devcentral.f5.com/articles/f5-in-aws-part-5-cloud-init-single-nic-and-scale-out-of-big-ip-in-v12-21476)
