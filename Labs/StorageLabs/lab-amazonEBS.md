# Storage Lab: Working with Amazon EBS

## Objective
- Create an EBS volume.
- Attach and mount an EBS volume to an EC2 instance.
- Create a snapshot of an EBS volume.
- Create an EBS volume from a snapshot.

## Steps Taken
1. Created a new EBS volume in the EC2 Management Console, setting the size to 1 GiB and ensuring it was placed in the same Availability Zone as the running Lab EC2 instance.
2. Attached the newly created volume (named My Volume) to the Lab EC2 instance, designating its device name as /dev/sdb.
3. Connected to the Lab EC2 instance using the EC2 Instance Connect terminal in the browser.
4. Created and configured the file system on the new volume within the Linux instance:
-  Used sudo mkfs -t ext3 /dev/sdb to format the volume as an ext3 file system.
- Created a mount point directory using sudo mkdir /mnt/data-store.
- Mounted the volume with sudo mount /dev/sdb /mnt/data-store.
- Ensured the volume persists across reboots by adding an entry to /etc/fstab.
5. Tested the mounted volume by writing a file (file.txt) to the /mnt/data-store directory and verifying its content.
6. Created an EBS Snapshot (named My Snapshot) of the active My Volume.
7. Simulated a data loss by running sudo rm /mnt/data-store/file.txt to delete the test file from the original volume.
8. Restored the snapshot by creating a new EBS volume (Restored Volume) directly from My Snapshot.
9. Attached the restored volume to the Lab EC2 instance using the device name /dev/sdc.
10. Mounted the restored volume to a new directory /mnt/data-store2 and verified that the deleted file (file.txt) was present, confirming the snapshot was a successful point-in-time backup.

## Challenges
- 

## Screenshot
![Challenge Instructions](images/Linux%20Lab%20Challenge%20Instructions.png "Instructions")
After launching the Linux terminal with SSH, you log into terminal as EC2-User, and proceed to running commands.

* Shows the 1 GiB volume ready to be attached, along with its Availability Zone matching the EC2 instance.

* Confirms the correct instance and device name were chosen before attachment.

* Demonstrates that the new disk space is successfully recognized and mounted at /mnt/data-store.

* Indicates the successful connection of the disk to the instance.

* Confirm the point-in-time backup process finished successfully.

* Proves the restored volume contains the backed-up file, validating the entire recovery process.

## Takeaways
I learned that EBS volumes are independent of the instance's life, and their proper use requires both console-level attachment and OS-level file system preparation.
