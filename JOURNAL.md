---
title: "Bolide65"
author: "Reuben 0"
description: "A custom 65% keyboard with 66 keys, a rotary encoder, RGB backlighting and a few custom macros that I'm making to replace my sister's broken keyboard." 
created_at: "2026-10-05"
---

# October 6: Initial Brainstorming + Research and Final Plan

From the start of Week 1, I knew that I wanted to design and build a custom mechanical keyboard. Creating a keyboard was already something I had been interested in (due to the KEEB YSWS), and Half Life gave me the motivation to finally begin the project.

Since Monday, I have spent approximately 2.4 hours brainstorming and researching keyboard design. This consisted of two dedicated 2 hour research/discovery sessions, along with additional idea development throughout during small spare moments in my day, such as lunch breaks and my train rides to and from school. Based on my browser history, Google Docs revision history, and the time spent sketching concepts, I feel that 2.4 hours is a fair estimate of my work so far.

During this research process, I learned about and decided on different keyboard layouts and form factors, mechanical switch types (linear, tactile, and clicky), keycap profile options, adding custom macro functionality, and general keyboard construction methods! I am now super ready to begin making my schematic! The Hack Club KEEB YSWS guide was especially helpful in helping me get my foot in the door with regards to understanding the overall design process and the components required for a custom keyboard. I put my notes and brainstorming ideas on a google doc and then polished it up with my final design idea:

![google docs](assets/journal/bolide-journal-docs_plan.jpeg)

**Project Inspiration**
This project will kill two birds with one stone: help develop my hardware skills and also help my sister. As I explained in my idea reel, I am designing this keyboard for my sister because a few of her keys on her laptop keyboard have stopped functioning properly. She has continuously expressed annoyance at how this makes completing school assignments much more frustrating. Since she will likely need to wait a whole year before replacing her laptop, I wanted to create an external keyboard that she can use in the meantime.

**Design Explanation**
I named the project “Bolide” because I want its LEDs to be a major part of its visual identity. The keyboard will feature LED backlighting and keycaps that allow the LEDs to shine through. I also plan to use a sandwich mounting design with a translucent top plate, allowing light to pass throughout the keyboard and emphasize its aestheticss

After researching different layouts and components, I settled on a 65% keyboard layout (I was debating on 75% and TKL, but was worried it would be too expensive to make - I think the 65% will allow me to stay under tier 2 budget). To restore lost functionality, I will add a fn key that will allow my sister to still access a hidden function key layer on the number pad.

Some other notable choices is that I chose linear switches (as my sister did not express a strong preference for a specific kind, so I chose the simpler option), a rotary encoder that will likely be volume control and custom macro keys replacing the Delete, Page Up, and Page Down keys.

Before finalizing the design, I tried sketching out layouts based on a few 65% layouts I liked… but inevitably failed (none of them looked nice or helpful). So I just recorded my decisions and then tried to draw the general shape of the keyboard. Once I was satisfied with the concept, I finalized the layout using [Keyboard Layout Editor NG](https://editor.keyboard-tools.xyz/). I will use this layout for making the top plate when doing CAD. (I’m NOT using it to generate traces for my PCB!!)

![rough idea sketch](assets/journal/bolide-journal-sketch.jpeg)
![keymap](assets/journal/bolide-journal-layout.jpeg)

At this stage, I have completed the initial planning and research phase. My next steps will be beginning the PCB design process!! See ya tomorrow

**Total time spent: 2.6 hours**

# October 7: Started Schematic

Did a work session this evening where I focused on starting the PCB schematic for my keyboard! 

I spent the first few minutes of my session ensuring I have sucessfully imported right symbols and footprints I will need for my schematic. I specifcally had to upload the schematic for the RP2040 Zero (the microcontroller I chose to use for this project) and download the marblastlib library from the ebastler KiCAD Repository (has all the keyboard specific symbols and footprints I will need). I had to keep pausing the timelaspe so I could do some extra reading regarding the components I was using and the way I was setting up my schematic to ensure I was not messing up anywhere.

Afterwards, I got to start on the keyboard matrix as I figured it would take most of my time. For my keyboard matrix, I am using 9 columns and 8 rows to connect all 66 keys and the clicker function of my rotary enocder to the RP2040. I was planning to work for two hours, but cut the session short as some delays made me work a bit later than I wanted and I realized I may have incorrectly planned for how many keys would be in the last row of my matrix. I'll double check my work and hopefully finish the schematic tommorow.

![schematic in progress](assets/journal/bolide-journal-WIP_matrix.jpeg)

[**Laspe Recording**](https://lapse.hackclub.com/timelapse/WhSj9wUxpo-r)

**Total time spent: 1.48 hours**

# October 8: The Schematic is Almost Done!

After yesterday's session, I figured out how to properly add my rotary encoder to the keyboard matrix and also determined my original matrix plan was missing two keys on the last row. So today I fixed those two things and double checked all my connections.

I thing I want to work on during this project is producing clean schematics and routing. I think I am making some progress on that goal as today, I learned how to create sub-sheets in KiCad to isolate certain parts of the schematic. Additionally, as a double check to ensure I had all the keys I needed in my schematic, and to increase the clarity of my PCB, I labelled each switch with its corresponding keycap label (based on my keymap design).

![matrix done](assets/journal/bolide-journal-matrix.jpeg)

After finishing my keyboard matrix, I linked up my rows and columns to my main microcontroller, the RP2040 Zero. While I was at it, I also added the necessary power symbols and other connections to board schematic. The main reason I chose it is because it has a small size that still supports just enough GPIO pins for me to fit all the features I want!

![microcontroller schematic](assets/journal/bolide-journal-mc_schematic.jpeg)

I then began making my LED daisy chain. I went into it thinking I could create a larger version of the daisy chain I made for my macropad, but after I finished creating the main chain and was comparing it with my own past design (for my macropad) and other online schematics, I noticed many designs from other people had capacitors in them. I'm going to have to do a bit more research before I finalize the data chain for my SK6812 MINI-E LEDs. Once that is done, I can move on to the actual PCB design!

[**Laspe Recording:** Finishing Keyboard Matrix](https://lapse.hackclub.com/timelapse/16NFAEM3M887)

[**Laspe Recordng:** Working on LED Data Chain](https://lapse.hackclub.com/timelapse/T1WGkkZpFPrV)

(I added a bit more extra time from my timelapse to account for one moment I forgot to unpause my recording when adjusting the LED symbol names as well as the preliminary time I spent confirming my schematic plan with datasheets)

**Total time spent: 2.02 hours**