#What is Snort?

Snort is the foremost Open Source Intrusion Prevention System (IPS) in the world. Snort IPS uses a series of rules that help define malicious network activity 
and uses those rules to find packets that match against them and generates alerts for users.

#Snort has three primary uses: 

1.As a packet sniffer like tcpdump 

2.as a packet logger — which is useful for network traffic debugging

3.it can be used as a full-blown network intrusion prevention system. 

---SNORT INSTALLATION - UBUNTU---

#Make a Backup of Current Sources.list File

First, we need to create a backup of Kali’s sources.list file in order to restore it later:

mv /etc/apt/sources.list /etc/apt/sources.list.bak

#Remove currently installed Kali Updates

#Go to /var/lib/apt/lists and delete all the files within the directory, leaving only the partial and auxfiles directory:

find /var/lib/apt/lists -type f -exec rm {} \;

#Download Ubuntu Sources.list File

#Download Ubuntu’s sources.list file into the /etc/apt/ directory:

wget https://gist.githubusercontent.com/ishad0w/788555191c7037e249a439542c53e170/raw/3822ba49241e6fd851ca1c1cbcc4d7e87382f484/sources.list -O /etc/apt/sources.list

#Download Ubuntu Sources.list File

#Download Ubuntu’s sources.list file into the /etc/apt/ directory:

wget https://gist.githubusercontent.com/ishad0w/788555191c7037e249a439542c53e170/raw/3822ba49241e6fd851ca1c1cbcc4d7e87382f484/sources.list -O /etc/apt/sources.list

#Attempting to Update

#Attempting to update withsudo apt updateusing the Ubuntu Sources.list file will generate an error regarding GPG public keys:

GPG error: http://archive.ubuntu.com/ubuntu focal-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32 NO_PUBKEY 871920D1991BC93C

#informing us that the Ubuntu server public keys were not found on our machine. So, we need to add the specified public keys to our computer:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 871920D1991BC93C

#Run sudo apt update and you should be ready to install snort now!

---Install Snort---
#After successfully updating our apt repository using the Ubuntu sources.list file, we can install Snort:

sudo apt install snort

#Note: You will be prompted to enter the IP address or IP address range of your computer using CIDR notation for Snort’s configuration. Enter your IP address or IP address range and hit enter.

---CONFIGURATION---

1.enter ethernet interface as 'enp0s3'

2.enter ip address range as '192.168.25.0/24'


#Restoring Kali’s Repository Sources.list File

#After installing Snort, remove the new update files located in /var/lib/apt/lists:

find /var/lib/apt/lists -type f -exec rm {} \;

#Then, rename the current Ubuntu sources.list file to ubuntu_sources.list, just in case you need it again in the future:

mv /etc/apt/sources.list /etc/apt/ubuntu_sources.list

#Finally, rename the Kali Linux /etc/apt/sources.list.bak file back to /etc/apt/sources.list:

mv /etc/apt/sources.list.bak /etc/apt/sources.list

#and run 

sudo apt update && sudo apt upgrade.

#The End
You now have Snort installed! Run snort --version to confirm the installation. 

