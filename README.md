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

 - [smart-mirror-electron](https://github.com/kevintrankt/smart-mirror-electron)
 - [smart-mirror-config](https://github.com/kevintrankt/smart-mirror-config)
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

The following steps will cover how to integrate facial recognition with OpenCV and voice control with Amazon Alexa with the Smart Mirror.

8. TODO: Add OpenCV README
9. TODO: Add Amazon Alexa README
  
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
