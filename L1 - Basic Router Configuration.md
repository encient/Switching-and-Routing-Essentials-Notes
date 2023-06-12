# Class
PuTTY - software used to configure router using laptop
LAN cable = Ethernet cable
Note: MUST change hostname for every single device

### Level of Access in Router
- 1st level - User mode
	- default mode
	- can see basic information of the router
	- Router>
- 2nd level - Privilege exec mode
	- how to enter this mode: `enable`
	- can see all information of the router
	- Router#
- 3rd level - Global mode
	- how to enter this mode: `configure terminal / config t`
	- Router(config)#


### MUST DO in Assignment
```
Router> enable                     --Switch to from user exec to privilege exec mode
Router# conf t                     --Configure terminal
Router(config)# hostname R1        --Set hostname to R1
R1(config)# enable password cisco  --Set password (from user to priv)
                                   ----insecure, no encryption
R1(config)# enable secret cisco1   --Set password (from user to priv)
                                   ----secure, with encryption, preferred
R1(config)# line vty 0 15          --Enable virtual connection (Telnet, SSH)
                                   ----for 0-15 people (16 people)
R1(config-line)# password cisco2
R1(config-line)# login             --Enable prompt (without it will be locked)
R1(config-line)# exit
R1(config)# line con 0
R1(config-line)# password cisco3
R1(config-line)# login
R1(config-line)# exit

R1# show run                       --Show current operating configuration
R1# conf t
R1(config)# service pass           --Enable password encryption
R1(config)# do show run            --Run privilege mode command

R1(config)# banner motd #Your message here.#
```
- service pass / service password-encryption
- banner motd # No unauthorized access. #

## Login After Configuration
```
Press RETURN to get started!

User Access Verification
Password: cisco3

Router> enable
Password: cisco1
```

## Question:
- cisco3 is enable for line connection 0 only or other line also can? What is line con 0?
- cisco2 is used for SSH and Telnet? Can demonstrate?

# YouTube
https://www.youtube.com/watch?v=-YV9Y_YIDcI

## Basic Router Commands
```
Router(greater than sign)        ---User EXEC mode               exit
Router(greater than sign) ?
Router(greater than sign) enable     
---------------
Router#                          ---Privileged EXEC mode         disable, exit
Router# ?
-----------------
Router# configure terminal / conf t / config t
Router(config)#                  ---Global Config mode           exit, end, Ctrl+c, Ctrl+z
Router(config)# ?
-----------------
Router(config)# line vty 0 15    -----Configure virtual terminal connections (Telnet, SSH)
Router(config)# line console 0   -----Configure on console port
Router(config-line)#             ---Line configuration mode      exit, end, Ctrl+c, Ctrl+z
Router(config-line)# ?
----------------------------
Router(config)# interface gigabitEthernet 0/0/0
Router(config-if)#               ---Interface configuration mode exit, end, Ctrl+c, Ctrl+z
Router(config-if)# ?
----------------------------
Router#
Router# configure terminal
Router# show ?
Router# show running-config / show run
Router# copy running-config startup-config
Router# ping 192.168.1.100
Router# traceroute 192.168.1.100
Router# ssh 192.168.1.100 
Router# telnet 192.168.1.100
Router# debug ?
Router# clock set 07:14:00 October 15 2019
Router# reload
---------------------------------
Router(conf)#
Router(conf)# hostname R1
Router(conf)# banner motd "No unauthorized access allowed!"
Router(conf)# enable password class
Router(conf)# enable secret class
Router(conf)# service password-encryption
Router(config)# line vty 0 15
Router(config)# line console 0
Router(config)# interface gigabitEthernet 0/0/0
----------------------------------------------------
Router(config-line)# 
Router(config-line)# password cisco
Router(config-line)# login                                 -----Enable login prompt
Router(config-line)# transport input all   (line vty)      -----Enable Telnet & SSH
----------------------------------------------------
Router(config-if)# 
Router(config-if)# interface gigabitEthernet 0/0/0
Router(config-if)# int g0/0                              //command abbreviation
Router(config-if)# ip address 192.168.1.1 255.255.255.0 
Router(config-if)# no shutdown                             -----To turn on interface
```

## Basic Switch Commands
```
Switch(greater than sign)        ---User EXEC mode               exit
Switch(greater than sign) enable     
---------------
Switch#                          ---Privileged EXEC mode         disable, exit
-----------------
Switch# configure terminal
Switch(config)#                  ---Global Config mode           exit, end, Ctrl+c, Ctrl+z
-----------------
Switch(config)# line vty 0 15
Switch(config)# line console 0
Switch(config-line)#             ---Line configuration mode      exit, end, Ctrl+c, Ctrl+z
----------------------------
Switch(config)# interface vlan 1
Switch(config-if)#               ---Interface configuration mode exit, end, Ctrl+c, Ctrl+z
----------------------------
Switch#
Switch# configure terminal
Switch# show ?                
Switch# show running-config
Switch# copy running-config startup-config
Switch# ping 192.168.1.100
Switch# traceroute 192.168.1.100
Switch# ssh 192.168.1.100 
Switch# telnet 192.168.1.100
Switch# debug ?
Switch# clock set 07:14:00 October 15 2019
Switch# reload
---------------------------------
Switch(conf)#
Switch(conf)# hostname R1
Switch(conf)# banner motd "No unauthorized access allowed!"
Switch(conf)# enable password class
Switch(conf)# enable secret class
Switch(conf)# service password-encryption
Switch(config)# line vty 0 15
Switch(config)# line console 0
Switch(config)# interface vlan 1
----------------------------------------------------
Switch(config-line)# 
Switch(config-line)# password cisco
Switch(config-line)# login
Switch(config-line)# transport input all   (line vty)
----------------------------------------------------
Switch(config-if)# 
Switch(config-if)# interface vlan 1
Switch(config-if)# ip address 192.168.1.2 255.255.255.0 
Switch(config-if)# no shutdown
Switch(config-if)# exit
Switch(config)# ip default-gateway 192.168.1.1
```

## Extra Helpful Commands
```
Router(conf)# no ip domain-lookup       //prevents miss-typed commands from being "translated..." 
Router(conf-line)# logging synchronous  //prevents logging output from interrupting your command input
```