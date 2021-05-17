# CTM-infra
Objectives from the assignment pdf:
- Produce a simle cluster web service setup in AWS - Done
```
   Here I have an EKS cluster running, deployed with terraform.
   I have an ingress controller and a few helm charts deployed with providers
```
- Cluster hit with get request returns a simple hello world with data and time - Done
```
   App in golang that refreshes the time and a salutation when hit with GET request
```
- infrastructure and pipelines as code - Done
```
   Pipeline created in github actions, with tests written in go.
```
- Tools that are transferable or platform agnostic - done
```
   All resources definied as code. A possible improvement here would be to make even more use of helm.
```
- Products deployed should be highly available, scalable and maintainable and monitored - Done
```
  cluster using an NLB ingress controller, capable of handling a multitude of requests and balance the load through pods/services. 
  Deployment resources highly used, allowing the system to self heal and scale with ease.
  A possible improvement would be to make use of livelyness and rediness in the deployment definition
  
  For monitorization, I have instrumented my golang application with prometheus, installed prometheus and grafana to scrape my app.
```
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
2. Clone the project clone 
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
- security-groups.tf: <br/>
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
| Terraform-aws-modules/eks/aws | 
| Terraform-aws-modules/vpc/aws | 


- Requirements:

| Requirements                          | 
| ------------------------------------- | 
| Cluster: 2 Worker nodes t2.small       | 
| Root volume type GP2                  |
| All assets on a separate VPC          |


- Online sources:
https://learn.hashicorp.com/tutorials/terraform/eks
https://managedkube.com/kubernetes/k8sbot/troubleshooting/imagepullbackoff/2019/02/23/imagepullbackoff.html

