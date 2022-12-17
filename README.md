---Detect NMAP Scan Using Snort---

#Requirement

Attacker: Kali Linux (NMAP Scan)

Target: Ubuntu (Snort as IDS)

Let’s Begins!!

---Identify NMAP Ping Scan---

#As we know any attacker will start the attack by identifying host status by sending ICMP packet using ping scan.

#Execute given below command in ubuntu’s terminal to open snort local rule file in text editor.

sudo nano /etc/snort/rules/local.rules

#add the rule given below to local.rule

#this will capture the incoming traffic coming on 192.168.1.105(ubuntu IP) network for ICMP protocol.

alert icmp any any -> 192.168.1.105 any (msg: "NMAP ping sweep Scan"; dsize:0;sid:10000004; rev: 1;)

#Turn on IDS mode of snort by executing given below command in terminal:

sudo snort -A console -q -u snort -g snort -c /etc/snort/snort.conf -i enp0s3

#Now using attacking machine execute given below command to identify the status of the target machine i.e. host is UP or Down.

nmap -sP 192.168.1.105 --disable-arp-ping

#If you will execute above command without parameter “disable arp-ping” then will work as default ping sweep scan which will send arp packets in spite of sending 
ICMP on targets network and maybe snort not able to capture NMAP Ping scan in that scenario, therefore we had use parameter “disable arp-ping” in the above command.





