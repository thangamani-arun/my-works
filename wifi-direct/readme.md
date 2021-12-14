There are ways to setup Wi-Fi Direct if your wi-fi adapter supports P2P GO and P2P Client using `iw list` command

```
$ sudo iw list | grep -A10 modes
Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
		 * mesh point
		 * P2P-GO
		 * P2P-Client
```
