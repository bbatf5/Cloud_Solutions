# AWS:

### Notes

Started with 11.4.1

Current Supported TMOS is AMI's:

- 11.5.4
- 11.6.2
- 12.1.2
- 13.0.0
- 13.1.0.2

Current Support Throughputs in Market Place:
- 25Mbps to 5000Mbps

Instance Size Change: supported starting in 11.6 for BYOL, in Badger for utility licenses.

Software Upgrades: supported starting 11.5.1 HF8 +  11.6.0 HF4 for BYOL and Utility

### GitHub:

Every release (6-8 weeks) is tagged for historical reference

### CloudFormation Templates:

We use troposphere project to create our CFT's https://github.com/cloudtools/troposphere

All CFT's have Outputs

awscli examples (deploy_via_bash)
convenience scripts for stitching two CFTs for outputs

Template Definitions:
- "existing-stack": more aligned with whats seen, adds BIP-IP to VPC, subnet, route-tables, webserver, and security groups
- "full-stack": creates a full example deployment (VPC, subnets, route-tables, security groups, sample webserver and a Big-IP) so you can quickly have a complete working environment from scratch to explore.
- "infra-only": creates a VPC, subnet, route-tables, webserver, and security groups.
- "network-only": creates a VPC, subnets, route-tables.
- "security-groups": creates reference security groups.

### AWS Features:

- IAM Roles to EC2 instance 12.1
- Cloud-init


### iApps:

- HA setup
- Service Discovery
  - Tag a VM resource: The BIG-IP VE will discover the primary public or private IP addresses for the primary NIC configured for the tagged VM.
  - Tag a NIC resource: The BIG-IP VE will discover the primary public or private IP addresses for the tagged NIC. Use this option if you want to use the secondary NIC of a VM in the pool.
- Cloud-Logger - Cloudwatch Format

### Logging

- 
