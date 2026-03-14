# EBS-Mount-volume
 process of how to add and mount EBS Volume on Ubuntu EC2 Linux Instance
# How it works
Amazon Elastic Block Store (Amazon EBS) is an easy-to-use, scalable, high-performance block-storage service designed for Amazon Elastic Compute Cloud (Amazon EC2).
# Prerequisites:
An active AWS account.
An EC2 instance running Ubuntu.
# Step 1: Create an EBS Volume:
Open the AWS Management Console and navigate to the EC2 dashboard.
In the left navigation pane, choose “Volumes” under the “Elastic Block Store” section.
Take note of the existing volumes.
Click “Create Volume” to add a new EBS volume.
# Step 2: Attach EBS Volume to EC2 Instance:
# Step 3: Connect to your EC2 Instance:
Use the following command to list the available block devices:
**lsblk**
Identify your attached volume (e.g., /dev/xvdf)
# Step 4: Create a Filesystem on the EBS Volume:
Let’s first create a directory to be used as the mount point:
**mkdir -p /mnt/ebs_volume**
 Now use the below command to create a filesystem on the attached volume: ** mkfs -t ext4 /dev/xvdf**
Now if we verify if the new file system exists use the below command and you should see the output:

** file -s /dev/xvdf**
/dev/xvdf: Linux rev 1.0 ext4 filesystem data, UUID=8e2aa1fb-46c9-4461-a150-eb333
**Step 5: Mount the EBS Volum**e:
Mount the EBS volume to the specified mount point:
**mount /dev/xvdf /mnt/ebs_volume**


=========================================================================================================

**Step 6: Configure Automatic Mount on Boot:**
Open the /etc/fstab file in a text editor:
**nano /etc/fstab**
2. Add the following line to the end of the file:

**/dev/xvdf   /mnt/ebs_volume   ext4   defaults,nofail   0   2**
Save and exit the editor.
