# A314 - a co-processor for the A500 trapdoor

﻿The Amiga series from Commodore became one of the best selling home computers of the 80's and 90's. Their success came not only from their competitive price, but mainly from their ability to outperform almost everything else on the market, including systems whose cost were orders of magnitude more expensive. And they did that by utilizing a concept of ASIC chips called co-processors. 

Those chips could off-load the main processor and perform specialized tasks such as manipulation and rendering of graphics and audio of - at the time - stunning quality. This project continues that legacy, and nearly 35 years after the first Amiga, presents yet another co-processor: The Raspberry Pi SBC.
## Is it really a good idea to put a computer inside another computer?
We obviously think so, and this is why: The Amiga 500 was a great machine of its time, but has become seriously outdated. Its actually so dated that it's nearly impossible to use for anything else except for those moments of nostalgia when you're playing old games or maybe just whipping up some code to convince yourself that coding was so much more fun back in the days... We felt that the A500 still has more to offer, as long as we could get around some practical obstacles.

One being the obvious lack of internet connectivity. Today almost anything you do on a computer, is somehow related to the internet. The A500, which merely has its serial port for data transfer*, is quickly falling behind. The Raspberry Pi on the other hand is the perfect Internet companion. It can take care of the protocol handling, data buffering and file shovelling labour, and present ready-to-use, nicely formatted content towards the Amiga OS.

Another major drawback of an old computer is of course its poor performance when it comes to raw processing power. Just face it - a Raspberry Pi SBC runs in circles around the Amiga. It's fast enough to emulate the whole machine even though it has a completely different processor architecture! So we thought we could let the Amiga take advantage of some of that abundant resource, and offload some tedious tasks to that competent little SBC.

Those tasks could for instance be cross-comping Amiga code, or decoding MP3 audio files, or why not having a throwback with those Mandelbrot images that were so popular back then? But instead of waiting 7 hours for a single image to complete, you could have it served in minutes, if not in seconds!

*_Yes, the Amiga has other ports that could be used for data transfer, but they are kind of exotic and beyond the point here._
## Once you place a computer inside another computer, great ideas are formed
The fist prototype was built around summer 2018, and we had quite a few issues to work out. One of them was that neither of us was any good at HDL. That got sorted out, even if we are still learning :)

Another thing that became apparent, was that the project took a slightly different path then was initially intended: The whole thing was actually meant to be a kind of hardware accelerated browser engine, in order to allow for Amiga users to surf the net. After some R&D work, we came to the conclusion that even if we could achieve the necessary power and speed to cope with today's web pages, the Amiga video hardware was not capable of generating graphic output of adequate quality. It's easy to get spoiled by current video resolutions and colour depths and think it could be easily ported to a screen of 640 x 256 with 16 colours at best. Sadly, it cannot. This is what graphics could look like:

| Original image | Amiga image |
:-------------------------:|:-------------------------:
![Original image](./Pictures/img.jpg) | ![Amiga image](./Pictures/A_img.png)

You might think the image looks kinda ok, but once you add text, you'll notice its hard to get it in good contrast and easily readable. Another thing is that the Amiga uses an awkward aspect ratio of 5:2 (640 x 256), which needs to be inversely stretched (compressed?) to translate from a typical square pixel.

During the process we discovered a lot of interesting things that could be done once you have direct access to (parts of) the Amiga custom chip memory, or "chipmem" as it is called. For instance, if you place graphic data in the proper bitplane format, the Denise custom chip will happily output whatever you have put there, without bothering the CPU. This means you can show fancy graphics and even animated video with a 0% penalty hit on the Amiga's CPU! 

The same goes for audio; Amiga users have always been envious of the PC community for their ability to play mp3-encoded music. But if you do the processor-intensive decompression on the Raspberry, you could just present the decoded sample data for custom sound chip Paula to read out and play. Just like that, still with a 0% CPU load in the Amiga.

Those are cool features, nice and neat, but the most productive one is the PiDisk: device driver and Pi shell handler. You can find more details on those in the documentation here.
## That's cool, but I have this great idea...
Perfect! That is exactly what we were hoping for. We have realized that the A314 module is not a complete product that you buy or build, and then use as intended, but rather a starting point or an enabler for great ideas and projects. We won't say its limitless, but it certainly expands the horizon of possibilities for what can be done on a Amiga 500 home computer.

We have placed everything we know about the board, it's hardware and firmware, and all the software necessary for both the Amiga and the Raspberry Pi in this public repo. Further, we have chosen a license model that ensures perpetual freedom for the intellectual property of this project. In total, it should be everything you need to realize your great idea.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNzUzMzYyNiwtMjA2NDE5MjMxNSwtMT
IyNDM5MDUyN119
-->
