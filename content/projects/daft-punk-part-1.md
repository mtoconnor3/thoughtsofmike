+++
date = '2026-02-01T09:49:05+01:00'
draft = true
title = 'Building a Daft Punk Helmet, Part 1: The Plan'
tags = ["electronics", "3d-printing", "build-log"]
+++

For many years, I've wanted to make a replica of Thomas Bangalter's Daft Punk helmet — the silver one. Full size, wearable, with working lights. And recently I decided to do something about it. This is one of those projects that floats around in my head in different forms but never materializes because of the scope and complexity. But that ends now. 

## Why?

A lot of elder millennials will remember when Daft Punk first made an appearance. I listened to a huge amount of their music when I was in high school and college, and it's still on a steady rotation today. I always liked the costumes they wore. I guess it was to help separate their personal identities from the music they created. 

## The Original

The original Bangalter helmet has taken various colors and formats over the years, but the one I want to recreate is chrome, and had an animated LED matrix in the visor. This is the one that comes to mind for me immediately. 

![Thomas Bangalter performing as Daft Punk](/images/bangalter-helmet.webp)
*Image: [BBC News](https://www.bbc.com/news/entertainment-arts-65140938)*

## Scope

Generally speaking, this is what I'm aiming for:

- **Shell** — 3d printed
- **Visor** — lexan or acrylic, with window tint applied
- **Lighting** — home-brewed LED matrix
- **Finish** — chrome (or something like it)

## Tools & Materials

### Printing the Helmet itself
For this project I'm going to rely pretty heavily on my 3d printer. I built a Voron 2.4 about 3 years ago and it's been a workhorse for many projects over the years. But this is by far the most ambitious one so far. The helmet shell is too large to fit on the build plate in its entirety. So I'll need to cut the helmet into sections in CAD, print them individually, and bond them together. 

### Lights Lights Lights
One of the things I've seen often in other people's attempts at this project is a whole lot of wiring mess in the helmet. And as I've pondered the project, I've decided that I want to make the electronic components as streamlined and clean as possible. I think I can dispense with the manually soldered grid of LEDs and replace them with something built directly onto a stack of PCBs. That will be an interesting engineering challenge. 

### Brains
The firmware also presents a challenge for me. I'm imagining a setup where I can control the lights wirelessly, which means I'll need something more sophisticated than a simple AVR microcontroller. The first thought that comes to mind here is the [Raspberry Pi Pico W](https://www.raspberrypi.com/documentation/microcontrollers/pico-series.html) because it's cheap, widely available, and offers some flexibility in the way I program it. I also expect to find a lot of resources online for the right way to program it so that will be where I focus my attention. 

![Picture of the Pico in its different formats](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-1s.png)

## Unknowns

### Electroplating
I'd really like this thing to have a mirror finish, to achieve the same effect that the original one had. Pulling that off will be tricky, and involve electroplating plastics which is not something I've done before. 

### Firmware
I'll need to write firmware to drive the LED matrix. I haven't decided if I want it to be fully independent, or driven by some client device somewhere else. If it's driven by a client, it could be wireless or wired. Wireless would be simpler to integrate into the helmet, but a lot more effort in software. So there are some tradeoffs to consider.  

### Power
I'm expecting the LED matrix to be rather power hungry. Lithium batteries are probably going to play a big role in powering the project, but they make me nervous. I'll need to spend a lot of time thinking about how to manage the power demands safely, and figure out exactly how much power I'm going to need to drive this thing for reasonable lengths of time. 

## First Steps

The first step in the process is, of course, finding a good model of the helmet to work from. I've been scouring the web for files that are easy to work with, and found [this one](https://www.thingiverse.com/thing:5033571) on Thingiverse. It's got the right level of detail, and I think I can section it into pieces easily. Once I've done that, the printing begins. 

![3d Render of the helmet model](https://cdn.thingiverse.com/assets/8e/37/a9/de/cf/large_display_Thomas_2.0_-_Helmet.png)


---

*This is part 1 of an ongoing build log. I'll post updates as the project progresses.*
