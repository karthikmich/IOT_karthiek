# Follow these steps for 0S installation 

1. Setup your working environment on your laptop
Prepare your device to with an archiver extractor - on windows I used BreeZip http:www.breezip.com but others are available from https://www.7-zip.org . On MacOS V11 it extracted using tools already installed but an unarchiver is available at https://theunarchiver.com for your mac if extraction is not working.
Prepare you laptop with a sd card writer such as: balenaEtcher https://www.balena.io/etcher/
2. Download and configure DietPI on your laptop
Download and extract the DietPi disk image

Go to https://dietpi.com/#download and select the RaspberyPI Images
On the new page choose the download for your targeted pi
Write the DietPi image to your SDcard using balenaetcher or other flashing software

Open balenaetcher
Select the dietpi image
Select the targeted card ( that was inserted into your laptop)
Press flash ( you may have to put in your credentials. I also had to try a second time to make it work. )
Wait until the flash finished and verifies the copy
Close balenaetcher
Configure the boot image on the microSD card of dietpi.

copy dietpi.txt and dietpi-wifi.txt to a temporary directory
edit dietpi-wifi.txt with your router ssid and creadentials Change the lines:
                          
                           aWIFI_SSID[0]=''
                           aWIFI_KEY[0]=''
                          
adding your SSID and ssid_password for example SSID= Karthiektej and password= ********** 

edit dietpi.txt with your location and wifi network default settings For the East Coast US settings change the values of the variables listed below
                
                
                  AUTO_SETUP_LOCALE=en_US.UTF-8
                  AUTO_SETUP_KEYBOARD_LAYOUT=us
                  AUTO_SETUP_TIMEZONE=America/New_York
                  AUTO_SETUP_NET_ETHERNET_ENABLED=0
                  AUTO_SETUP_NET_WIFI_ENABLED=1
                  AUTO_SETUP_NET_WIFI_COUNTRY_CODE=US
                  AUTO_SETUP_DHCP_TO_STATIC=1
                  AUTO_SETUP_NET_HOSTNAME=DietPi_{YOUR_INITIALS}
                  AUTO_SETUP_HEADLESS=1
                  AUTO_SETUP_AUTOSTART_TARGET_INDEX=1
                  SURVEY_OPTED_IN=0
                  CONFIG_SERIAL_CONSOLE_ENABLE=1
                  
                  
be sure to replace {YOUR_INITIALS} with a locally unique string for me I used KG so my pit is names DietPi_KG.
search for each variable before the = and put in the new value in the file.
be sure to save the changes

Copy the dietpi.txt and dietpi-wifi.txt you edited to the top level directory of your sd card.

Eject the SD card from your laptop

Install SD card onto the PI and powerup the PI to run DietPI
You should see the red led turn on and the green led will start to flash as the install is running
Wait until the green light has finished flashing - could take 10 minutes or more depending on the local network load.
Login to the DietPi using the wireless access point
Using the admin website of your router at (if using vanilla openwrt configuration it usually found at 192.168.8.1
check the CLIENTS page for the IPADDR of the pi that is booted up.



<img width="1440" alt="CLIENTS" src="https://user-images.githubusercontent.com/112646644/190835190-43cd78b5-e8fc-4407-82e0-d7c2bd85824d.png">





use SSH to login into your PI using
ssh root@IPADDR
password: dietpi
be sure to change your root login during setup

 
You are now ready to start install platform software.
Continue with other installs such as: IOT Platform Install mostly by using diepi-software

