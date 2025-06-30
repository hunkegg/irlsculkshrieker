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
I plan to recreate this effect by having a microcontroller receive input via a microphone module, then play the game audio from a speaker + SD card. 
