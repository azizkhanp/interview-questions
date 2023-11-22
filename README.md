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

**#k8s**

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
