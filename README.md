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
2. Diff su and su -
    su <user-name>: it will switch to the user but It doesn't change the user's home directory or bring in the user's environment settings.
    su - <user-name>: it set home dir and env setting for user
    visudo or /ect/sudoers (user    MACHINE=COMMANDS)
3. How to run CMD or Script in the background?
    nohup cmd/script &  (no hang up)
    nohup COMMAND [ARGUMENTS] > output.log 2>&1 &

4. umask and ulimit 
    https://foxyknight29.medium.com/umask-and-ulimit-in-linux-45f2c5ae1279
5. to list, all the files opened by a particular PID #lsof -p PID
6. ls -l | grep -v^a  (it will show all files except letters starting with a)
7. how to find all empty files or dir and delete them?
    #find /var/tmp -type f -empty -delete  (Dry run  find /path/to/search -type f -empty)
     find /var/tmp -type d -empty -delete  
8. How to redirect the error of command into a file?
       to redirect errors we need to use 2>
       to redirect errors and output use 2>&1
9.  How to check the user list in a particular group 
     cat /etc/group | grep <Group-name>
10. we are unable to unmount the file system. What are the reasons behind it
#ur in the same dir
#some users are using files in dir
#some files are open in dir (lsof +D /path/to/your/directory)

11. what could be the reason if the server takes more time after reboot?
   Hardware issue / Service start delay / N/W issue / Filesystem checks / Resources issue
12. we're trying to create the file under any partition but we're getting a permission denied alert.
what could be the reason? however, no space issue and no permission issue
#may be inode
13. how to check kernel routing table information
#route -n
#netstat -rn
#ip route

14. how to set sticky bit. what is the diff b/w small s and S?
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
#nice value is the priority of a process -20 to 19 , lower the number high priority 
#nice -n 5 cmd

14. how to change the nice value of of process with ID 2264,
 The values typically range from -20 to 19, where -20 is the highest priority and 19 is the lowest.
 Only the superuser can assign negative values

  To start a process with a lower priority
  #nice -n 10 <cmd>

  If you’ve already started a process and want to change its priority
  #renice 10 -p process_id



15. how will u rollback the packages after patching
#yum history
#yum history info 8
#yum history undo 8

16. Diff b/w yum update vs yum upgrade?
    The yum update command is used to update all packages on the system to their latest versions, including kernel packages.
    If a new kernel version is available, yum update will install it, but it won't remove the old kernel.

   It performs the same tasks as yum update but may also remove packages that are no longer needed due to changes in dependencies or obsolescence.

16. How to convert ext3 file system to ext4 without any data loss
#umount /dev/sda5
#tune2fs -O extents,uninit_bg,dir_index /dev/sda5
#fsck -pf /dev/sda5
#e2fsck -f /dev/sda5
#mount -t ext4 /dev/sda5 /new

17. what is a Linux kernel? Can we edit it?
18. what are system utilities?
19. what are system libraries?
20. Diff b/w unix vs Linux?
21. what is heap memory(heap space)?
22. swap space?
23. linux loader(LILO)?
24. Diff b/w cron vs ana-cron?
25. user account locked?
    Account Expired:/Account Password Expired: chage -l username
    Password locked : passwd -l username or /etc/shadow ! , passwd -S username , passwd -u username
    User lock: usermod --lock username , usermod --unlock username
    Failed Login Attempts: /etc/security/faillock.conf
    Account is Expired Due to Inactivity: /etc/default/useradd
    logs: grep username /var/log/auth.log

26. what is ACL in Linux?
27. SELinux: https://www.freecodecamp.org/news/securing-linux-servers-with-se-linux/
28. Linux System Hardening
-> Enable Strong Authentication like strong password policies and use MFA
-> Create an SSH keys
-> Keep the system up to date like regular patching
-> Install only necessary software
-> Disable Unnecessary Services
-> Disable root login
-> Use Secure remote logins
-> Give the least Privilege to user accounts
-> Filesystem security like permissions to files/dir
-> Enable SELINUX
-> Enable firewall rules like open necessary ports

30. How do you get the top 10 lines of your file?   
     head -n 10 <FN>
31. How do you access the live logs of your file, such as TOCA log or Apache do log, to see exactly what is being recorded in the file?  
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
6. Booting process
   BIOS --> MBR --> GRUB -->  kernel/initramfs --> init level -->user space initialization --> login prompt --> user interaction

7. if yum update is not pulling lib, how do you resolve the issue? 
Check Yum Repositories: yum repolist
Clean Yum Cache: yum clean all / yum update
Check for Package Availability: yum search <pac_name>
Check for Package Dependencies: yum deplist <pack_name>
Examine Yum Logs: less /var/log/yum.log
Check with the central repo team


9. swap space
10.  Diff b/w yum vs rpm 
     RPM: individual .rpm packages / not resolve dependencies automatically / You must manually install all required dependencies / location depends
     YUM: Automatically resolves dependencies / Fetches packages and dependencies from online or configured repos / no location req
11. paging in linux
12. DNS:53, SSH:22, FTP:21, DHCP:67,68, Squid:3128, HTTP:80, HTTPS:443, SMTP:25
13. grep & egrep cmnd usage 
14. password policy agent in linux
PAM --> Check password quality, reusing the same passwords, password aging, /etc/pam.d/ directory.

15. user not able to log in remote server(SSH)?
-ssh is running
-Check port of SSH
-User has permission to login to server
-Publickey authentication/ authorizeskeys

11.how to give permission to a particular user to access a particular file?

- setfacl -m u:<user_name> <filename>

12. how to disable root a/c
usermod -s /sbin/nologin root

13. How to change id of user? /etc/login.def
14. How to set env. variables in linux?
    user level: .bashrc
    global level: cat /etc/bashrc or cat /etc/profile

15. root user not able to delete a file
lsattr <FN>
chattr -i <f_n>
chattr +i <file_name>

16. how to check the top 10 space-consuming files/dir in a particular dir
# du -sh * | sort -rn | head

Cron
minute (0-59), hour (0-23), day of the month (1-31), month (1-12), and day of the week (0-7)

16. How to check when the was package installed on the server
- rpm -q -last <package_name>
- rpm -qf <file_name> # to get package name of filename
- rpm -qa | grep <package_name>  --> to check if package is installed or not 

17. List some of the commonly used shell commands.
ls,cp,mv,mkdir,touch,vim,grep,find,locate,top,sar,df

18. write a simple shell script to list all process
 - ps -ef | awk '{print $2}'  # print all process ids
 - ps -ef | wc -l   # count how many process are running 

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

set -x: De-bugging the commands in a shell script
set +x: To stop debugging
set -e: script exit immediately if any command fails to run
set -u: enforces strict variable usage, if the variable is not set value, the script will exit with an error

what would be the result of each command:
echo $0: Display the current shell-like (bash / sh / csh)
echo $?: Displays the exit status of the last executed command. (0-succeeded / error - non-zero)
echo $$: Displays the process ID (PID) of the current shell.
echo $#: Displays the number of positional parameters (arguments) passed to a script or function.

$@: Treats each positional parameter as a separate word when enclosed in double quotes. Preferred when dealing with arguments that contain spaces or special characters.
$*: Treats all positional parameters as a single word when enclosed in double quotes. The arguments are concatenated with the first character of IFS as the separator.

How do you get input from the user in shell scripts?
Read input: **read** -p "enter a number: " num

Grafana: https://computingforgeeks.com/how-to-install-grafana-on-centos-7/
prometheus: https://blog.fourninecloud.com/what-is-prometheus-and-how-to-install-and-configure-it-on-linux-server-9b5f88685451
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
  - ENTRYPOINT: When you start the Docker container, a command or script called ENTRYPOINT is executed.(only 1 ENTRYPOINT in DockerFile)
  - ENV: to set environment variables 
  - COPY: copying the files/dir to the image 
  - ADD: Downloading any data from URLs 
  - CMD: The main purpose of the CMD command is to start the process inside the container and it can be overridden
             Dockerfile can only have one CMD, 
  - RUN: To run any command
which instruction the docker image will take if we use both ENTRYPOINT and CMD in DockerFile
   - It takes only the last instruction(ENTRYPOINT or CMD) which mentioned in DockerFile

Diff b/w CMD and ENTRYPOINT
https://www.bmc.com/blogs/docker-cmd-vs-entrypoint/#:~:text=They%20both%20specify%20programs%20that,as%20arguments%20of%20the%20command.
  only 1 CMD and ENTRYPOINT in DockerFile
  CMD can be over wirtten using var's but ENTRYPOINT not
  If the Dockerfile has multiple CMD instructions, only the last one will take effect.
  If the Dockerfile has multiple ENTRYPOINT instructions, only the last one will take effect.
  
DockerFile:
 FROM python:3.9
 WORKDIR /app
 RUN pip install -r requirements.txt
 COPY . /app
 ADD packages /app/pacakges
 EXPOSE 8080
 CMD ["python", "app.py"]

 docker build -f DockerFile -t app:1.0.0
 
 
How to mount Dir to the container
   


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
EFS: 
 Can EFS be accessed from multiple AZs?  Yes
 class : stand (frequently accessed data) / IA (Infrequent Access)
S3 storage types (classes) ? 
What happens to my data when EC2 is terminated?
If U check "Delete on termination" then data will be deleted
Why I'm not able to login EC2?

EC2 instance type used in project: 
  web/api --> t3.xlarge
  app(java)--> need more CPU --> m5a.4xlarge
  batch --> we use arm(graviton2-based) to save cost
  DB: use memory based r6 type
  Then spot,RI, we use autoscaling 

**EC2 Launch:**
Name/tag --> AMI(image) --> Instance type --> key pair --> N/W(VPC / subnet / public IP / SG) --> Storage --> Advance settings
Why my Ec2 not pinging?
VPC components: 
  **VPC** : 
  **subnets**:
     IP address range in VPC
     you can create multiple subnets within a VPC, they are associated with different availability zones.
**Security Groups**:
  SG acts as a virtual firewall for your instances. They control inbound and outbound traffic based on user-defined rules.
  **Route table**:
     It controls traffic b/w subnets within VPC and the internet.
     Each subnet must be associated with an RT that specifies the routing rules.
 ** Internet Gateway** :
      Virtual router that connects a VPC to the internet
  **NAT gateway**: (N/W Add Translation)
     It provides internet access for private instances without exposing their IP add to the public
 
 **Network ACL**:
    They are subnet-level firewalls that control inbound and outbound traffic at the subnet level.
**vpc peering** : 
      VPC Peering is a networking connection between two Virtual Private Clouds (VPCs) that allows them to communicate with each other privately using private IP addresses
**transit gateway** : 
    Connect multiple VPCs and on-premises networks through a single central gateway.

inline policy: 
   Inline policies are directly attached to a specific user, group, or role.
Managed Policy: Can be attached to multiple entities

 VPC Endpoint in AWS allows you to privately connect your VPC to supported AWS services and VPC endpoint services without going through the public internet
If your EC2 instance is in a private subnet (no Internet Gateway/NAT Gateway) and you want it to access S3, the best and secure way is to use a VPC Gateway Endpoint for S3.
private-link vs vpc-endpoint: 

ALB vs NLB 
  
      

Diff b/w NAT gateway vs NAT instance
https://medium.com/@smt.dubey/aws-nat-gateway-nat-instance-8e31972df1cf

Autoscaling types:  Manual/Dynamic/Scheduled Scaling
https://www.developer.com/web-services/aws-auto-scaling-types-best-practices/

AWS --> VPC --> subnet --> SG --> CIDR --> Route table , IAM
Patching, monitoring,
vpc peering: https://medium.com/@vishal.sharma./create-an-aws-vpc-peering-connection-47ce518de870 

Azure --> vNET --> subnets --> NSG / ASG --> CIDR
For example, you might have a VNet that contains multiple subnets, each hosting different types of resources. You can use NSGs to control the traffic between these subnets and from the internet. ASGs can be used to group VMs with similar roles, making it easier to manage and update security rules.

1.Route53 type: https://gauravguptacloud.medium.com/aws-route53-records-routing-policies-f3657b01ffa2
public hosted zone -- traffic is routed on the internet
private hosted zone -- traffic is routed within an aws vpc
Latency-based routing in AWS Route53
How AWS N/W firewall protect VPC?
Stateful vs State-less firewall in AWS?
When do we use spot or on-demand EC2?
what is ECS? cluster? EC2 vs Fragent?

**Lambda**
1.Lambda function that runs every 24 hours, checks for untagged AWS resources, and sends an email to your team distribution list via Amazon SES.

2.Created Lambda functions(python) to create a ebs volume snapshot with event bridge / same for delete the ebs snapshot after 7 days 

3.created lambda function to detects the manual changes in aws resources(created by terraform)-- who changed/which resource/time stamp

    1.CloudTrail – enabled to log all API activity across the AWS account.
    2.CloudWatch EventBridge Rule – monitors for specific Write API calls (like ModifyInstanceAttribute, PutBucketPolicy, CreateUser, etc.) by IAM users.
    3.Lambda Function – triggered by EventBridge when such changes occur.

lambda limitations: https://awsfundamentals.com/blog/lambda-limitations 
lambda layers: https://medium.com/@gowthamshankar09/an-overview-of-aws-lambda-layers-8cf04948e1c4 


1.Grafana alert rule
2.how do u config grafana alert
3.how to combin promotehus and grafana(loki)
4.how to send logs to grafana (source of logs)




#############################################################################################################################################################

# Devops
What is Tech stack using in your DevOps project?
Explain the complete CICD process that has been followed in your project.
what is the flow of your CICD or Steps in Jenkins build?
1.git checkout
2.gitguardian secret scan in code
3. SAST - SonarQube scan(Static Application Security Testing )
4. maven build
5. Junit test
6. Docker image build
7. Docker image scan using JFROG Xray
8. Push Docker image to JFROG 
9. DAST - ZAP(Dynamic Application Security Testing)
10. Deploy to EKS using ArgoCD

How can you instruct your pipeline to schedule a job on a specific node that has JDK 7.0, when it is only available on one node out of ten? 
What are Executors in Jenkins?
  An Executor is just a slot in which to run a job on an agent/node. An agent can have zero or more executors. The number of executors per Agent defines how many concurrent jobs can be run to that agent.
what is a multi-branch pipeline
How do you secure the Jenkins server?
-->Use HTTPS and SSL
-->Configure user authentication and authorization
-->Manage and protect your credentials
-->Update and audit your plugins
-->Harden your server

how to pass parameters in Jenkins pipeline
what is trigger in Jenkins
If your CICD was aborted by you due to it continuously running bez of a parameter issue? when u run again same CICD pipeline what will happen? State-lock file.
Which tool do you use to build Java projects? 
Where will you store your credentials? Username and password for Jenkins, Docker registry, etc.?   
How do you write custom actions and integrate them into your pipeline? 
What is sonarqube? why your using it?
sonarqube : 
what is debt sonarqube
Technical debt: The estimated time required to fix all Maintainability Issues/code smells

what is code smells sonarqube
they indicate weaknesses in design that may be slowing down development or increasing the risk of bugs or failures in the future

what is code coverage sonarqube
is a measure of how much of the application’s code has been run in testing

what is duplications sonarqube
detection feature that scans the codebase to identify duplicate or highly similar code fragments 


Git branch Strategies?  
Main
Develop
Feature
Release
Hotfix

How do discard changes in working dir?
#git checkout -- <file_name>
#git checkout -- . 

we have 50 commits in DEVELOP branch out of which only 5 commits need to be pushed in RELEASE branch.
--> Use git cherry-pick
#git cherry-pick <commitsha>

Developer has developed an app module in local with 100 commits, but now he wants to push all his changes in remote DEVELOP branch as a single commit?
# git rebase -i HEAD~3 (last 3 commits)
what is git stash? 
  when you want to switch b/w branches but not to commit the code, then we can use git stash to temp save the code
  Git stash command takes your uncommitted changes and saves them away for later use
#git stash
#git stash list
#git stash pop <stash_name/ID>

Do you have experience in configuration management tools like Ansible?   
Ansible playbook error checks 
  ansible-playbook your_playbook.yml --check: Dry run of playbook, what will happen when play executed
  ansible-playbook your_playbook.yml --syntax-check:  To check the syntax of playbook 
  ansible-playbook your_playbook.yml --list-hosts: To check the on which hosts playbook will run 
  ansible-playbook your_playbook.yml --list-tasks: To check what are tasks playbook will run

if one task failed in the playbook, how to continue other tasks : ignore_errors: true, ignore_unreachable: true

Ansible role example: 
https://www.devopsschool.com/tutorial/ansible/ansible-roles-explained-with-examples.html#example2

forking and serial executions and Ansible?
https://medium.com/devops-srilanka/difference-between-forks-and-serial-in-ansible-48677ebe3f36

what is import and included in ansible?
what is facts in ansible?
what is delegate_to in ansible?
https://www.middlewareinventory.com/blog/ansible-delegate_to/

Ansible roles, and variable precedence follow a specific order
1. Variables passed to Ansible on the command line using the -e or --extra-vars option override all other variables defined in the playbook
2. When including a role in a playbook, you can pass variables to the role using the vars parameter.
3. Variables defined directly in the playbook, vars sections
4. Variables defined in the role defaults/main.yml file

ansible-playbook on distinctive nodes with diff ports and usernames

update the below details in the inventory file
anisble_port: 
ansible_user:

What are Register targets in Ansible?
  register targets are used to capture the output of tasks or commands and store them in variables.

Diff b/w copy vs fetch in Ansible
 Copy: copy files or directories from the control node to the managed nodes.
 Fetch: fetch files or directories from the managed nodes to the control node.

what is --include in ansible
 to run more than 1 playbook we use --include option

playbook vs Ad-hoc

Quick and easy
automate single task
non-repetitive tasks

multiple tasks
Repetitive
Reusable

How to run only a particular task from a playbook?
use tags to run a particular task : ansible-playbook --tags tag1 playbook.yaml





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


 Ansible:
Handlers: https://medium.com/cloudnloud/how-to-use-handlers-in-ansible-9e62e17c3b61
Patching: https://medium.com/@sangeetv09/linux-os-patching-using-ansible-playbook-0927e7e92630
Scenario: https://medium.com/@sushantkapare1717/ansible-senario-based-questions-part-ii-8c5413ec335c

