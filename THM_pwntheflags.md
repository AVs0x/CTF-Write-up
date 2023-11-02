# TryHackMe CTF Writeup

![logo](https://github.com/AVs0x/CTF-Write-up/assets/111527380/4e93b5c6-eb31-4ffc-8fd0-bfa7581801d5)

## Try Hack Me - Pwn The Flags

##### URL: https://tryhackme.com/room/pwntheflags

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

Specify Name as anonymous and for password just hit enter.


![asa3w](https://github.com/AVs0x/CTF-Write-up/assets/111527380/0dffdf09-253c-4f2f-bdd0-f69110b44d5b)

use get command to download the files.  ```get filename```

To crack the hashes you can use John the Ripper tool or crackstation.net

![asdas3](https://github.com/AVs0x/CTF-Write-up/assets/111527380/31255eeb-e001-409f-b2b9-91f4c3c04131)

Now unzip the zip file using  ```unzip filename``` and provide the password retrieved from the hash.

Voila!! Now We have successfully found Flag1.txt
 ```cat Flag1.txt```
 
For Flag2 we need to use SSH Brute Forcing technique. We'll be using hydra tool.

```hydra -l <username> -P <wordlist location> <target IP> ssh```

![as2as7](https://github.com/AVs0x/CTF-Write-up/assets/111527380/d766238b-28ba-4e6c-98bf-dac427887d44)

Now login to ssh using ```ssh <username>@<target IP>```

Let's list the file and directories using ```ls``` 

Voila!! We found Flag2.txt
```cat Flag2.txt```

let's try to use sudo for root access. 
```sudo su```
Now locate to /root directory.
```cd /root```

Here we have Leo's secret file.

![aseed3](https://github.com/AVs0x/CTF-Write-up/assets/111527380/96bd5dfa-a6cd-4ea7-9746-9a6a7e4b9328)

Now we'll crack the given hash using John the Ripper tool or crackstation.net
![asads3](https://github.com/AVs0x/CTF-Write-up/assets/111527380/231f17ed-a105-4cda-a80e-a967169317fb)

Now We'll login as leo by ```su leo``` and locate to ```cd /home/leo```.

To Decrypt the file we'll be using ```ccdecrypt Flag3.txt.cpt``` followed by the password retrieved from Leo's secret file.

Finally!! We found Flag3.txt
```cat Flag3.txt```



![sadw](https://github.com/AVs0x/CTF-Write-up/assets/111527380/17dce597-0995-4880-aa59-68c0018b91be)

And now we have all the flags.

CONGRATULATIONS!!! YOU HAVE COMPLETED THE ROOM!!!


