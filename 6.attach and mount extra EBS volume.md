# Increase EBS Volume Size in AWS an existing volume



===========================================================
Step 1: Take Snapshot of EBS Volume (to be Safe).
Step 2: Increase EBS Volume Size in AWS Console in this we simply select the ebs vol and modify to increase the size . 
Step 3: Extend a Linux file system after resizing a volume.


## Command to Extend the file system:
===========================================================
> df -hT 
> The df -h command is used to display disk space usage on a Linux-based system in a human-readable format



## Check whether the volume has a partition:
> sudo lsblk
> The lsblk command is used to list information about block devices on a Linux-based system. It provides a hierarchical view of the storage devices, including disks and partitions, as well as information about their sizes and mount points



## Extend the partition:
sudo growpart /dev/xvda 1


Extend the file system on /:
[XFS file system]: sudo xfs_growfs -d /
[Ext4 file system]: sudo resize2fs /dev/xvda1






# Mounting an extra drive in ec2 running instance


Commands Used: 

df -h

### Lists all the block devices in the Linux Machine:
lsblk 

### Check if there is any file system on new EBS Volume:

file -s /dev/xvdf 

[ /dev/xvdf is the name of the attached drive ]
(If you see "Data", meaning you need to setup file system for this block device.)

Create a file system on volume to mount it to EC2:
mkfs -t xfs /dev/xvdf

Create new directory:
mkdir -p /apps/my-data/apps/volume/new-volume
cd /apps/my-data/

Mount volume to EC2 Instance:
mount /dev/xvdf /apps/my-data/apps/volume/new-volume 





# backup and restore server extending the vol size ! 

Step 1: Take the Snapshot of Server.
Step 2: Create new EBS Volume(Increased Size) out of the Snapshot taken in Step 1.
Step 3: Stop the Backup Server and detach the EBS Volume attached.
Step 4: Attach the new EBS Volume that we created in Step 2 to the Backup Server.
Step 5: Start the Backup Server.