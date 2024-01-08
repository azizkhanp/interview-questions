# interview-questions

# vMware:
what is vSAN
vSAN types and version
VRA,VROPS versions your using
what you do in VRA
what you do in VROPS
have you created a dashboard in vROPS
what are nodes in vROPS
how you check performance metrics in vROPS
what you do in login site
if PSU's are down what will impact on vCenters
what are services running on vCenter server
  service-control --status 
how to restart services from vCenter cli
   service-control --start --all
how to patch vCenter appliance
vCenter patch you faced
how to upgrade vCenter 6.5 to 7.0 (pre-checks, process,post-checks)
vCenter upgrade issues you faced
how to upgrade UCSFI
what types of service profiles you using (how many types do we have)
what are H/W vendors using
how to replace H/W on the server (pre-checks and post-checks)
Esxi patch (pre-checks, process,post-checks)
Esxi patch you faced
what are the remediation of Esxi(steps)
Esxi went to a not-responding state (why? How did you resolve)
how to create new Datastores
DS filesystem upgrade vmfs5 to vmfs6
how to add RDS disk to VM
have you faced Datastores issue(VM's RO state,VM's disconnected)
how to deploy OVA/OVF vms from vCenter
vMotion (pre-checks, process, post-checks)
  CPU compatibility
  vMotion interface (minimum 1 Gb adapter)
  Shared storage
  Same naming for virtual port groups
  VMkernel port group with vMotion enabled
  Sufficient resources on the target host
  At least one vSphere Essentials Plus license on the Corresponding ESX host

FT how it works (Fault-Tolerance)
https://www.techtarget.com/searchitchannel/feature/VSphere-Fault-Tolerance-requirements-and-FT-logging#:~:text=Fault%20Tolerance%20(FT),-Fault%20Tolerance%20(FT&text=FT%20takes%20that%20to%20the,created%20on%20another%20functional%20host.

FT is applicable on VM level, 
FT takes that to the next level and guarantees that the VM stays operational during a host failure by keeping a secondary copy of it running on another host server; in case of a host failure, that VM then becomes the primary VM and a new secondary is created on another functional host.
The primary VM and secondary VM stay in sync with each other by using a technology called Record/Replay

DRS how it works (Distributed Resource Scheduler)


HA how it works (BG of HA),fdm agents
https://cloudpathshalacom.wordpress.com/2018/09/01/how-vmware-ha-works-deep-dive/

Affinity,anti-affinity rules
new Esxi installtion process
how to create vmware case
how to inform notifications to customers on P1/P2 issues
recently faced P1/P2 issue
in the last 6 months what you learned new things
what is vmkernel adpters
what is a standard, distributed switch in vmware
what is VLAN, how it works
have you deployed new vCenter/VRA
what are the files of vm
what are files of snapshot 
  https://www.parallels.com/blogs/ras/vm-snapshot/
why I try to extend disk not-able Y?
how to remove and add vm from inventory
what type of authentication you using to log into vCenter
what are vmtools, uses
what is hostd,vpxa,vpxd service, how they work
knowledge on windows OS
OS patch of VM 

#################################################################################################################################################################

# linux:
1. How to set a username and password to never expire  #chage -M -1 username
2. umask and ulimit 
    https://foxyknight29.medium.com/umask-and-ulimit-in-linux-45f2c5ae1279
3. to list, all the files opened by a particular PID #lsof -p PID
4.  How to check the user list in a particular group 
     cat /etc/group | grep <Group-name>
5. we are unable to unmount the file system. What are the reasons behind it
#ur in the same dir
#some users are using files in dir
#some files are open in dir (lsof +D /path/to/your/directory)

6. what could be the reason if the server takes more time after reboot?
   Hardware issue / Service start delay / N/W issue / Filesystem checks / Resources issue
7. we're trying to create the file under any partition but we're getting a permission denied alert.
what could be the reason? however, no space issue and no permission issue
#may be inode
8. how to check kernel routing table information
#route -n
#netstat -rn
#ip route

9. how to set sticky bit. what is the diff b/w small s and S?
Only applicable to Dir

#chmod o+t dir
s-setuid and executable
S-setuid and non-executable

8. Setuid/Setgid Special Permissions
  Applicable to files/Dir
  chmod u+s file/dir 
  chmode g+s file/dir


9. which file is used to specify the default gateway?
#/etc/sysconfig/network

10. in RHEL-7, how to switch b/w two run levels
#systemctl isolate runlevel3.target
#systemctl set-default multi-user.target
#systemctl get-default

11. Run Levels
   init0 -- power off
   init1 -- single-user mode
   init2 -- Multiple user mode with no N/W.
   init3 -- Multiple user modes under the command line interface and N/W.
   init4 -- User-definable.
   init5 -- Multiple user mode under GUI (graphical user interface) and this is the standard runlevel for most of the LINUX-based systems.
   init6 -- Reboot/restart

12. what is NFS? How to configure, ports
2049
13. nice value? How to set it?
#nice value is the priority of a process -20 to 19
#nice -n 5 cmd

14. how will u rollback the packages after patching
#yum history
#yum history info 8
#yum history undo 8

15. How to convert ext3 file system to ext4 without any data loss
#umount /dev/sda5
#tune2fs -O extents,uninit_bg,dir_index /dev/sda5
#fsck -pf /dev/sda5
#e2fsck -f /dev/sda5
#mount -t ext4 /dev/sda5 /new

16. what is a Linux kernel? Can we edit it?
17. what are system utilities?
18. what are system libraries?
19. Diff b/w unix vs Linux?
20. what is heap memory(heap space)?
21. swap space?
22. linux loader(LILO)?
24. Diff b/w cron vs ana-cron?
25. user account locked?
    Account Expired:/Account Password Expired: chage -l username
    Password locked : passwd -l username or /etc/shadow ! , passwd -S username , passwd -u username
    User lock: usermod --lock username , usermod --unlock username
    Failed Login Attempts: /etc/security/faillock.conf
    Account is Expired Due to Inactivity: /etc/default/useradd
    logs: grep username /var/log/auth.log

26. what is ACL in Linux?
27. How do you get the top 10 lines of your file?   
     head -n 10 <FN>
28. How do you access the live logs of your file, such as TOCA log or Apache do log, to see exactly what is being recorded in the file?  
     tail -f <FN>

1. Diff b/w bash and dash
2.Diff b/w hardlink and softlink
3. what are daemons? 
it is a process run in BG without user interaction.
many daemons are configured to start automatically when the sys boots up and continuously running in BG until the sys is shut down.
ex: cron,sshd
4. Daily tasks in Linux
--> user management, LVM, package management, OS patch
5. architecture of Linux
H/w --> kernel --> shell --> utilities

6. if yum update is not pulling lib, how do you resolve the issue? 
Check Yum Repositories: yum repolist
Clean Yum Cache: yum clean all / yum update
Check for Package Availability: yum search <pac_name>
Check for Package Dependencies: yum deplist <pack_name>
Examine Yum Logs: less /var/log/yum.log
Check with the central repo team

7. swap space
8. grep cmnd usage
9. password policy agent in linux
PAM --> Check password quality, reusing the same passwords, password aging, /etc/pam.d/ directory.

10. user not able to log in remote server(SSH)?
-ssh is running
-Check port of SSH
-User has permission to login to server
-Publickey authentication/ authorizeskeys

11.how to give permission to a particular user to access a particular file?

- setfacl -m u:<user_name> <filename>

12. how to disable root a/c
usermod -s /sbin/nologin root

13. How to change id of user? /etc/login.def

14. root user not able to delete a file
lsattr <FN>
chattr -i <f_n>
chattr +i <file_name>

15. how to check the top 10 space-consuming files/dir in a particular dir
# du -sh * | sort -rn | head

16. How to check when the was package installed on the server
- rpm -q -last <package_name>
- rpm -qf <file_name> # to get package name of filename

17. List some of the commonly used shell commands.
ls,cp,mv,mkdir,touch,vim,grep,find,locate,top,sar,df

18. write a simple shell script to list all process
 - ps -ef | awk -F " "'{print $2}'

 19. write a script to print only errors from a remote log
      curl <remote_server_name/ip> | grep -i error  

 20. How to open a file in read-only mode?
    - vim -r <FN>
21. Diff b/w break and continue statements

22. How will u sort the list of names in a file
    sort <FN>

23. How will u manage logs of a system that generates huge log files every day?
--> logrotate


awk -F : '{ if ($<position_in_line_to_check> ~ <content_to_search>) print $<position_in_line>}' <File_Name>
sed 's/aziz/Khan/g' <filename>    # it will search file aziz word in file and replace it with Khan and display output on the terminal

sed -i 's/aziz/Khan/g' <filename> # it will save changes in file

#it will replace aziz with Khan in 2&3 lines
sed '2,3 s/aziz/Khan' <filename>

##########################################################################################################################################################
Docker Architecture
  1. Client: Build, Pull, Run
  2. Docker Host: 
           a.Docker daemon: It manages docker objects such as images, containers, networks, and volumes with the help of the API requests of Docker.
           b.container: Containers are created from docker images as they are ready applications.
           c.Images: An image contains instructions for creating a docker container. It is just a read-only template.
  3. Registry: All the docker images are stored in the docker registry (Public or private)

How to edit the docker image? (example: my-img)
 - first, we need to run a container (# docker run -dt my-img)
 -  login to the container (docker exec -it <container_ID> bash)
 -  make changes to what you need for new image like create some Dir or install some packages
 -  Then commit changes (docker commit <conatiner_ID> new-image-name)

DockerFile
  - FROM: base image
  - WORKDIR: To set the working dir
  - EXPOSE: to expose any ports
  - ENTRYPOINT: When you start the Docker container, a command or script called ENTRYPOINT is executed.
  - ENV: to set environment variables 
  - COPY: copying the files/dir to the image 
  - ADD: Downloading any data from URLs 
  - CMD: The main purpose of the CMD command is to start the process inside the container and it can be overridden
             Dockerfile can only have one CMD, 
  - RUN: To run any command
which instruction the docker image will take if we use both ENTRYPOINT and CMD in DockerFile
   - It takes only the last instruction(ENTRYPOINT or CMD) which mentioned in DockerFile
How to mount Dir to the container
   

# k8s
1. k8s pod vs docker container
  container is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools.
  Designed for packaging and running a single application or service.

  A Pod is the smallest deployable unit in Kubernetes and represents a single instance of a running process in a cluster. 
  It can contain one or more containers that are tightly coupled and share the same network namespace, storage, and other resources.
  Designed for deploying and managing groups of containers that need to work together.
2. what is the init container? when it runs? why do we use them? 
   initialization tasks that need to be completed before the application containers start. Once all init containers have completed their task successfully, the main application containers are started.
   Init containers share the same volume as the main application containers. 
   Once an init container completes its task, it terminates
  use-cases: 
    Downloading application dependencies, setting up configuration files, or performing database schema migrations.
    Waiting for a database to be ready or waiting for a service to become available.
    
3. what is a stateful set? when we choose it? 
   StatefulSets are designed to provide guarantees about the ordering and uniqueness of pods, making them suitable for applications that require stable network identifiers, persistent storage, and ordered deployment and scaling.
  Use StatefulSets when deploying stateful applications that require unique identifiers, stable network identities, and persistent storage. Examples include databases (like MySQL, PostgreSQL), messaging queues, and other applications that manage state.
  When the order in which pods are deployed and started matters, StatefulSets is a good choice. This is crucial for applications where one instance depends on the availability of another.

4. Diff b/w config maps and secrets? 
   ConfigMaps: Store data in key-value pairs. The values can be strings or files. 
    Designed for storing non-sensitive configuration data such as environment variables, configuration files
   Secrets: Store data in key-value pairs similar to ConfigMaps, but the data is treated as base64-encoded.
    Designed for storing sensitive information such as passwords, API tokens, or encryption keys.
5. Deployment strategies? Diff b/w rolling updates vs blue-green vs canary?
  Rolling Updates: updating 1 pod at a time to the new version.  It minimizes downtime by gradually shifting traffic to the updated pods. It consumes a lot of time to complete the upgrade.
  Blue-Green Deployments: maintaining two separate environments (Blue and Green), with one active at a time. The deployment consists of switching traffic from the current active environment (Blue) to the new version (Green).
  Canary Deployments: This involves releasing a new version of the application to a subset of users or instances before a full release. conditional routing to control which users receive the new version.
6. How to set up RBAC(Role-based access control)  for a user or service account? 
    Deploy below with manifest files.
   a. Create a Service Account: service account name
   b. Create a Role: what resources, permission like get, list, create, delete
   c. Bind the Role to the Service Account: attach Role to SA
   d. Deploy pod/deployments using a service account

7. multi-tendency k8s cluster? 
   A multi-tenancy Kubernetes cluster is a cluster that is shared by multiple tenants or user groups, each running their own workloads and applications.
    Namespace Isolation:Each tenant can have its own namespace, and resources within a namespace are isolated from other namespaces.
    RBAC: Implement RBAC to control and restrict access to resources within each namespace.
    Resource Quotas and Limits:Set up resource quotas and limits at the namespace level to prevent resource hogging and ensure fair allocation of resources among tenants.
8. Horizontal pod scaling? 
   In Kubernetes, you can use the Horizontal Pod Autoscaler (HPA) to automatically adjust the number of pods in a deployment or replica set based on observed metrics. Common metrics include CPU utilization and custom metrics.

9. How do you restart your deployment?
   kubectl rollout restart deployment <deployment-name>

10. Liveness and readiness in k8s?
     The liveness probe is used to determine if a container is alive or not. If a container fails its liveness probe, Kubernetes will restart the container.
      Like: checking whether a specific endpoint in the application is responsive or if the application process is running.
     The readiness probe is used to determine if a container is ready to serve traffic. 
      This is particularly useful during deployments or when an application needs time to initialize before accepting traffic.

11. Kubectl describe vs kubectl logs ?
12. Where do you store secrets in Kubernetes?
13. Error codes or diff status codes in k8s and also how do u debug or find what's the issue?
CreateContainerConfigError: 
Pending: insufficient resources(namespace limits, pod limits), if affinity rule not match, pv storage
OOMKilled: if the container or pod exceeds its memory limit, k8s terminate the container
CrashLoopBackOff: config error, resource constraints, dependency issues, app error
Running(but status id 0/1): issue with liveness or readiness probe

##############################################################################################################################################################
# AWS

How many AWS accounts do you have in the project? 
  3 Accounts || Prod(Infra and Devops teams) >> Stage (Testing and QA team) >> Dev (Developers)
What if ELB goes down and solution?
 max ELB doesn't go down bcz it AWS managed service
 pre-warming with AWS support if your traffic is high to hit LB (They will provide good hardware) 
Can I mount single EBS volumes to multiple EC2? NO
Can I mount multiple EBS volumes to a single EC2? Yes
How many EBS volumes can we attach to a single EC2? 24
What happens to my data when EC2 is terminated?
If U check "Delete on termination" then data will be deleted
Why I'm not able to login EC2?
Why my Ec2 not pinging?
VPC components: 
  vpc : 
  subnets:
     IP address range in VPC
     you can create multiple subnets within a VPC, they are associated with different availability zones.
  route table:
     It controls traffic b/w subnets within VPC and the internet.
     Each subnet must be associated with an RT that specifies the routing rules.
  Internet Gateway:
      Virtual router that connects a VPC to the internet
  NAT gateway: (N/W Add Translation)
     It provides internet access for private instances without exposing their IP add to the public
 Security Groups:
  SG acts as a virtual firewall for your instances. They control inbound and outbound traffic based on user-defined rules.
 Network ACL:
    They are subnet-level firewalls that control inbound and outbound traffic at the subnet level.    

1.Route53 type
public hosted zone -- traffic is routed on the internet
private hosted zone -- traffic is routed within an aws vpc
Latency-based routing in AWS Route53
How AWS N/W firewall protect VPC?
Stateful vs State-less firewall in AWS?
When do we use spot or on-demand EC2?
what is ECS? cluster? EC2 vs Fragent?




1.Grafana alert rule
2.how do u config grafana alert
3.how to combin promotehus and grafana(loki)
4.how to send logs to grafana (source of logs)




#############################################################################################################################################################

# Devops
What is Tech stack using in your DevOps project?
Explain the complete CICD process that has been followed in your project.
what is the flow of your CICD or Steps in Jenkins build?
How can you instruct your pipeline to schedule a job on a specific node that has JDK 7.0, when it is only available on one node out of ten? 
What are Executors in Jenkins?
  An Executor is just a slot in which to run a job on an agent/node. An agent can have zero or more executors. The number of executors per Agent defines how many concurrent jobs can be run to that agent.
what is a multi-branch pipeline
how to pass parameters in Jenkins pipeline
what is trigger in Jenkins
If your CICD was aborted by you due to it continuously running bez of a parameter issue? when u run again same CICD pipeline what will happen? State-lock file.
Which tool do you use to build Java projects? 
Where will you store your credentials? Username and password for Jenkins, Docker registry, etc.?   
How do you write custom actions and integrate them into your pipeline? 
What is sonarqube? why your using it?
What is code coverage in sonar qube?
Git branch Strategies?  
Do you have experience in configuration management tools like Ansible?   

How to find drift detection 
  1. terraform refresh  or  cronjob - terraform refresh
  2. Create a strict Rule if any IAM user wants to change any resources in AWS manually he/she needs to get approval from a manager
  3. Audit log - Create a Lambda function to send alerts to the team if there is any change for resources managed by Terraform 
       (Like who changed resources IAM user name and timestamp ..)

I have created resources using Terraform and deleted some resources manually how to update statefile as per deleted resources
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




Are you deploying in Kubernetes or in EC2?     
How do you execute the command to install the next?   
Can you give me an example? Why do we need user data?   
How do you refer to the captured output in the Terraform resource?   
How do you refer to the value of the secret that was captured in the resource block below?
What is the difference between local variables and normal variables in terraform?   
Create a security group with the security group resource. For example, when you create a security group, how do you refer to the security group ID in the resource called Easy Two ?
How do you call the output of code written in another module into a different module?   
How do you read the map if you use count?   
  
After creating an instance, execute commands on it.
Can you explain how you deploy your workloads using EKS and GKE?   
Have you used autoscaling groups in AWS?   
 
