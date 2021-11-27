Ad-Hoc Network on Linux Terminals:

			 A
	               __|__
		       /|\ \			
		      / | \ \
		     B  C  D...N
		     
		     
A- Ad-hoc head node
B- Ad-hoc client 1
C- Ad-hoc client 2
D- Ad-hoc client 3 
		     
On Node A:
----------

ifconfig wlan0 down
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 channel 4
iwconfig wlan0 essid 'mine'
ifconfig wlan0 10.0.0.1 up

#forwards the ad hoc network to the router
iptables -A FORWARD -i wlan0 -o eth0 -s 10.0.0.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"


$ sudo vi 

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
ap_scan=2
network={
   ssid="my-wifi"
   mode=1
   frequency=2412
   proto=WPA
   key_mgmt=NONE
   pairwise=NONE
   group=TKIP
   psk="s0m3k3y$"
}


To share an internet connection, you need to tell the clients about the DNS servers. See the /etc/resolv.conf file on the server.

On Node B:
----------

iwconfig wlan0 essid mine
iwconfig wlan0 mode Ad-Hoc
ifconfig wlan0 10.0.0.2 up
route add default gw 10.0.0.1


On Node C:
----------

iwconfig wlan0 essid mine
iwconfig wlan0 mode Ad-Hoc
ifconfig wlan0 10.0.0.3 up
route add default gw 10.0.0.1


On Node D:
----------

iwconfig wlan0 essid mine
iwconfig wlan0 mode Ad-Hoc
ifconfig wlan0 10.0.0.4 up
route add default gw 10.0.0.1

On Node N:
----------

iwconfig wlan0 essid mine
iwconfig wlan0 mode Ad-Hoc
ifconfig wlan0 10.0.0.n up
route add default gw 10.0.0.n






