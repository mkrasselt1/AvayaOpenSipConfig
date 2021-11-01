# AvayaOpenSipConfig
My working configuration and findings to get avaya phones working with any open sip server
Tested Working: Avaya 9641G
1. First you need to find the VLAN of the used phone you got and setup a layer 2 switch with that vlan
2. Setup up a DHCP Server to the VLAN and IP range, the phone was looking for during boot
3. Set Gerneal DHCP Option 242 to Character String "PROCSTAT=0,PROCPSWD=27238"
4. Reboot the phone - wait for the second time the phone offers you "press star for admin menu"
5. Enter the Code 27238 as in the DHCP Option and select factory reset and restart again
6. Wait for the phone to be booted up for the second time
7. Set up an HTTP Server and note down IP Adress
8. Create folder with lowercase macadress without separators
9. Upload 46xxsettings.txt as well as language and sip firmware files for your phone from avaya website
10. Add a DHCP Reservation for this phone and add DHCP Option 242 to character String "HTTPDIR=/MACADRESS/,HTTPPORT=80,HTTPSRVR=IP.ADDRESS.OF.SERVER,SIG=2" - remember to change mac address to the phones mac and ip adress of the http server
11. reboot the phone again
12. wait until the firmware update took place - takes about 5-10 minutes, might not work at the first try
13. change sip settings to your sip server and reboot the phone again
