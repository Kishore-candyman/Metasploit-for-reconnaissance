# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="659" height="341" alt="image" src="https://github.com/user-attachments/assets/271fbe85-d39c-4522-b088-f882bc90d04f" />

Invoke msfconsole:
## OUTPUT:
<img width="744" height="538" alt="image" src="https://github.com/user-attachments/assets/cb080889-2c62-431c-8e62-4e9877805850" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="877" height="1086" alt="image" src="https://github.com/user-attachments/assets/d9e004fa-518e-4467-b37c-7b74f3cd504c" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)

## OUTPUT:
<img width="558" height="191" alt="image" src="https://github.com/user-attachments/assets/6631b7da-a765-4676-8a86-533486f80d92" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="635" height="136" alt="image" src="https://github.com/user-attachments/assets/e82eb899-90de-4f40-a302-7d1ec3e4ca91" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="584" height="292" alt="image" src="https://github.com/user-attachments/assets/4f6c39f9-5285-40a7-beeb-7081f90b3984" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1122" height="1068" alt="image" src="https://github.com/user-attachments/assets/e41c4b88-6cda-48aa-b115-503406d4b13b" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="870" height="145" alt="Screenshot 2026-05-17 131204" src="https://github.com/user-attachments/assets/24272593-aa6f-4476-af58-8f5f3a4ddb16" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1032" height="536" alt="image" src="https://github.com/user-attachments/assets/05c6cea2-2dc1-4ec5-afb7-1d992312b76a" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1003" height="393" alt="image" src="https://github.com/user-attachments/assets/506ac18a-9c4f-4187-8cae-85a02929664d" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/0d895d4d-0445-40f3-9f1f-307a54739520" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/b05049af-5f55-45d2-9e7d-8c5c2ed7cc04" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
