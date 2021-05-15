# CTM-infra
ctm infrastructure on AWS


The project is composed by 3 repos:
    CTM-infra
    Resources
    application
    

This repo is for CTM-infra:
- Permissions:
The AWS user needs the necessary permissions to build this project,have used an administrator user to build it.
For production a restriction guide advised here(https://github.com/terraform-aws-modules/terraform-aws-eks/blob/master/docs/iam-permissions.md)

- Build:
1. clone the project
2. In the main folder build with the following commands:<br />
```
   $ terraform plan 
   $ terraform apply
```
The project contains 5 files:
- vpc.tf: <br/> 
Creates the VPC, using the VPC AWS module. This is a battle tested flexible module.

- versions.tf: 
Sets restrictions regarding versions available

- Security-groups.tf: 
Sets the security groups used in the project

- outputs.tf: 
Returns information about the build

- kubernetes.tf: 
Sets information for host, token and cert.

- eks-kluster.tf:
In this file the cluster and worker nodes are created.


       


