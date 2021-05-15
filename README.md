# CTM-infra
CTM infrastructure on AWS


The project is composed by 3 repos:<br/>
- CTM-infra<br/>
- CTM-Resources<br/>
- CTM-application<br/>
    

This repo is for CTM-infra:<br/>
Here you will find all files to create an EKS cluster in terraform.<br/>
- Permissions:<br/>
The AWS CLI user needs the necessary permissions to build this project. For production a restriction guide is advised here(https://github.com/terraform-aws-modules/terraform-aws-eks/blob/master/docs/iam-permissions.md) for EKS, but additional permissions
might be needed.

- Build:
1. Setup your AWS CLI user 
```
    https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html
```
3. Clone the project clone 
```
   $ git clone git@github.com:celsoRodrigues/CTM-infra.git
```
3. Install terraform (https://learn.hashicorp.com/tutorials/terraform/install-cli)
4. In the main folder build with the following commands:<br />
```
   $ terraform init
   $ terraform plan 
   $ terraform apply
```
5. Inside the CTM-infra repo, configure kubectl:<br/>
```
  # CTM-infra
CTM infrastructure on AWS


The project is composed by 3 repos:<br/>
- CTM-infra<br/>
- CTM-Resources<br/>
- CTM-application<br/>
    

This repo is for CTM-infra:<br/>
Here you will find all files to create an EKS cluster in terraform.<br/>
- Permissions:<br/>
The AWS CLI user needs the necessary permissions to build this project. For production a restriction guide is advised here(https://github.com/terraform-aws-modules/terraform-aws-eks/blob/master/docs/iam-permissions.md) for EKS, but additional permissions
might be needed.

- Build:
1. Setup your AWS CLI user 
```
    https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html
```
3. Clone the project
```
   $ git clone git@github.com:celsoRodrigues/CTM-infra.git
```
3. Install terraform (https://learn.hashicorp.com/tutorials/terraform/install-cli)
4. In the main folder build with the following commands:<br />
```
   $ terraform init
   $ terraform plan 
   $ terraform apply
```
5. Inside the CTM-infra repo, configure kubectl:<br/>
```
  $ aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
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
