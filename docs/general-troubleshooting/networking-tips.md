# 🖥️ Networking Tips

## How to find your computer's IP Address

### Windows

1. Press the Windows key, type **Command Prompt** and open
2. Type in **ipconfig** and press enter<br>
3. Find the ip address you are looking for.\
   Ethernet adapters will be listed as well as any Wireless adapters. You are looking for the **IPv4 address.**<br>

### Mac

1. Search for the Mac app Terminal
2. type in ifconfig and press enter<br>
3. Find for the ip address you are looking for. On my Mac, usually en0 is the wifi

## How to ping a device on the network

If you are trying to connect to a network, you can use the ping command to troubleshoot if the computer can talk to the device you are trying to connect to.

1. (Windows) Click on Windows and search for Command Prompt.\
   (Mac) Search Applications for Terminal.
2.  Type in "ping" then the address you want to ping, with a space between ping and the address. For example I would enter "ping 192.168.1.1"

    If the ping is successful, it will show a number and **bytes** from the address like in this screenshot:<br>

    If the ping is unsuccessful, it will say **Request timeout**.<br>
3. To stop the ping, close the terminal window or press Control+C (Mac and PC).
