How to find drift detection 
  1. terraform refresh  or  cronjob - terraform refresh
  2. Create a strict Rule if any IAM user wants to change any resources in AWS manually he/she needs to get approval from a manager
  3. Audit log - Create a Lambda function to send alerts to the team if there is any change for resources managed by Terraform 
       (Like who changed resources IAM user name and timestamp ..)

I have created resources using Terraform and deleted some resources manually how to update state-file as per deleted resources
   -- terraform state list
   after the resource is deleted manually from the console, then
   -- terraform refresh

To force unlock lock-id
#terraform force-unlock <Dynamo-DB-LOCK_ID>

How to migrate manual deployed resources to terraform
  - Write a main.tf 
      provider "AWS" {
    region = "us-east-2"  
}
    import {
       to = "aws_instance.vm-name"
       id = "Ec2-ID"
      }
 -  terraform plan -generate-config-out=vm-name.tf (This will generate terraform code in vm-name.tf copy and pate all code to main.tf and remove import block)
 - terraform import aws_instance.vm-name <EC2-ID> (it will generate the state file)

How to install anything during the provisioning process using Terraform? or what are the provisioners in Terraform?
  provisioners are used to execute scripts or commands on the local machine or the remote machine during the provisioning process.
  Local Exec Provisioner (local-exec):
    provisioner "local-exec" {
    command = "echo 'Hello, World!'"
  }
  Remote Exec Provisioner (remote-exec):
     provisioner "remote-exec" {
      inline = [
        "sudo apt-get update",
      "sudo apt-get install -y nginx",
    ]
  File Provisioner (file):
    provisioner "file" {
    source      = "local/path/to/file.txt"
    destination = "/remote/path/on/instance/file.txt"
  }

How would you save any particular resource while destroying the complete infra.? Lifecycle in terraform?
- lifecycle {
    create_before_destroy = true
    prevent_destroy       = true
    ignore_changes        = ["tags"]
  }
How to destroy particular resources in terraform? 
- terraform destroy -target=resource_type.resource_name

How to manage terraform data in multiple env?
Workspace
re-usable modules

how may ways variables can provide to terraform?
Variable Declarations: we can define directly in main.tf
Variable files: variables.tfvars
Environment Variables: export TF_VAR_region="us-west-2"
Command-Line Flags: terraform apply -var="region=us-west-2"

What will happen when you run the terraform init command? what files will be created? 
- Backend Configuration: If ur using a remote state then the backend will be initialized
- Plugin Initialization: download plugins mentioned in config files like (AWS,GCP) in a Dir .terraform
- Lock file creation: .terraform.lock.hcl

Explain core terraform end-to-end workflow to deploy and delete resources in AWS
Workflow:
- write: like main.tf / provider.tf
- init: terraform init
- validate: terraform validate
- plan: terraform plan
- apply: terraform apply -auto-approve
- destroy: terraform destroy -auto-approve

we have existing terraform infra created in AWS, now one particular resource needs to be re-created, whenever we do the next apply.
terraform taint 
  terraform state list
  terraform taint "resource-name"
  terraform plan
  terraform apply

Explain the various types of META arguments in terraform 
 depends_on: One resource is created before another resource
 count: to deploy multiple resources like EC2 (count is used when you want to create multiple instances of a resource with the same configuration.)
         Creating a fixed number of identical instances, such as multiple EC2 instances in the same subnet.
     count = 3
tags= {
Name = "my-vm-${count.index + 1}"
}
 for_each: loop (Key = value) (for_each is used when you want to create multiple instances of a resource with distinct configurations.)
           Creating a variable number of instances with different configurations, such as multiple EC2 instances with different AMIs.
            
for_each = {
instance1 = { ami = "ami-name"}
instance2 = { ami = "ami-name"}
}
ami = each.value.ami
tags ={
Name = each.key
} 

who created the "terraform.tfstate.backup1" file and under which scenario it is created?
- When you run terraform destroy then "backup" file will be created, it has all resource info of previously deployed infra using terraform config
  we can move backup file to statefile and apply it to deploy previously created resources. 

what is import in terraform? 
    terraform import resource-block.<resource_name> <resource_ID>
  - This is useful when you have resources that were created outside of Terraform, and you want to start managing them using Terraform without recreating them. 

if someone changed resources manually, which was deployed through terraform. what will happen? how to update terraform? 
- update the terraform config file as per manual changes
- terraform refresh

what are Modules? Types of modules in terraform?
 Terraform modules are reusable and encapsulated collections of Terraform configurations. They simplify managing resources, making your Terraform code more manageable and scalable.
  1. Root Module: Main module
  2. Child Module: Called by another module like root 
  3. Published Modules: Terraform registry

how to export data from one module to another module?
  - you can export data from one module to another module using module outputs.
  
what is # terraform init -reconfigure
  If you want to change the backend of your statefile 
what is a state file in Terraform?
 - To store information about the resources it has created and their current configuration. (terraform.tfstate)

what is a state-lock mechanism in terraform?
 - It ensures that only one operation can modify the infrastructure at any given time
 - The state-lock mechanism involves acquiring and releasing locks to coordinate access to the Terraform state.

what do you understand about data_source? 
what is external-data-block in terraform?
null resources in terraform? trigger
 - Terraform null_resource does not have a state which means it will be executed as soon as you run "terraform apply" command but no state will be saved.
 - The trigger is a block inside the null_resource which holds key-value pair.
 
if a state file is deleted how to recover it?
what is a dynamic value at run time in terraform?
How to pass parameters in terraform? 
 - use variables

How to share data b/w 2 modules or 2 remote state files. (terraform_remote_state)
 vpc.tf

![image](https://github.com/azizkhanp/interview-questions/assets/26810752/e6822a48-39b9-45c1-9342-34c4f410a0a9)

Ec2.tf
![image](https://github.com/azizkhanp/interview-questions/assets/26810752/47ec2636-b556-4dd1-9bc1-e364bb49dcf7)

