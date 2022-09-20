---
template: SinglePost
title: HypeCycle - An over engineered Cycling Computer
status: Published
date: 2022-09-20
excerpt: I love all the tech that goes into products like the Garmin 530 and
  Hammerhead Karoo, so I decided to try build my own one using a raspberry pi.
  How hard could it be?
categories:
  - category: hypeCycle
---
I love all the tech that goes into products like the Garmin 530 and Hammerhead Karoo, so I decided to try build my own one using a raspberry pi. How hard could it be?

T﻿o be clear, this project is purely for learning and fun. I don't expect to ever produce something as complete or functional as the commercial products but it will be interesting to see how far one can get with off the shelf parts and a 3D printer :D

### Proposed HypeCycle Feature Set:

* Crisp high density 4” touch screen: 800x480 pixels (~235 PPI) Hyperpixel
* Bluetooth sensor compatibility (HR and Power)
* Front facing Camera with ability to record
* Fast fix (possibly assisted-GPS) or at least coincell 
* Automatic upload to strava when in wifi
* High accuracy altimeter and ambient temperature
* Controllable Front facing LED lights for visibility
* Quadcore rpi zero 2 W at its heart
* 1200mah high capacity Lipo battery
* 100% opensource
* 3 physical buttons
* Integrated into bar mount

### Hard Maybes

* Wireless charging
* A﻿NT+ support
* Haptic buzzer you can feel in the handlebars
* Ability to bluetooth tether to phone for internet access.
* I﻿ncident detection via onboard accelerometer

## C﻿urrent Hardware Design

![](https://ucarecdn.com/e1c1f170-b3c5-4208-a1ef-a154286b5aec/ "Current Hardware Config")

T﻿he current design consists of:

\-﻿ Raspberry Pi zero 2 W

\-﻿ [Hyperpixel LCD](https://shop.pimoroni.com/products/hyperpixel-4?variant=12569485443155) - 400x800 high density display

\-﻿ [Adafruit MiniGPS PA110D](https://www.adafruit.com/product/4415)

\-﻿ [Adafruit BMP388](https://www.adafruit.com/product/3966) - Accurate altimetry and temperature measurement 

\-﻿ [Pimoroni IO expander](https://shop.pimoroni.com/products/io-expander?variant=32005993136211) - enables use of i2c to expand the number of available GPIOs we can use as our hyperpixel screen uses all of them :/

\-﻿ [DFrobot Power Boost & Charger Module](https://www.dfrobot.com/product-1613.html) - Allows 2.5A of current to power our full device, even during peak usage moments like getting a GPS fix.