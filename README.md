# Raspberry Pi HomeKit Garage Door Controller + Cam

## Acknowledgements
Camera code based on [HomeKitCam](https://github.com/Didel/HomeKitCam)

**Blog:** [Building a Siri/iOS HomeKit-Enabled Garage Door Control with Raspberry Pi](https://spin.atomicobject.com/2017/08/20/siri-homekit-raspberry-pi-hardware/)

## Setup Pi for Headless**
I'm using a pi zero w, but other pi's should follow the same instructions.  Here is an [excellent guide with more details](https://hackernoon.com/raspberry-pi-headless-install-462ccabd75d0)
Cliff Notes version:
1. Download [RASPBIAN STRETCH LITE](https://www.raspberrypi.org/downloads/raspbian/)
2. Burn the image onto a new SD card (I like to use etcher).
3. Put the SD card back into your mac (or remount it)
4. Enable ssh
  * `cd /volumes/boot`
  * `touch ssh`
5. Setup WIFI
  * nano `wpa_supplicant.conf`
  * paste the following into `wpa_supplicant.conf` (setting your ssid and psk accordingly)
  ```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US

network={
	ssid="Your network SSID"
	psk="Your WPA/WPA2 security key"
	key_mgmt=WPA-PSK
}
  ```
## Install dependencies
1. Eject the SD card from your mac and insert into your pi and power it up.
2. Find it's ip address.  You can try `ping raspberrypi` or `nslookup...` or check your router's UI.
3. ssh into your pi
```
ssh pi@192.168.1.xxx
password: raspberry
```
4. Update your pi:
`sudo apt-get update`
5. [Install nodejs](http://www.instructables.com/id/Install-Nodejs-and-Npm-on-Raspberry-Pi/)
 * `uname -m`
 * Get [nodejs](https://nodejs.org/en/download/)
 * Right-click to copy the download link for your version of **ARM**
 * Run the following command to from your ssh session to download nodejs - be sure to change the link to end in **gz**
   * ` wget https://nodejs.org/dist/v8.11.1/node-v8.11.1-linux-armv6l.tar.gz`
 * Extract the gzip
   * `tar -xzf node-v8.11.1-linux-armv6l.tar.gz`
 * Copy it to `/usr/local`
   * `cd node-xxxx`
   * `sudo cp -R * /usr/local/`
6. Install git and some other dependencies needed to compile [HAP-NodeJS](https://github.com/KhaosT/HAP-NodeJS/wiki/Installing)
 * `sudo apt-get install -y git git-core libnss-mdns libavahi-compat-libdnssd-dev libav-tools`
7. Install yarn
 * `sudo npm install -g yarn`
 
## setup Garage-PI
1. Clone this repo.
 * `git clone https://github.com/foleymic/garage-pi.git`
 * `cd garage-pi`
2. Download packages
 * `yarn`
3. Start it up...
 * `yarn controller`
 
 
## License
MIT
