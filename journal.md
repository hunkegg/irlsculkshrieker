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

Once I got the general idea down, I started to do research on the parts. I found a blog page by [DroneBot Workshop](https://dronebotworkshop.com/esp32-i2s/) which detailed much of the electronics and theory for the project, covering i2c and how to use the INMP441 microphone module and MAX98357A amp. I will be basing most of my research around this, but also making my own code for the sound detection and shrieker sound. <br/>

From the blog post, I made up a quick BOM and looked on Aliexpress to find the parts I needed. As usual, the parts were relatively cheap, with most of the modules totaling to about 13 USD. <br/>

time spent: 2 hours

## 7/1/25 - more planning
locking in rn <br/>

