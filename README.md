


## [Voice Enabled Smart Mirror](https://github.com/kevintrankt/smart-mirror-readme)
The Voice Enabled Smart Mirror is a smart home project that allows information to be seen through a mirror. The Smart Mirror features customizable widgets, multi-user support, Amazon Alexa integration, facial recognition, and gesture based interaction. This README will provide users with the steps and tools needed to set up their own Voice Enabled Smart Mirror.

### Table of Contents

 - Video Demo
 - Repositories
 - Requirements
	 - Hardware
	 - Software
	 - Optional
 - Usage
	 - Gestures
 - Installation
	 - Hardware Setup
	 - Software Setup
		 - Amazon Alexa
 - Smart Mirror Config
	 - Adding/Removing a User
	 - Saving Your Config
	 - Loading an Existing Config
	 - API Keys
	 - Users
	 - Widget Layout
	 - Widgets
		 - Clock
		 - Weather
		 - News
		 - Agenda
		 - Subreddit
		 - Destination
		 - Forecast
 - Making a Custom Widget
 - Configuring and Running Alexa

### [Video Demo](https://youtu.be/EH-0puEEL3A)
A demo of the Voice Enabled Smart Mirror can be viewed here https://youtu.be/EH-0puEEL3A.

### Repositories

 - [smart-mirror-electron](https://github.com/kevintrankt/smart-mirror-electron)
 - [smart-mirror-config](https://github.com/kevintrankt/smart-mirror-config)
 - [smart-mirror-alexa](https://github.com/juliebee1024/smart-mirror-alexa/tree/master)
 - [smart-mirror-facial-recognition](https://github.com/vincentchu12/smart-mirror-facial-recognition)
 
### Requirements
The Smart Mirror is designed to be an interactive project for educational purposes. Because of this, many requirements are optional to ensure anyone can clone the project and work on it with limited supplies. The Smart Mirror is built using Electron which makes the frontend cross platform compatible with macOS, Linux, and Windows. 
The requirements below are to build an actual Smart Mirror, but to develop and play with the Smart Mirror, you will only need the software requirements.
#### Hardware 

 - [Raspberry Pi 3B+](https://www.amazon.com/Raspberry-Pi-RASPBERRYPI3-MODB-1GB-Model-Motherboard/dp/B01CD5VC92/ref=sr_1_5?s=pc&ie=UTF8&qid=1543362710&sr=1-5&keywords=raspberry%20pi)
 - [Acrylic See-Through Mirror](https://www.amazon.com/12-Acrylic-See-Through-Mirror/dp/B017ONH3EG)
 - Raspberry Pi Compatible Camera 
 - Raspberry Pi Compatible Microphone 
 - 1920 x 1080 Resolution Monitor
 - 8 GB or Larger microSD Storage
 - 3.5mm Audio Cable
 - Keyboard
 - Mouse
 
#### Software 
 - NPM (Additional dependencies will be installed using NPM)
 - Git (Additional software will be installed using Git)

#### Optional 

 - Google Developers API Key
 - NewsAPI API Key
 - Open Weather Map API Key
 - Import.io API Key
 
### Usage
In the `smart-mirror-electron` directory, run the following command to start the Smart Mirror.
```bash
npm start
```
##### Gestures
- If the user is not signed in and...
    - **A five is detected the mirror** will attempt to detect a face.
    - **A two is detected the mirror** will prompt the user to capture 5 pictures
    - The photo is captured by showing a five
- If the user is signed in...
    - The user is logged out by showing a zero

### Installation
If you are cloning this project with only software requirements, skip to step 3 in the Software Setup section.

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
4. Clone the `smart-mirror-electron` repository and `cd` into the directory. This repository contains the src files for the Electron packaged Angular 6 web application. Detailed installation and usage notes can be accessed [here](https://github.com/kevintrankt/smart-mirror-electron).
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
7. Copy the `config.json` file generated from the Smart Mirror Configurator to `/smart-mirror-electron/src/assets/`.
8. Verify your installation by running the following command in the terminal. If everything worked perfectly, you should now have a functioning Smart Mirror! 
You can test logging into each account by typing numbers associated to the user and pressing space to logout. 
	```bash
	npm start
	```

*The following steps will cover how to integrate voice control with Amazon Alexa with the Smart Mirror. These steps are optional if you do not meet the hardware requirements.*
##### Amazon Alexa
1. Run ` sudo apt-get upgrade ` to get the necessary updates on terminal in the Raspberry Pi
2. Get necessary files:
	```bash
	wget https://raw.githubusercontent.com/juliebee1024/smart-mirror-alexa/master/pi.sh \
	wget https://raw.githubusercontent.com/juliebee1024/smart-mirror-alexa/master/setup.sh
	```
3. Create a config file:
	```bash
	sudo nano config.txt
	```
4. Copy and paste into the config file:
	```
	#NOTE: The Device Serial Number can be any unique number
	DEVICE_SERIAL_NUMBER=""
	CLIENT_ID=""
	PRODUCT_ID=""
	```
5. Open a web browser and login to Amazon Developer (https://developer.amazon.com/avs/home.html#/avs/home) and click on your product
6. Scroll down and copy & paste the **Product ID** into config.txt
7. Click on "**Security Profile**" under the "Product Details" tab
8. Scroll down and click on "**Other devices and platforms**"
9. Copy & paste the **Client ID** into config.txt
10. Enter any number (i.e. 123456) as the **Device Serial Number**
11. Ctrl-o and enter to save
12. Ctrl-x to exit
13. Follow https://developer.amazon.com/docs/alexa-voice-service/input-avs-credentials.html starting at "**Download your credentials**" to get the config.json file
14. In terminal, run the install script
	```bash
	cd /home/pi
	sudo bash setup.sh config.txt
	```
15. Follow https://developer.amazon.com/docs/alexa-voice-service/build-the-avs-device-sdk.html for the rest of the installation process

*Referenced from https://github.com/carolinedunn/Alexa-RPi-AutoStart*

*****The following steps will cover how to integrate facial recognition with OpenCV with the Smart Mirror. These steps are optional if you do not meet the hardware requirements.*****

#### Expand Filesystem (Optional)
If using brand new/default Raspbian Stretch, make space on microSD card using following instructions. 
```
sudo apt-get purge wolfram-engine
sudo apt-get purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```

#### Update Pi 
```
sudo apt-get update
sudo apt-get upgrade
sudo rpi-update
```
#### Install Dependencies 
```
sudo apt-get install build-essential cmake pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
sudo apt-get install libgtk2.0-dev libgtk-3-dev
sudo apt-get install libatlas-base-dev gfortran
```

#### Setup Python3 Development and pip Tools 
```
sudo apt-get install python3 python3-setuptools python3-dev
```
```
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
```
#### Download OpenCV 3.4.1 and OpenCV-contrib 
```
cd ~
wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.4.1.zip
wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.4.1.zip
unzip opencv.zip
unzip opencv_contrib.zip
```
#### Install Python Packages
```
sudo pip3 install numpy
sudo pip3 install imutils
sudo pip3 install sklearn
```
#### Build OpenCV 
```
cd ~/opencv-3.4.1/
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.4.1/modules \
      -D ENABLE_PRECOMPILED_HEADERS=OFF \
      -D BUILD_EXAMPLES=ON ..
```
#### Increase Swap Space 
Increase swap space from 100MB to 1024MB to facilitate compilation of OpenCV and prevent crashing on the Pi using nano editor. 
```
sudo nano -w /etc/dphys-swapfile 
```
Scroll down to "**CONF_SWAPSIZE**" and change value to 1024. Save file by using "**CTRL+O**" and then exit nano with "**CTRL+X**". 

Activate new swap space: 
```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```
#### Compile and Install OpenCV 
This process may take 2 to 3 hours. The Pi will get hot in the process, so be sure to provide cooling to the Pi. 
```
make -j4
```
Install OpenCV 
```
sudo make install
sudo ldconfig
```

#### Test Successful OpenCV Installation 
Open Python3 interpreter and enter the following to test successful installation. 
```
import cv2
cv2.__version__
```
The output should be '3.4.1'

#### Revert Swap Size and Free Up Space 
Similarly to increasing swap size, use the same commands to revert the swap size back to 100MB. Once reverted, restart the service. 
```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```
Remove the downloaded zip files to free up space. 
```
cd ~
rm -rf opencv.zip opencv_contrib.zip
```

### Smart Mirror Config
The Smart Mirror is personalized for users using the [Smart Mirror Configurator](https://kevintrankt.com/smart-mirror-config/). This tool allows you to create or modify a config file to include any external API keys, add or remove users, and to personalize the Smart Mirror for each user. This section will cover how to create a config file using the configurator.


#### Adding/Removing a User
To add a user click on the User icon in the top left. To remove a user, click the X to the right of each user field.

#### Saving Your Config
There are two ways you can save your config: saving or copying to clipboard. To save the config, click the Save icon in the top right to save a `config.json` file. Move this file to `smart-mirror-electron/src/assets/` to change the settings for the Smart Mirror. To copy the config to your clipboard, click the Copy icon in the top right. You can now paste replace the contents of `smart-mirror-electron/src/assets/config.json` with the contents in your clipboard. 

#### Loading an Existing Config
You can load an existing config by choosing a file. This will populate all the fields with the information from your existing `config.json` file 

#### API Keys
Some widgets will require specific API keys to grab data properly. To get proper API keys, click on each API Key section label and follow the signup process to get a unique API key.

#### Users
Each user has their own personal settings for the Smart Mirror. The Smart Mirror supports up to 10 users. Each user has an ID starting from 0 up to 9. When setting up a user, you can optionally set a name and a login message.

#### Widget Layout
There are 8 possible locations for a widget to exist on the Smart Mirror. The Smart Mirror is divided into a grid of 3x3 where the outer cells are used to place widgets.

#### Widgets
Widgets are personalized for each user. Depending on the widget, certain API keys and settings are required.

The following subsection will cover the process of setting up each provided widget.

##### Clock
![clock widget](https://i.imgur.com/cMIsI26.png)

The clock widget simply shows the time and date. This widget has no dependencies and can be placed anywhere on the Smart Mirror.

##### Weather
![weather widget](https://i.imgur.com/hFbQuTI.png)

The weather widget shows the current temperature and weather for a location. This widget requires a Zip Code and the Weather API key, and it can be placed anywhere on the Smart Mirror.

##### News
![news widget](https://i.imgur.com/2C2miA9.png)

The news widget shows popular news headlines with short descriptions if possible. This widget requires the News API key and should only be placed on the left or right side of the Smart Mirror.

##### Agenda
![agenda widget](https://i.imgur.com/l5zOnfx.png)

The agenda widget shows your events for the day in an agenda view from Google Calendar. This widget requires an Import.io API key, the email of the Google Calendar, and it can be placed anywhere on the Smart Mirror. 

##### Subreddit
![subreddit widget](https://i.imgur.com/EAgkZoy.png)

The subreddit widget displays the Hot posts on your selected subreddit. This widget requires a subreddit, and it should only be placed on the left or right side of the Smart Mirror.
##### Destination
![destination widget](https://i.imgur.com/QQ1ABKT.png)

The destination widget displays a live estimated travel time to a location using Google Maps. This widget requires a Google Maps route URL, a destination name, and an Import.io API key, and it can be placed anywhere on the Smart Mirror. To get a Google Maps route URL, you can go to https://maps.google.com, enter a starting and ending destination, and copying the URL.

##### Forecast
![forecast widget](https://i.imgur.com/xpVrMLy.png)

The forecast widget displays the upcoming 5 day forecast. This widget requires the Weather API key and a zip code, and the widget should be placed on either the left or right side of the Smart Mirror.
### Making a Custom Widget
For this example, we'll be going through the process of making a vertical forecast widget using Open Weather Map's forecast API: https://openweathermap.org/forecast5.

Assuming you created a Smart Mirror config file, you should already have the API key for Open Weather Map.

1. Add the following function to `smart-mirror-electron/src/app/data.service.ts`
	```javascript
	  getForecast() {
	    const location = this.activeUser.location;
	    const url = `http://api.openweathermap.org/data/2.5/forecast?zip=${location},us&units=imperial
	      &APPID=${this.config.apiKeys.weather}`;
	    return this.http.get(url);
	  }
	  ```
	  `data.service.ts` handles all HTTP requests and loads the `config.json` file from `smart-mirror-electron/src/assets/`. This function grabs the location for the active user and the weather API key from `config.json`. The `url` variable is the API call from Open Weather Map's 5 day forecast API.
	  
2. Run the following command in terminal to create a new Angular component.
	```bash
	ng g c forecast
	```
	This will create a new folder `forecast` with Angular component file and updates `app.module.ts` to include the new component. 
3. In the newly created folder, replace the content in `forecast.component.ts` with the following code.
	```typescript
	import { Component, OnInit } from '@angular/core';
	import { DataService } from '../data.service';

	@Component({
	  selector: 'app-forecast',
	  templateUrl: './forecast.component.html',
	  styleUrls: ['./forecast.component.scss']
	})
	export class ForecastComponent implements OnInit {
	  forecast;

	  constructor(private data: DataService) {}
	  ngOnInit() {
	    this.initializeWidget(60);
	  }

	  /*-------------------------------------------------------------------------|
	  | Initializes the widget to populate the DOM with data from data.service.  |
	  | -----------------------------------------------------------------------  |
	  | @param {number} reload Number of seconds before the widget reloads       |
	  |-------------------------------------------------------------------------*/
	  initializeWidget(reload) {
	    this.getForecast();
	    setInterval(() => {
	      this.getForecast();
	    }, reload * 1000);
	  }

	  /*-------------------------------------------------------------------------|
	  | Fetches data from API by subscribing to data.service methods             |
	  |-------------------------------------------------------------------------*/
	  getForecast() {
	    this.data.getForecast().subscribe(
	      data => {
	        this.forecast = data;
	      },
	      error => console.log(error),
	      () => {
	        console.log(this.forecast);
	      }
	    );
	  }
	}
	```
	This class does 3 essential things: fetches data, updates parameters, and reloads data. To fetch data, the `getForecast()` method is called to access the `getForecast()` method in `data.service.ts`. The `forecast` parameter will hold the data received from the API call. The class is currently written to simply console.log the data received from the API call.
	
	The `initializeWidget(reload)` method fetches the data and asynchronously fetches data every x seconds where x = reload. This method is called in `ngOnInit` with an update time of 60 seconds.
4. Replace the content in `forecast.component.html` with the following code.
	```html
	<div ngDraggable ngResizable class="widget-body">widget loaded properly!</div>
	```
	At the moment, this component will only show the "widget loaded properly!". Once you verify that the data is being extracted properly, you can modify this file using two way binding to change how the widget looks.
5. Replace the content in `forecast.component.css` with the following code.
	```css
	.widget-body {
	  width: auto;
	  text-align: center;
	}
	```
	Similarly to step 4, you will modify this once you have verified that everything is working.
6. Navigate to `smart-mirror-electron/src/app/components/home.component.html` and add the following line under Widget Set 1 and Widget Set 2
	```html
	<app-forecast *ngIf="widget == 6"></app-forecast>
	```
	`home.component` is the first component that is loaded when the Electron application starts. Based on the user's config file, `home.component` is altered to match the layout in `config.json`.
	
	Widget Set 1 are the widgets in the top left, top right, bottom right, and bottom left. Widget Set 2 are the widgets in the top, right, bottom, left.

	This line checks to see if the user has included widget #6 in a certain location in their `config.json`, and it populates `home.component` to include that widget.
7. To confirm that the widget works, open `smart-mirror-electron/src/assets/config.json` and add the number 6 anywhere in the widgets arrays. For this example, we're placing this on the right of the Smart Mirror.
	```json
	"widgets2":  ["0",  "6",  "-1",  "3"]
	```
8. On the Smart Mirror, login to your user and verify that the widget is showing up on the screen, and verify that data is being logged in the Developer Console. If you want to add this widget to the Smart Home Configurator, visit the [smart-mirror-config](https://github.com/kevintrankt/smart-mirror-config) repository and add the widget to `widgets` in `scripts.js`.

If you are curious as to how we design the widget, you can view the component [here](https://github.com/kevintrankt/smart-mirror-electron/tree/master/src/app/forecast).

### Configuring and Running Alexa
Please refer to [Smart Mirror Alexa README](https://github.com/juliebee1024/smart-mirror-alexa/blob/master/README.md) for how to run Alexa, add wake sound and notification of bootup, autobooting Alexa, and customizing Alexa.
