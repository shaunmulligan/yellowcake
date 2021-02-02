---
template: SinglePost
title: Zwiftendo - A bike mounted zwift controller
status: Published
date: 2021-01-20
featuredImage: https://ucarecdn.com/655e48a7-593c-42ef-ab68-94a680938348/-/crop/1718x1829/14,259/-/preview/-/enhance/75/
excerpt: The first post in a series detailing building Zwiftendo, a handle bar
  mounted zwift keyboard.
categories:
  - category: zwiftendo
---
I started [Zwifting](https://zwift.com/) about a year ago and like a bunch of people became obsessed with smashing virtual miles surrounded by dinosaurs. However I never would have guessed how sweat drenched my tiny office setup would get while pushing mega-wattage. Having already ruined one mechanical keyboard I decided to over engineer a solution. This blog series is the story of building the Zwiftendo.

![](https://ucarecdn.com/c099448d-a5af-4a28-947f-99272e74a320/)

Zwiftendo: Zwift + Nintendo ( I know! super clever) is the small Zwift remote that can be attached to your head unit. The idea being that if I had a small bar mounted controller to full control my laptop and the things I needed to do while riding, then I could pull my bike further way and no longer have my precious laptop and keyboard in the splash zone. When riding indoors I'm most often doing structured workouts or races and always have Spotify pumping tunes or a very "highbrow" podcast. So functionally the Zwiftendo needs to be able to:

* Simulate arrow keys to control the Zwift in game menu, probably using a ["blackberry" like trackball input](https://shop.pimoroni.com/products/trackball-breakout). 
* Control laptop media buttons. Play/pause, skip to next track.
* Run from battery power for 8+ hours ( just incase I ever want to be on Zwift that long :P ).
* Easily mountable on a Garmin like head unit mount.
* A way to cycle through zwift rider views.
* A way to increase or decrease FTP bias during workout mode ( not sure yet if this will be possible ).
* A simple way to trigger a power-up during a race.
* Start up Zwift and a default Spotify playlist on my laptop when it starts up.
* Be hella sweat proof!

## Part 1: Picking the right tools

Given the fact that I want this to be able to run for hours on battery and be mounted on my handlebars in someway, I need to find a micro-controller. I also want it to be fully wireless because wires are annoying (marginally more than keeping things charged). So we are looking for some kind of bluetooth enabled MCU. Luckily I have a bunch of these lying around from projects that never happened.

![](https://ucarecdn.com/9ec8af1c-cd4d-44cc-9a0a-ad18f22c6d51/-/preview/-/rotate/270/)

In the pile we had 3 EPS32 base devices namely the [Adafruit Huzzah32](https://www.adafruit.com/product/3405), the [TinyPICO](https://www.tinypico.com/) and the [LilyGo T-Call SIM800](https://github.com/Xinyuan-LilyGO/LilyGo-T-Call-SIM800). We also had the older [Adafruit feather HUZZAH](https://www.adafruit.com/product/2821) based on the ESP8266, an [Adafruit Feather nRF52840 Express](https://www.adafruit.com/product/4062)  and finally a [Particle.io Xenon](https://docs.particle.io/xenon/). All of them are super capable and fun to build with but for this particular project one of the focuses was to learn a bit about [micropython](http://micropython.org/). So I started out hacking on the Huzzah32 as it has some of the best micropython support. 

The first thing to figure out was how to control a laptop's input from the microcontroller. Since we have bluetooth and the BLE specifications have a nifty HID profile, it was just a "simple" matter of getting that to work in micropython. After some quick googling I found myself on a great BLE HID example on the micropython repo itself: https://github.com/micropython/micropython/pull/6559 

At this point I thought it would be plain sailing. Unfortunately after some testing it turns out BLE is not created equal on all platforms and while I could get macOS to recognise and pair with my new ESP32 powered keyboard, it was incredibly unstable and I couldn't even get a simple character key press sent over to the device. So back to square one :(

After another marathon bout of googling I found that [circuitPython](https://circuitpython.org/) (an Adafruit fork of micropython) had a super nice looking BLE library. More importantly, many people on the forums had built HID devices on top of this and it seems to even work with macOS. Winner Winner, Chicken Dinner! or so I thought. It turns out circuitPython doesn't support the ESP32, something about it not having a native USB implementation for the UF2 bootloader they use to expose the device as a USB drive.

In any case, this lead me to switch to using the nRF52840 Express microcontroller which fortuitously might even be lower power than the Huzza32. So after getting familiar with the circuitPython dev process and ripping apart some of the BLE HID examples, I now have a fully working bluetooth HID implementation. If you are interested you can see the somewhat janky code here: https://github.com/shaunmulligan/zwiftendo .

![](https://ucarecdn.com/7d1b6d1e-b780-4543-8fdc-2b4aff170592/)