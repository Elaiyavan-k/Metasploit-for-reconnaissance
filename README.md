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
<img width="632" height="356" alt="image" src="https://github.com/user-attachments/assets/a66cdd5e-139b-47c9-bab8-11ebcf3f981d" />


Invoke msfconsole:
## OUTPUT:
<img width="577" height="371" alt="image" src="https://github.com/user-attachments/assets/1d9799c0-6b76-4f1e-9854-fed3ded1deec" />
<img width="771" height="738" alt="image" src="https://github.com/user-attachments/assets/ec492228-54e7-4958-9a16-678cd0b1107b" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="553" height="186" alt="image" src="https://github.com/user-attachments/assets/4cb5043f-1702-4ea4-b0fb-7a8b260d6b69" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="698" height="121" alt="image" src="https://github.com/user-attachments/assets/eb7cdcf8-0c35-4e80-95dd-fb83fb244563" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="663" height="86" alt="image" src="https://github.com/user-attachments/assets/7fe3dc19-2cb7-4e22-b2c1-f784404c273b" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="943" height="787" alt="546499457-43d524eb-77ff-4baa-9aa2-1eeb1dc8a2ab" src="https://github.com/user-attachments/assets/df4ce3d4-6858-4dd6-9908-b389358be687" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="790" height="169" alt="image" src="https://github.com/user-attachments/assets/818c206d-587a-40e5-a5f5-7487b1f9ae6c" />




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="741" height="135" alt="546499688-e1a8f352-2e1a-4a2d-8d1f-5e5f668a3fd7" src="https://github.com/user-attachments/assets/370bb654-ecb3-496f-8b36-5a09c1ff6758" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="967" height="572" alt="546499996-720c40dc-b5d9-460c-bcdd-234ba967d8a5" src="https://github.com/user-attachments/assets/c79afd7b-2691-47dd-b364-e80c72614b4e" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="605" height="57" alt="546500107-7776ab14-20aa-4c17-9a2a-51f48a1b272e" src="https://github.com/user-attachments/assets/7a39a9b3-8da0-4271-9f25-6e4cbee73ab9" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="567" height="122" alt="546500450-59024823-553b-479c-ba78-d6e530883de7" src="https://github.com/user-attachments/assets/ad9bf40c-19e9-444b-90e5-753e8fc919ca" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="555" height="97" alt="546501147-9aad778b-691d-4cdd-a140-03b3d5828b47" src="https://github.com/user-attachments/assets/a81c74d2-95e3-410c-b234-237c499a5bfc" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="772" height="457" alt="546501076-42456ae3-75cc-4629-af83-10195725cf90" src="https://github.com/user-attachments/assets/a706973a-6772-4eb9-8fee-d6768a0b525c" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
