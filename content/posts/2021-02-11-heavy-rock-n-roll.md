---
template: SinglePost
title: Indoor Rock n' Roll
status: Published
date: 2021-02-11
featuredImage: https://ucarecdn.com/ec6cb5fe-6411-4422-a83d-9d8a726eb996/-/crop/351x151/0,0/-/preview/
excerpt: Building a "smart" rocker plate for my indoor cycling setup.
categories:
  - category: Ultimate Cycling Cave
meta:
  title: Smart Rocker Plate
---
Since I plan to be logging a lot of indoor mileage, one of the things I really want to improve with my projects here is my "pain cave". Currently its not the neatest setup and doubles as my office. So one of the first things on my hit list was making my longer indoor rides more comfortable. 

The nether regions always tend to lose their will to live after about 2 hours indoors. I think thats because it's not as comfortable to do efforts out of the saddle. So the plan is to have a rocker plate setup that makes me more confident to get out of the saddle on those longer rides. 

![](https://ucarecdn.com/b3f1af30-4cc9-4034-b2fe-330ee2fc032b/)

Of course I could easily buy one of these beasts (see above), professionally and ready made, but there is no fun in that. Handily there is a healthy [community of people](https://www.facebook.com/groups/415329188897706/) building their own and open sourcing the designs. So that was my first stop. It seems when it comes to DIY rockerplates there are two core designs. The first being based on rubber isolation mounts. Basically you have two pieces of plywood balanced on a spine of rubbery spacers about 7cm tall. The rubber isolation mounts allow you to rock side to side and then most designs use blow up mini dodge balls on either side to vary the amount of sway. They also obviously prevent you from hitting the bottom plate as well. This design is a bit simpler to build but has the downside of only having 1 degree of motion (side-to-side).

The second option, which I want to build, uses linear rod bearings to enable both side-to-side and forward-backwards motion. [Andrew Grabbs](https://www.andrewgrabbs.com/interests/cycling/indoor-trainer-rocker-plate/) has an awesome design and explainer video for building one. So I plan to follow the fundamentals from there. I already managed to source some cheap linear rod bearings and mini dodge balls (see below). As the project progresses I will try create a list of parts and where to order them.

![](https://ucarecdn.com/7ed71bf6-be7f-40d1-afa2-24d4ec569999/-/preview/-/enhance/50/)

However, in this day and age, we can't just build a plain rocker plate. So in the spirit of over-engineering I want to try add some smarts to my rocknroller. The first thing I plan to add is the ability to automatically weigh the rider and update their Zwift profile. For this I have 4 load cells and the [HX711 load cell amplifier](https://www.sparkfun.com/products/13879) which should allow me to weigh even the most well fed rider. I'm not 100% sure this will be possible to do as Zwift doesn't have a developer friendly API, but I'm hoping I can find some workaround. At the very worst I think it might be possible to use the Zwift <-> Fitbit integration and patch the weight updates to the Fitbit API, but we will have to see how that goes. I also need to work out the UX for the weighing functionality. Not sure yet if I want an explicit button or for it to try do it automatically. It also might be pretty cool to have the rockerplate measure my weight lost from the start of a ride to the end. That way I would get some idea of my sweat loss while riding as a specific temperature.

The second feature is in-game stearing. A while back [Zwift FutureWorks](https://www.zwift.com/news/22056-futureworks?__znl=en-eu) added stearing in-game with the use of something like the [Elite Sterzo](https://www.elite-it.com/en/products/home-trainers/trainers-accessories/sterzo-smart). Some smart dude name [Andy](https://github.com/fiveohhh) reverse engineered the bluetooth protocol and opensourced his work here: [zwift-steerer](https://github.com/fiveohhh/zwift-steerer) . So I want to see if I can use his work and integrate it nicely into my rocker plate in some way. 

This should be a fairly fun project with lots of hands-on building work. Potentially somethings won't work out but at the very least I should end up with a semi rideable rockerplate. First things first though, I need to order myself a jigsaw and bench to do some of this wood working. Wish me luck!