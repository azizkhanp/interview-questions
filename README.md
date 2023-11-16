# interview-questions
# linux:
How to set a username and password to never expires
#chage -M -1 username

to list,all the files opened by particular PID
#lsof -p PID

we are unable to unmount the file system.what are the reason behind it
#ur in the same dir
#some users are using files in dir
#some files are open in dir

what could be the reason if server take more time after reboot

we're trying to create the file under any partition but we're getting permission denied alert.
what could be the reason?however no space issue and no permission issue
#may be inode

how to check kernel routing table information
#route -n
#netstat -rn
#ip route

how to set sticky bit.
what is the diff b/w small s and S?
#chmod o+t file/dir

s-setuid and executable
S-setuid and non-executable

which file is used to specify default gateway?
#/etc/sysconfig/network

in RHEL-7, how to switch b/w two runlevels
#systemctl isolate runlevel3.target
#systemctl set-default multi-user.target
#systemctl get-default

what is NFS? how to configure,ports
2049

nice value?how to set it?
#nice value is the priority of a process -20 to 19
#nice -n 5 cmd

how will u rollback the packages after patching
#yum history
#yum history info 8
#yum history undo 8


How to convert ext3 file system to ext4 without any data loss
#umount /dev/sda5

#tune2fs -O extents,uninit_bg,dir_index /dev/sda5
#fsck -pf /dev/sda5
#e2fsck -f /dev/sda5

#mount -t ext4 /dev/sda5 /new


awk -F : '{ if ($<position_in_line_to_check> ~ <content_to_search>) print $<position_in_line>}' <File_Name>
sed 's/aziz/Khan/g' <filename>    # it will search file aziz word in file and replace it with Khan and display output on terminal

sed -i 's/aziz/Khan/g' <filename> # it will save changes in file

#it will replace aziz with Khan in 2&3 lines
sed '2,3 s/aziz/Khan' <filename>

1.Diff b/w bash and dash
2.Diff b/w hardlink and softlink
3.what is daemons
it is a process run in BG without user interaction.
many daemons are config to start automatically when the sys is boots up and continuesly running in BG until the sys is shutdown.
ex: cron,sshd
4. Daily tasks in linux
--> user management,LVM
5. architecture of linux
H/w --> kernel --> shell --> utilities
6.if yum update is not pulling lib, how do you reslove issue.
7.swap space
8.root kit infection
9.parallel ports
10.grep cmnd usage
11.password policy agent in linux

# AWS
1.Route53 type
public hosted zone -- traffic is routed on the internet
private hosted zone -- traffic is routed within an aws vpc


1.Grafana alert rule
2.how do u config grafana alert
3.how to combin promotehus and grafana(loki)
4.how to send logs to grafana (source of logs)




