# TryHackMe CTF Writeup

![logo](https://github.com/AVs0x/CTF-Write-up/assets/111527380/4e93b5c6-eb31-4ffc-8fd0-bfa7581801d5)

## Try Hack Me - Pwn The Flags

##### URL: tryhackme.com/jr/pwntheflags

##### Created by AVS0X.

Task 1)  Deploy The Machine

You should deploy the machine first.

Task 2)  Reconnaissance 

Run nmap against the target machine.

```nmap -sC -sV <target IP>```

![asa3](https://github.com/AVs0x/CTF-Write-up/assets/111527380/504860e8-257d-4012-a0bb-cb0adaac7f30)

We have the first answers to the relevant questions based on the scan.

Next we fire up gobuster in order to seach for paths in the web application that will help us to map the app.

```gobuster dir -u <target IP> -w <wordlist location>```


![ads](https://github.com/AVs0x/CTF-Write-up/assets/111527380/13c00e4f-72d3-44e5-ad72-acaea3ee5fe2)

We access the panel path and we observe that uploads directory has a file containing base64 message.

Decode the base64 using CyberChef 
URL: https://gchq.github.io/CyberChef/

Task 3)  Find the 🚩

Now We'll login into ftp server, As nmap scan reviled that Anonymous login allowed.

```ftp <target IP>```
Name as anonymous and hit enter.

