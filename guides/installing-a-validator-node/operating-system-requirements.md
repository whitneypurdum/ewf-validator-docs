# Operating System Requirements

The following Linux-based Operating Systems are supported for running a validator node:

* Ubuntu Server 18.04 LTS or later
* Debian 9.8 or later
* CentOS 7 or later
* RedHat Enterprise Linux 7.4 or later

Validators can elect other operating systems at their discretion, but may need to customize the installation scripts. Contact [netops@energyweb.org](mailto:netops@energyweb.org) for questions and support.&#x20;

The following section provide a comprehensive guide for installation of one the supported operating systems. All further deployment procedures are based on the installation results.

### **Ubuntu Server 18.04 LTS**

**On-Premise**

Procedure based on version 18.04.2.

* Download the ISO from [https://www.ubuntu.com/download/server](https://www.ubuntu.com/download/server).\

* Boot the ISO
* Select **English** as language
* Choose a convenient keyboard layout
* Choose **Install Ubuntu**
* Let the network auto-configure -or- configure manually if needed. The system needs an internet connection.
* Select no proxy and keep the mirror address.
* Select **Use an entire disk** and confirm
* Choose user name and host name in next screen. Choose a strong password.
* Select **Install OpenSSH Server** but don’t import keys
* Don’t select any snaps and continue
* Finish installation and let it boot to the prompt
* Login as the created user and run a full system update using `sudo apt-get update && sudo apt-get dist-upgrade -y`

**Amazon AWS**

Ubuntu AMI's are listed at [https://cloud-images.ubuntu.com/locator/ec2/](https://cloud-images.ubuntu.com/locator/ec2/). Search for "ebs 18.04 amd64" to get the right version.

**Microsoft Azure**

The URN for the image is **Canonical:UbuntuServer:18.04-LTS:latest**

### **Debian 9.8**

**On-Premise**

* Download the NetInst ISO from [https://www.debian.org/distrib/netinst](https://www.debian.org/distrib/netinst)
* Boot the ISO
* Select **Install** from the boot screen
* Select **English** as language
* Select Location based on actual location of the host
* Chose a convenient keyboard layout
* Let the network auto-configure -or- configure manually if needed. The system needs an internet connection.
* Name your host. Change it from debian to something else
* Choose a strong root password
* Create the user account and choose a strong password
* Select the proper timezone
* For the partitions use **Guided - use entire disk**
* Select **All files in one partition**
* Finish partitioning and write changes to disk
* Select **No** when ask to scan more disks
* Choose a mirror close to the host
* Opt-out of the package survey
* on the **Software Selection** select only **SSH Server** and **standard system utilities**
* Install the grub bootloader to MBR and use the primary disk for that
* Finish installation and let it boot to the prompt
* Login as root and run a full system update using 'apt update && apt dist-upgrade -y'
* Reboot

**Amazon AWS**

The AMI Id's can be found at [https://wiki.debian.org/Cloud/AmazonEC2Image/Stretch](https://wiki.debian.org/Cloud/AmazonEC2Image/Stretch)

**Microsoft Azure**

The URN for the image is **credativ:Debian:9:latest**

### **CentOS 7**

**On-Premise**

* Download the minimal ISO from [https://www.centos.org/download/](https://www.centos.org/download/)
* Boot the ISO
* Confirm the automatic boot option **Test this media & install CentOS 7**
* Choose **English** as language
* On the installation summary choose **Installation destination** and confirm **automatic partinioning**
* Back on the installation summary screen click on **Network & Hostname**
* Change the hostname
* Enable the network interface and make sure it is configured properly
* Click **Done** to get back to the summary and click **Begin Installation**
* During installation set a root password
* Finish installation and let it boot to the prompt
* Login as root and run a system update with 'yum update'

**Amazon AWS**

The AMI Id's can be found at [https://wiki.centos.org/Cloud/AWS#head-78d1e3a4e6ba5c5a3847750d88266916ffe69648](https://wiki.centos.org/Cloud/AWS#head-78d1e3a4e6ba5c5a3847750d88266916ffe69648)

**Microsoft Azure**

The URN for the image is **OpenLogic:CentOS:7.5:latest**
