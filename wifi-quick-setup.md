
# Prepare Raspberry for login via wifi from the beginning:

## 1. Before booting for the first time put these two files into /boot partition:
- ssh (empty)
- wpa_supplicant.conf:
```
country=DE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
    ssid="my-ssid"
    psk="my-password"
}
```

## 2. When Raspberry has already booted, add this to /etc/network/interfaces
for preventing loss of connection when using wifi:
```
wireless-power off
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```
