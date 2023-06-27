### Follow below steps to route traffic from USB to Ethernet port in OpenWrt.

> Assuming that you have already installed OpenWrt in your Raspberry-Pi 4 B

### Step 1: Setup Wi-Fi as it requires some software installation.
1. Open browser and enter url: http://192.168.1.1/
2. Click on drop down menu <Network> and select <Wireless>
3. In Wireless Overview section beside radio0 click on <scan>. It will start wireless scan.
4. Choose your network's SSID having internet access and click on <Join Network>
5. Enter your network password in <WPA passphrase> and click submit.
6. Click on save and apply button to connect to this wireless network.
7. To check it internet is working properly. Click on drop down menu <Network> and select <Diagnostics>
8. Under Network Utilities section click on <ping>
9. It will give ping us back as long as we have internet connection.

### Step 2: Install USB driver
1. ssh your Raspberry-Pi device (make sure Raspberry-Pi is connected to your computer using RJ45 cable). 
```sh
ssh root@192.168.1.1
```
2. Install the required packages
```sh
opkg update
opkg install kmod-usb-net-rndis
```
#### After installing drivers, You can disconnect Wi-Fi.

## Step 3: Connection setup
To establish a connection between your LAN cable originating from the router and your Raspberry Pi, follow these steps:
1. Take the LAN cable from your router.
2. Connect the LAN cable to a USB LAN adaptor.
3. Plug the USB LAN adaptor into an available USB slot on your Raspberry Pi.

To establish a connection between your computer and Raspberry Pi using a LAN cable, follow these steps:

1. Take the LAN cable.
2. Connect one end of the LAN cable to the LAN port of your computer.
3. Connect the other end of the LAN cable to the LAN port of your Raspberry Pi.

## Step 4: OPENWRT Traffic Routing
1. Open browser and enter url: http://192.168.1.1/
2. Click on drop down menu <Network> and select <Interfaces>
3. Click on Add new interface ...
4. Create a new Interface with name <USB_4G> , select Device <eth1> and Protocol <DHCP client>
6. Go to Interfaces Â» USB_4G Â» Firewall Settings
   Create / Assign firewall-zone
   Select <wanUSB_4G:> 
7. Select network/firewall 
   Inside Zones section
   edit <wan>
   Select <USB_4G> in Covered networks. 


## License
**Free Software, Hell Yeah!**

## Authors
- [Rahul Gupta](https://github.com/rahulelex)
