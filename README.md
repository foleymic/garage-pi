# Raspberry Pi HomeKit Garage Door Controller + Cam

## Acknowledgements
Camera code based on [HomeKitCam](https://github.com/Didel/HomeKitCam)

**Blog:** [Building a Siri/iOS HomeKit-Enabled Garage Door Control with Raspberry Pi](https://spin.atomicobject.com/2017/08/20/siri-homekit-raspberry-pi-hardware/)

**Setup Pi for Headless**
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

## License
MIT
