Okay so at this point we have prepped our cluster for setting up persistent storage, which is very exciting!  Before we move into any steps in this portion of the guide, we need to make sure our second set of USB drives are plugged into our cluster, or if you're running with an SSD then make sure those are installed as well.  Once that is complete, we can move on to the next steps.

**Step 1.** We will start off by running the command ``ansible cube -b -m shell -a "lsblk -f"`` this will display to us all of our available storage devices for all nodes across our cluster.  I personally have an extra USB drive for each node (including the master).  Each node should display 2 separate disks, they should have the naming convention along the lines of ``sba`` and ``sdb``.  When looking at these outputs, we will see that there should be drives that have a ``FSAVAIL`` listed and one entry under the same node that doesn't have an entry.  **We do not want to include our drives that are mounted to /boot or /** those are the drives for our OS and we want to make sure we do not wipe that data out, or we will have undone all of our work.

**Step 2.** I did this part with 2 separate command prompt instances running SSH'd into the same node (our master node).  Now, for certain USB drives, they may come in the incorrect format for what we are trying to do.  My USB drives were formatted in exfat format and they need to be ext4 format.  So we will go ahead and wipe our drives and reformat them so we can be sure we are starting with a fresh slate. 

First we will will navigate to our hosts file that we created for Ansible earlier in the walkthrough, if you followed this guiede it should be located in ``etc/ansible/hosts``:

- ``cd /etc/ansible``
- ``nano hosts``

**Step 3.** We should now see our previously created hosts file, we will be adding some information to this file. After our master node entry under our ``[control]`` group, we will be adding ``var_hostname=MASTER_NODE_NAME extra_disk=NAME_OF_STORAGE_DEVICE_TO_WIPE`` where you will add the name of your master node after ``hostname=``.  

** Step 4.** We now will add some information after our worker node entries under our ``[worker]`` group: ``var_hostname=WORKER_NODE_NAME extra_disk=NAME_OF_STORAGE_DEVICE_TO_WIPE``.  **Make sure you put the correct name under the ``extra_disk=`` variable!** My devices were named ``sdb`` when I ran my previous Ansible command, but yours could be different so please make sure you put the correct name here or you could wipe everything out.  We are using the variables ``var_hostname`` and ``extra_disk`` so we can call on those values later as part of our wipe and reformat commands.

**Step 5.** We will now wipe and reformat our USB drives using the following Ansible commands:

- ``ansible cube:children -b -m shell -a "wipefs -a /dev/{{ extra_disk }}"``
- ``ansible cube:children -b -m filesystem -a "fstype=ext4 dev=/dev/{{ extra_disk }}"``

After running the first command, we should see something along the lines of ``calling ioctl to re-read partition table: Success`` which indicates it successfully wiped and re-read the partition table.

After running the second command to reformat, we should see something along the lines of ``"changed": true`` to show a successful reformat.

**Step 6.** We can verify that this was successful by running our Ansible command again: ``ansible cube -b -m shell -a "lsblk -f"`` and observing the output 😄.  All of our drives that we would like to mount will now have a UUID, which will come in handy when mounting them, which we will do in the next section!  See you there!
