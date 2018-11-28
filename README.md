## Voice Enabled Smart Mirror
Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime velit earum repellendus reiciendis esse id molestiae tempora ullam amet veritatis iure temporibus consectetur, quas, nesciunt, quod et quae soluta qui. Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime velit earum repellendus reiciendis esse id molestiae tempora ullam amet veritatis iure temporibus consectetur, quas, nesciunt, quod et quae soluta qui.
### Table of Contents

 - Repositories
 - Requirements
	 - Hardware
	 - Software
	 - Optional
 - Installation
	 - Hardware Setup


### Repositories

 - smart-mirror-electron
 - smart-mirror-configurator
### Requirements
Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime velit earum repellendus reiciendis esse id molestiae tempora ullam amet veritatis iure temporibus consectetur, quas, nesciunt, quod et quae soluta qui.
#### Hardware 

 - [Raspberry Pi 3+](https://www.amazon.com/Raspberry-Pi-RASPBERRYPI3-MODB-1GB-Model-Motherboard/dp/B01CD5VC92/ref=sr_1_5?s=pc&ie=UTF8&qid=1543362710&sr=1-5&keywords=raspberry%20pi)
 - [Acrylic See-Through Mirror](https://www.amazon.com/12-Acrylic-See-Through-Mirror/dp/B017ONH3EG)
 - Raspberry Pi Compatible Camera 
 - Raspberry Pi Compatible Microphone 
 - 1920 x 1080 Resolution Monitor
 - 8 GB or Larger microSD Storage
 
#### Software 
 - NPM (Additional dependencies will be installed using NPM)
 - Git (Additional software will be installed using Git)

#### Optional 

 - Google Developers API Key
 - NewsAPI API Key
 - Open Weather Map API Key
 - Import.io API Key
 
 ### Installation
Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime velit earum repellendus reiciendis esse id molestiae tempora ullam amet veritatis iure temporibus consectetur, quas, nesciunt, quod et quae soluta qui.

#### Hardware Setup

 1. Attach the microphone and camera to the Raspberry Pi following the manufacturers' instructions.
 2. Connect the Raspberry Pi to the display via HDMI to whatever input is available on the display.
 3. Attach the acrylic see through mirror to the front of the display. 
 4. Connect the Raspberry Pi and display to a power source.

#### Software Setup
1. Download the most updated version of Raspbian from https://www.raspberrypi.org/downloads/raspbian/ and load it onto the Raspberry Pi microSD storage. 
2. (Optional) If you want the Smart Mirror to be vertical, continue with this step. Otherwise, skip to step 3. Boot up the Raspberry Pi and run the following command in the terminal.

   ```bash 
   sudo nano /boot/config.txt
   ```
	  Add `display_rotate=3` to the bottom of the list and save.
3. Install NPM https://www.npmjs.com/get-npm and verify the installation by running the following command in the terminal.
	```bash
	npm -v
	```
4. Clone the smart-mirror-electron repository and `cd` into the directory. This repository contains the src files for the Electron packaged Angular 6 web application.
	```bash
	git clone https://github.com/kevintrankt/smart-mirror-electron.git
	cd smart-mirror-electron
	```
5. Install Angular and all other NPM dependencies
	```bash
	npm install -g @angular/cli
	npm install
	```
6. Create a Smart Mirror config file by navigating to https://kevintrankt.com/smart-mirror-config. You can read more about how to set up users in the user config in the next section.
7. Verify your installation by running the following command in the terminal. If everything worked perfectly, you should now have a functioning Smart Mirror! 
You can test logging into each account by typing numbers associated to the user and pressing space to logout. 

The following steps will cover how to integrate facial recognition with OpenCV and voice control with Amazon Alexa with the Smart Mirror.

8. TODO: Add OpenCV README
9. TODO: Add Amazon Alexa README
  
### User Config
