# Storage Lab: Working with Amazon EBS

## Objective
- Create an EBS volume.
- Attach and mount an EBS volume to an EC2 instance.
- Create a snapshot of an EBS volume.
- Create an EBS volume from a snapshot.

## Steps Taken
1. Created a new EBS volume in the EC2 Management Console, setting the size to 1 GiB and ensuring it was placed in the same Availability Zone as the running Lab EC2 instance.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 130835.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 131510.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 131536.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 131559.png>)

* Shows the 1 GiB volume ready to be attached, along with its Availability Zone matching the EC2 instance.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 131839.png>)

2. Attached the newly created volume (named My Volume) to the Lab EC2 instance, designating its device name as */dev/sdb*.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 131839.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 132003.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 132048.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 132150.png>)

3. Connected to the Lab EC2 instance using the EC2 Instance Connect terminal in the browser.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 132826.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 132901.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133001.png>)
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133039.png>)

4. Created and configured the file system on the new volume within the Linux instance:
-  Used `sudo mkfs -t ext3 /dev/sdb` to format the volume as an ext3 file system.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133159.png>)
- Created a mount point directory using `sudo mkdir /mnt/data-store`.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133337.png>)
- Mounted the volume with `sudo mount /dev/sdb /mnt/data-store`.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133337.png>)
- Ensured the volume persists across reboots by adding an entry to */etc/fstab*.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133337.png>)

5. Tested the mounted volume by writing a file *(file.txt)* to the */mnt/data-store* directory and verifying its content.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133519.png>)

6. Created an EBS Snapshot *(named My Snapshot)* of the active My Volume.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 133843.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 134101.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 134146.png>)

7. Simulated a data loss by running `sudo rm /mnt/data-store/file.txt` to delete the test file from the original volume.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 140127.png>)

8. Restored the snapshot by creating a new EBS volume *(Restored Volume)* directly from My Snapshot.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135339.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135358.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135504.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135523.png>)

9. Attached the restored volume to the Lab EC2 instance using the device name */dev/sdc*.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135903.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135942.png>) 
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 135955.png>)

10. Mounted the restored volume to a new directory */mnt/data-store2* and verified that the deleted file *(file.txt)* was present, confirming the snapshot was a successful point-in-time backup.
![alt text](<images/Workin With AmazonEBS/Screenshot 2025-12-08 140109.png>)

## Challenges
- The lab didn't present a lot of challenges, however, i noticed how important it is to pay close attention to detail when creating an ESB Volume or Snapshot because a minor mistake such as selecting the wrong availability zone will cause communication errors.

## Takeaways
I learned that EBS volumes are independent of the instance's life, and their proper use requires both console-level attachment and OS-level file system preparation.
