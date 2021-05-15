# CTM-infra
ctm infrastructure on AWS


The project is composed by 3 repos:
    CTM-infra
    Resources
    application
    

This repo is for CTM-infra:
- Permissions:<br/>
The AWS CLI user needs the necessary permissions to build this project. For production a restriction guide is advised here(https://github.com/terraform-aws-modules/terraform-aws-eks/blob/master/docs/iam-permissions.md) for EKS, but additional permissions
might be needed.

- Build:
1. Setup your AWS CLI user 
2. clone the project clone 
```
   $ git clone git@github.com:celsoRodrigues/CTM-infra.git
```
3. In the main folder build with the following commands:<br />
```
   $ terraform init
   $ terraform plan 
   $ terraform apply
```
The project contains 5 files:
- vpc.tf: <br/> 
Creates the VPC, using the VPC AWS module. This is a battle tested flexible module.

- versions.tf: <br/>
Sets restrictions regarding versions available
- Security-groups.tf: <br/>
Sets the security groups used in the project
- outputs.tf: <br/>
Returns information about the build
- kubernetes.tf: <br/>
Sets information for host, token and cert.
- eks-kluster.tf: <br/>
In this file the cluster and worker nodes are created.

- Modules:

| Modules used                  | 
| ----------------------------- | 
| terraform-aws-modules/eks/aws | 
| terraform-aws-modules/vpc/aws | 


- Requirements:

| Requirements                          | 
| ------------------------------------- | 
| Clster: 2 Worker nodes t2.small       | 
| root volume type GP2                  |
| All assets on a separate VPC          |


- Online sources:
https://learn.hashicorp.com/tutorials/terraform/eks
https://managedkube.com/kubernetes/k8sbot/troubleshooting/imagepullbackoff/2019/02/23/imagepullbackoff.html
