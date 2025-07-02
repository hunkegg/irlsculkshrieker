---
title: "IRL Sculk Shrieker"
author: "egg_splats"
description: "The Minecraft sculk shrieker... In real life! (warden sold seperately)"
created_at: "2025-06-28"
---

promised myself that i'd make a slot machine for my next custom project but yet again another idea got the better of me 🥀 <br/>
huge inspiration from [@aron huang's Minecraft Compass](https://hackclub.slack.com/archives/C08S22XRYMU/p1750910065012999) and [@danieliscrazy's Minecraft Jukebox](https://hackclub.slack.com/archives/C08S22XRYMU/p1750910065012999) <br/>

(dates are in mm/dd/yy again because 🦅)

## 6/28/25 - Figuring out electronics and design (a.k.a. da plan)
Today I made the repo for this project, and started to plan out the internals of this sculk shrieker. <br/>

The [sculk shrieker](https://minecraft.wiki/w/Sculk_Shrieker) is a block in Minecraft that *shrieks* when activated by a sculk sensor, which essentially is a microphone in our case since they are activated by sound. <br/>
I plan to recreate this effect by having a microcontroller receive input via a microphone module, then play the game audio from a speaker + SD card. I could also add some extra lighting via LEDs or electroluminescent wire to mimic the emmissive textures/animations found on the sides and top of the sculk shrieker. <br/>

![image](https://github.com/user-attachments/assets/04f94c4d-943a-4017-892e-98b933ef33b3)

Once I got the general idea down, I started to do research on the parts. I found a blog page by [DroneBot Workshop](https://dronebotworkshop.com/esp32-i2s/) which detailed much of the electronics and theory for the project, covering i2c and how to use the INMP441 microphone module and MAX98357A amp. I will be basing most of my research around this, but also making my own code for the sound detection and shrieker sound. <br/>

From the blog post, I made up a quick BOM and looked on Aliexpress to find the parts I needed. As usual, the parts were relatively cheap, with most of the modules totaling to about 13 USD. <br/>

time spent: 2 hours

## 7/1/25 - more planning (the looks and internals)
locking in imminent <br/>

While I have most of the parts planned out, I still need to plan out how the shrieker will look like. <br/>
The shrieker is a block with emmisive (glowing) textures, with an animated topside of two "souls" orbiting around the center. The block is made up of a half block (8 pixels tall) and four jaws that extend upwards. <br/>

![shrieker](https://github.com/user-attachments/assets/9508c61b-a115-4367-9f56-786c3e763c72)

I could place the speaker in the middle of the block, with a circular PCB of RGB lights or neopixels to simulate the souls moving around in the shrieker. All of the other components could be stored inside of the block and out of sight, while the microphone can be tucked away under or near one of the jaws to allow it to listen but also to be hidden.

![plannin](https://github.com/user-attachments/assets/3c7bc64b-b689-4cce-92a1-25c75315e4db)

Since most of the parts are on different breakout boards/modules, a pcb to hold everything *may* be overkill. I could instead try to design the 3D printed case to fit the modules, with the only PCB being to hold the animated RGB lights. <br/>

![diagram](https://github.com/user-attachments/assets/151638f6-ba67-4c54-9d3c-84ffa42fc750)

For the CAD, I plan to keep with the 16 x 16 pixel style of Minecraft, making the dimensions of my sculk shrieker 64mm xx 64mm with each pixel being 4mm wide. In game, the jaws actually *have* no thickness, so to keep consistency, I will also be making them a pixel thick (4mm thick). <br/>
To help with painting, I will 3D print the white sections separately from the dark blue/black sections and gluing them together after coloring. In all, this should result in the bottom half, four white corners, and the jaws. <br/>
I could also design the jaws to "socket" into the rest of the build for ease of assembly by making an indent inside the half-block portion and extending the jaws by a small amount, similar to how I designed the shells in my Engipad. <br/>

I also thought about some extra features to *really* set in the details of the sculk shrieker, for example:
* An integrated accelerometer to play the place/break sounds when it is picked up or put down
* A button or some type of sensor to detect if something has touched the black part of the top of the shrieker, since shriekers can also be activated if the player walks on top of it
* Engravings in the jaws/block that follow the texture of the in-game shrieker, such as the darker lines in the jaws standing in for grooves in them

time spent: 2 hours <br/>





