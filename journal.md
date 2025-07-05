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

<img width="1440" alt="image" src="https://github.com/user-attachments/assets/89de6f86-02f5-4493-adea-a85e6943370d" />

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
* Additional functionality as an alarm system by having the esp32 send out a message if the microphone is activated

time spent: 2 hours <br/>

## 7/3/25 - cadding and cool colors wow
Today I started work on making the CAD for the shrieker. <br/>
I started off making the half block of the shrieker and then the jaws, but soon ran into the issue of trying to extrude the jaws since Minecraft actually *doesn't* have any thickness for them. <br/>
To save myself on the hassle of going back into sketches and changing dimensions, I made a custom parameter in Fusion to automatically adjust the thickness of the jaws named JawThickness and set it to multiple thicknesses. <br/>

<img width="799" alt="image" src="https://github.com/user-attachments/assets/5d482335-ab93-47e5-9da9-323437007d26" /> <br/>

I at first wanted to go 2.5mm thick to stay as true to the game as possible (thin), but I also found 4mm to be appealing due to pixel consistency + making the jaws seem *slightly* taller. <br/>
I was pretty stuck on this decision, so I asked on the Slack and some friends and they all answered 4mm so I'll be doing that for the thickness. <br/>

After that, I went around the block, adding in extra details found on the texture of the sculk shrieker. I *could* have painted these in after printing, but I suck at painting and found the surface in Fusion to be really *flat and boring* without the details or coloring. <br/>
Furthermore, as far as I know, you can't get picture textures onto surfaces in Fusion without abusing the Decal tool a bunch, which would make the renders look incredibly bad lmao <br/>

<img width="1117" alt="image" src="https://github.com/user-attachments/assets/8d034ef8-7d0d-4429-bbeb-af74182be116" /> <br/>
> forgot to take pictures while modeling but you get the idea 

Once I did that, I had to split the main half-block into two parts in order to fit the components inside of the block. While I could've gone with a basic cut across the middle, I figured that I should make the two lids in the shape of the sculk that grows on top of the block. <br/>
This was done because:
1. The two halves can interlock more easily, allowing for better alignment
2. The shaped halves make painting much easier since I can isolate the darker colors of the block to the lighter blue of the sculk
3. The corners of the top half being lower allows me to use shorter screws through the bottom
4. The halves can be colored differently when rendering
> it also looks REALLY cool when i split the block into two <br/>

<img width="500" alt="image" src="https://github.com/user-attachments/assets/0053d59a-c521-403d-85d5-c2a3ba2a62a4" /> <br/>

After that, it was finally time to color. <br/>
I found the texture for the block on the [Minecraft Wiki](https://minecraft.wiki/w/List_of_block_textures), and quickly realized that this specific block had the one of the most EGREGIOUS and EVIL gradients in the ENTIRETY of Minecraft, going from the ivory white of the jaws to a dark blue and black, making the whole model hard to color accurately <br/>
> remember when i said that i made the extra details and textures because you can't get picture textures in Fusion? this is why lmfao <br/>
> if i made the entire half block as one, it would look like a singular color (and thus look like shit)

Anyways, I went back into drawing software, getting the colors I wanted and copying the hex codes to Fusion's appearance tool. I had to make another color for the sculk on the spot when coloring the two sculk halves, but we got there <br/>

<img width="1306" alt="image" src="https://github.com/user-attachments/assets/8b92dae4-84b4-4200-a650-7eb115f30c6e" /> <br/>

I also changed the wall thickness from 3mm to 7mm in order to support M3 screws to assemble the case <br/>

time spent: 7 hours cadding and coloring

## 7/4/25 - more cadding
america day wowee <br/>

Today I didn't have as much time as normal due to my family going out to celebrate July 4th, but I managed to figure out the internals of the sculk shrieker, trying to pack in everything into the already very small space of 64mm x 64mm x 32mm. <br/>
I started with importing all of the components from my Aliexpress list to Fusion by finding them on GrabCAD. I didn't find any for the specific speaker I found on Aliexpress, so in order to import it into my model, I had to reconstruct it with external documents and schematics from Alibaba and other internet images. <br/>
> the speaker controller module also didn't come with the appropriate headers/connectors so I had to import and model those in as well 

<img width="632" alt="image" src="https://github.com/user-attachments/assets/1934151b-71e5-43e6-b98a-3ef8d0e15c7c" /> <br/>
![image](https://github.com/user-attachments/assets/c1aca12f-8174-4e3d-b3ba-91f0d90fa078)
![image](https://github.com/user-attachments/assets/bc110c50-e9a7-43f2-a5d5-7d481ce729c9)

Once I had the parts in, I inserted them into the shrieker model and started to move and position them around. To improve on the ease of printing/building and to cut costs on screws, I decided to not create any screw holes to mount the modules, and instead I opted to create slots for the modules to fit inside and gluing/taping them once in. <br/>
I also plan on handwiring everything for this project, since a pcb to fit everything in this build is gonna be *way* out of size. <br/>

<img width="559" alt="image" src="https://github.com/user-attachments/assets/cdc23552-1b74-4436-9246-69757c28217c" /> <br/>

This was also the time that I realized that the speaker I am using is *fucking massive* <br/>

<img width="867" alt="image" src="https://github.com/user-attachments/assets/1657d85f-a8a3-4060-9ce4-8b3ac9d1eabe" /> <br/>

Everything fit inside nicely, but I had some issue finding where to place the microphone. I originally said that I could place it on or near the jaws, but turns out that the microphone is significantly bigger than the scale of the jaws. <br/>
The quality of the sound needed doesn't have to be incredible since we're only picking up generally loud sounds, but for now I am placing it next to the speaker in one of the corners of the jaws. When assembling and testing the build, I may pack it inside to make it look more complete, but this will do for now (plus when looking at certain angles, the microphone is hidden from sight) <br/>

<img width="308" alt="image" src="https://github.com/user-attachments/assets/405d62f5-fd24-496c-8e3b-f37de3772fe1" /> <br/>

All this leaves now is creating the PCB to animate the souls circling in the shrieker and the software to accompany it. <br/>
Considering the space left on the model, I may have to place the PCB on top of the block and cover it up with a separate plate similarly to the OLED on my previous Engipad to preserve the printability of the shells.
> considering time constraints on pcb shipping and the deadline of august 7, the pcb *may* not be included (but that's a last resort honestly)

time spent: 3 hours 




