# interview-questions
# linux:
1. How to set a username and password to never expires  chage -M -1 username
2. to list, all the files opened by a particular PID lsof -p PID
3. we are unable to unmount the file system. What are the reasons behind it
#ur in the same dir
#some users are using files in dir
#some files are open in dir
4. what could be the reason if the server takes more time after reboot?
5. we're trying to create the file under any partition but we're getting a permission denied alert.
what could be the reason? however, no space issue and no permission issue
#may be inode
6. how to check kernel routing table information
#route -n
#netstat -rn
#ip route

7. how to set sticky bit. what is the diff b/w small s and S?
#chmod o+t file/dir
s-setuid and executable
S-setuid and non-executable

8. which file is used to specify the default gateway?
#/etc/sysconfig/network

9. in RHEL-7, how to switch b/w two runlevels
#systemctl isolate runlevel3.target
#systemctl set-default multi-user.target
#systemctl get-default

10. what is NFS? How to configure, ports
2049
11. nice value? How to set it?
#nice value is the priority of a process -20 to 19
#nice -n 5 cmd

13. how will u rollback the packages after patching
#yum history
#yum history info 8
#yum history undo 8

14. How to convert ext3 file system to ext4 without any data loss
#umount /dev/sda5
#tune2fs -O extents,uninit_bg,dir_index /dev/sda5
#fsck -pf /dev/sda5
#e2fsck -f /dev/sda5
#mount -t ext4 /dev/sda5 /new

1. Diff b/w bash and dash
2.Diff b/w hardlink and softlink
3. what is daemons? 
it is a process run in BG without user interaction.
many daemons are config to start automatically when the sys is boots up and continuesly running in BG until the sys is shutdown.
ex: cron,sshd
4. Daily tasks in linux
--> user management,LVM , package management, OS patch
5. architecture of linux
H/w --> kernel --> shell --> utilities

6. if yum update is not pulling lib, how do you resolve issue? 
Check Yum Repositories: yum repolist
Clean Yum Cache: yum clean all / yum pdate
Check for Package Availability: yum search <pac_name>
Check for Package Dependencies: yum deplist <pack_name>
Examine Yum Logs: less /var/log/yum.log
Check with central repo team

7. swap space
8. grep cmnd usage
9. password policy agent in linux
PAM --> Check password quality, reusing the same passwords, password aging, /etc/pam.d/ directory. 


awk -F : '{ if ($<position_in_line_to_check> ~ <content_to_search>) print $<position_in_line>}' <File_Name>
sed 's/aziz/Khan/g' <filename>    # it will search file aziz word in file and replace it with Khan and display output on terminal

sed -i 's/aziz/Khan/g' <filename> # it will save changes in file

#it will replace aziz with Khan in 2&3 lines
sed '2,3 s/aziz/Khan' <filename>

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
  When the order in which pods are deployed and started matters, StatefulSets are a good choice. This is crucial for applications where one instance depends on the availability of another.

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

# AWS
1.Route53 type
public hosted zone -- traffic is routed on the internet
private hosted zone -- traffic is routed within an aws vpc


1.Grafana alert rule
2.how do u config grafana alert
3.how to combin promotehus and grafana(loki)
4.how to send logs to grafana (source of logs)




# Some more topics – just for your reference only – Good to know below topics before interview

Do you have experience in any other CA tools like Jenkins besides GitHub actions?   
How can you instruct your pipeline to schedule a job on a specific node that has J D K 70, when it is only available on one node out of ten?   
Which tool do you use to build Java projects?   
Where can we find the second XML file?   
Where will you store your credentials? Username and password for Jenkins, Docker registry, etc.?   
Where will you store your secret information in GitHub actions?   
Where will you attach that role in GI actions?   
Is it possible to store your secrets in the GitHub actions itself?
How do you write custom actions and integrate them into your pipeline?  
Does customer action support GitHub?   
Do you have experience in configuration management tools like Ansible?   
Do you need to install anything during the provisioning process using Terraform?  
Are you deploying in Kubernetes or in EC2?   
Do you have any knowledge of how Jinja templates work?   
How do you execute the command to install the next?   
How would you rate your Terraform skills on a scale of one to five?   
Can you give me an example? Why do we need user data?   
How do you refer to the captured output in the Terraform resource?   
How do you refer to the value of the secret that was captured in the resource block below?
What is the difference between local variables and normal variables that are defined in a variable in TensorFlow?   
Create a security group with the security group resource. For example, when you create a security group, how do you refer to the security group ID in the resource called Easy Two ?
How do you call the output of code written in another module into a different module?   
How do you read the map if you use count?   
Have you used any provisioners in Terraform?   
After creating an instance, execute commands on it.
Can you explain how you deploy your workloads using EKS and GKE?   
Have you used a WSS load balance controller?   
How do you restart your deployment?   
Where do you store secrets in Kubernetes?   
What is the advantage of using ASVPCI in this case?   
Have you used autoscaling groups in AWS?   
How do you get the top 10 lines of your file?   
How do you access the live logs of your file, such as TOCA log or Apache do log, to see exactly what is being recorded in the file?   
