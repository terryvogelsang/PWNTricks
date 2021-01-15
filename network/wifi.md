# Wifi Security

## Step-by-step

### 1. List available wireless interface
#### Using airmon-ng
`airmon-ng`

### 2. Enable monitor mode on wireless interface
#### Check and kill potentially conflicting processes with 
Check processes
`airmon-ng check`

Kill them
`airmon-ng check kill`

#### Put Wireless adapter in monitor mode
`airmon-ng start <your_wireless_interface>`

### 3. Start capturing packets and environment mapping
#### Using airodump-ng
`sudo airodump-ng --write airodump-ng-dumps/airodump-ng.dump <your_wireless_interface>`


### X. Crack WPA2 captured PSKs
Offline can be made faster by pre-generating PMKs (Pairwise Master Key) table using the SSID and a wordlist of possible PSKs. This can be done using cowpatty's `genpmk` utility.

## Encryption Algorithms

### WEP

### WPA/WPA2 
> Wi-Fi Protected Access (WPA) protects wireless data by applying encryption, integrity checks, and sequencing. The first version of WPA patched around mistakes in the old, broken Wired Equivalent Privacy (WEP), while WPA2 started from a clean slate to deliver more robust, efficient security. - Practically Networked

### WPA/WPA2 Personal / WPA-PSK
> Since home networks don't generally have RADIUS servers, a simpler option also exists: Pre-Shared Keys (PSKs). Known as WPA-PSK, WPA-Personal or WPA2 Personal, this approach authenticates everyone using the WLAN with the same secret passphrase, configured into the Access Point (AP). But, unlike those old WEP keys, PSKs are not encryption keys -- they are the starting point for deriving per-station (client) encryption keys. - Practically Networked

> Unfortunately, the way in which WPA/WPA2 encryption keys are generated and delivered makes it easy for an attacker to try to guess your WLAN's PSK. Once an outsider has the PSK, he can steal service or decrypt data sent by legitimate users on your network. - Practically Networked

#### WPA/WPA2 Enterprise
WPA Enterprise or WPA2 Enterprise corresponds to the use of WPA with 802.1X Port Access Control for per-user authentication and per-session key delivery. It requires RADIUS-based authentication. In this configuration, every new session gets its own, unique, random and short-lived key.

## Tools
- [Airmon-ng - Documentation](https://www.aircrack-ng.org/doku.php?id=airmon-ng)
- [cowpatty - GitHub](https://github.com/joswr1ght/cowpatty)

## References
- [Aircrack-ng - Tutorial: How to Crack WPA/WPA2](https://www.aircrack-ng.org/doku.php?id=cracking_wpa)
- [Practically Networked - WPA PSK Crackers: Loose Lips Sink Ships](http://www.practicallynetworked.com/security/041207wpa_psk.htm)
