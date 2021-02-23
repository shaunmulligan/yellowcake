---
template: SinglePost
title: Working MVP
status: Published
date: 2021-02-23
featuredImage: https://ucarecdn.com/4fa841aa-5fe1-46b7-89e5-461d1fe8c5b5/-/crop/1089x558/0,0/-/preview/
excerpt: An update on my Zwiftendo project. Showing off the working MVP with a demo.
categories:
  - category: zwiftendo
---
Finally got around to putting the Minimal Viable Product (MVP) together for the Zwiftendo to test the features out and see how the UX feels with the buttons and blackberry-esque trackball... Its not beautiful but it works! 

You can see the hackery below:

![](https://ucarecdn.com/b4135fb5-0100-4155-8cf5-1613df145aee/-/crop/2355x1141/217,388/-/preview/)

### The Current State:

In its current form, a successfully paired Zwiftendo will launch both Zwift and Spotify (primed with a playlist of your choice) when you click the "Start" button. This is currently done via a [macOS automator script](https://github.com/shaunmulligan/zwiftendo/blob/master/zwiftendo-launcher) I wrote which listens for a specific key combination from the Zwiftendo BLE keyboard. We can also control the media keys for `PLAY/PAUSE` and `SKIP` track on Spotify. I also wired up two other buttons, one is setup to be able to easily trigger a `powerUP` in Zwift. I figure this will be pretty useful when doing races. The second allows one to skip a block in a structured workout session. Hopefully won't have to use this one too many times :)

The blackberry style trackball covers a few features. The central RGB led is lit green when the device first powers up and will transition to blue once a bluetooth connection is esstablished with the laptop. The central led is also a button which acts as the "Enter/Return" key to allow us to select things and start riding. Obviously the directional rolling of the trackball maps to arrow keys and allows us to control the menu items in-game. You can checkout how this all works in the short demo ride below:

<iframe width="560" height="315" src="https://www.youtube.com/embed/Sh4jULJsBNU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Finally, the whole thing is powered from a 3.7v 1200mah LiPo battery and its set to light up the nrf52480 onboard neopixel RGB led red when the battery level drops lower than 15%. I also have it periodically updating the bluetooth battery level profile. However, sadly for some reason macOS doesn't appear to display that battery level for most of my BLE devices. The only one that has a reliable battery level indicator is my apple keyboard. So perhaps they are doing something non-standard there...

### Issues and UX:

If you watched the demo you might have noticed a few issues. One being that my gears sound a bit janky and yes I definitely need to put some time into sorting that. You also might have noticed that some of the button presses were not detected, I think this is because currently its programmed to be just a dumb loop, scanning through all the buttons each time and then sleeping for a bit of time. So if you happen to press during the sleep portion or while other buttons are being checked, then you are shit out of luck!

Another problem UX wise is with the trackball. It's much more clumsy and difficult to use than I expected. So even though it looks cool and I love the central RGB led, I'm gonna try replace it with something more akin to a thumb controller. 

Finally, I also seem to have some sort of heisenbug with the battery level detection and indication. It's a bit of a pain to try debug because it only happens when the battery is low and the serial cable is unplugged (so that its not charging). Some part of that detection occasionally fails and throws the Zwiftendo into a boot loop. I haven't managed to get any logs yet but might have to find a way to persist the logs to the device so I can debug it since I can't use the serial output.

### What's Next:

So up next, I am gonna switch out the sketchy button setup and trackball for this much neater [Adafruit Joy Feather](https://www.adafruit.com/product/3632) (pictured below). It looks like a great piece of kit. Unfortunately it doesn't seem to offer the ability to click the central control pad, so I might have to move the "Enter/Return" button to one of the other buttons. I need to play around with it a bit and figure out what will be the most intuitive. At the same time we will also try improve the input detection, maybe using interrupts or some kind of concurrency to ensure we have the button presses on a tighter loop so as to not miss anything.

![](https://ucarecdn.com/7f3e96e6-e89f-4547-994b-4507b141329f/ "Adafruit Joy Feather")

I'm also going to wire a little slide switch into the power line of the battery to allow powering down the device. Once that is all fully tested and we are happy with the new UX, I'll start putting together the design for the 3D printed enclosure. The plan is to have small controller box that is mounted out the front of my Garmin head unit and clips into the underside of the Garmin mount. However, there is still a bit to explore design wise on that side of things...