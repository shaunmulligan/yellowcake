---
template: SinglePost
title: Working MVP
status: Published
date: 2021-02-23
featuredImage: https://ucarecdn.com/4fa841aa-5fe1-46b7-89e5-461d1fe8c5b5/-/crop/1089x558/0,0/-/preview/
excerpt: An update on my Zwiftendo project. Showing off the working MVP with a demo.
---
Finally got around to putting the Minimal Viable Product (MVP) together for the Zwiftendo to test the features out and see how the UX feels with the buttons and blackberry-esque trackball. Its not beautiful but it works! You can see the hackery below:

![](https://ucarecdn.com/b4135fb5-0100-4155-8cf5-1613df145aee/-/crop/2355x1141/217,388/-/preview/)

### The Current State:

In its current form, a successfully paired Zwiftendo will launch both Zwift and Spotify (primed with a playlist of your choice) when you click the "Start" button. This is currently done via [macOS automator script](https://github.com/shaunmulligan/zwiftendo/blob/master/zwiftendo-launcher) I wrote which listens for a specific key combination from the Zwiftendo BLE keyboard. We can also control the media keys for play/pause and skip to next track on Spotify. I also wired up two other buttons, one is setup to be able to easily trigger a powerUP in Zwift. I figure this will be pretty useful when doing races. The second allows one to skip a block in a structured workout session. Hopefully won't have to use this one too many times :)

The blackberry style trackball covers a few features. The central RGB led is illuminated green when the device first powers up and will transition to blue once a bluetooth connection is esstablished with the laptop. The central led is also a button which acts as the "Enter/Return" key to allow us to select things and start riding. Obviously the directional rolling of the trackball maps to arrow keys and allows us to control the menu items in-game. You can checkout how this all works in the short demo ride below:

<iframe width="560" height="315" src="https://www.youtube.com/embed/Sh4jULJsBNU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Finally, the whole thing is powered from a 3.7v 1200mah LiPo battery and its setup to light up the nrf52480 onboard neopixel RGB led red when the battery level drops lower than 15%. I also have it periodically updating the bluetooth battery level profile. However, sadly for some reason the macOS doesn't appear to display that battery level for most of my BLE devices. The only one that has a reliable battery level indicator is my apple keyboard. So perhaps they are doing something non-standard there...

### Issues and UX:

### What's Next: