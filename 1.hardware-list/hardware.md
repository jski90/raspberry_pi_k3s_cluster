This is a list of the hardware I have used to get this cluster up and running:
(I will do a section below of non-affiliate links for all of the hardware I used to get this up and running)


- 4	Raspberry Pi 4B 4GB RAM 

- 4 Official Raspberry Pi PoE+ Hats

- 4 GPIO Header Extender

- 4 PoE Header Extender

- 1 NETGEAR 5 Port w/ 4 PoE+ Ports Switch

- 1 6 Pack Cat6 Ethernet Patch Cables (1ft) (Short cable only needed for attachment of Pi to PoE+ Switch)

- 1 GeekPi Raspberry Pi Cluster Case (4 Pi Cluster Case)

- 1 32GB Silicon Power 32GB 3D NAND High Speed MicroSD Card with Adapter (I am using USB Boot so a cheap SD card should be fine for flashing)

- 4 SanDisk 32GB Cruzer Fit USB 2.0 Flash Drive (Used as boot drive)

- 4 SanDisk 64GB 5-Pack Ultra Fit USB 3.1 Flash Drive (Used as persistent storage for cluster)

- 1 M4 Standoff Kit (This will be needed for use with the PoE+ Hats in conjunction with header extenders)

***#NOTES***

-I decided to use the 4GB Raspberry Pi, but if you have access to, or want to spend more money, the 8GB units would be more ideal.  However, the performance is still great with the 4GB units.  You'll have to make that decision for yourself which will work best for your use case.  With how expensive the RPi's are right now, I'm happy with 4GB.

-I made the decision to use the official Raspberry Pi PoE+ hats for a few reasons.  Firstly, I haven't seen a lot of people doing this on their clusters, and I thought it would be more on the "unique" side of things.  Secondly, using the hats would eliminate the need for all of the extra power cables, which can get very messy if you're running a larger cluster.  If you decide to go this route, make sure you get a PoE+ switch, not just a PoE switch.  The PoE+ hats are designed to push more power than the standard PoE hat so if your switch can't keep up, then you'd be better off just using the standard PoE hats.  The use of the PoE+/PoE hats is absolutely unnecessary for these types of builds, as I mentioned before, I just wanted to keep it as clean as possible with cables and offer maximum portability in the process.  If you decide to not use the PoE+/PoE hats, just ensure you add enough power supplys to your hardware list.  There are other manufacturers for PoE/PoE+ hats, I just decided to use the offical ones because they were the most affordable, that compounded with the fact that they are an official RPi part gave me more confidence.

-Initially I made the mistake of not getting the PoE header extenders, so I had to order them separately. Definitely make sure you get both sets of header exteners at the same time or you'll be waiting even longer to get everything fully assembled.  Not to mention, the extenders are cheap so the shipping will often cost a lot more than the actual extenders...

-I wanted to touch again on the PoE+ switch.  If you are using the PoE+ hats, you must use a PoE+ switch to ensure you get the full benefit of the hats.  You can use the standard PoE hat for this type of build if that is what you're wanting to do to save some money on the switch.  I decided to use the PoE+ hats mainly because they are the same price as the standard PoE hat but they can deliver more power.  The standard PoE hat can deliver 15.4W over Cat5 cables whereas the PoE+ hat can deliver up to 30W (25.5W to power devices) over Cat5 cables.  Seeing as I will be using 2 USB flash drives per RPi I wanted to make sure that power wouldn't be an issue for this build and opted for the PoE+ hat and PoE+ switch.  The switch I chose can also be managed, which I thought was a nice touch.  Realistically, you can get the cheapest PoE+ switch you can find, though I would say getting a "name brand" might be the safer route.

-I chose the GeekPi cluster case mainly because I like the way it looks and how open it is.  Especially with the fan on front moving air directly across all of the Pi's in the cluster.  Something I didn't notice in the pictures of the case, but I think is amazing, is that the case actually comes with SD card relocation brackets so it will actually make the SD card reader accessible from the rear of the case.  Without these, you would almost have to disassemble the case to get to the SD card brackets. 

-A cheap SD card should be more than enough to flash the USB boot software onto the RPi's.  If you're not planning on using USB boot, I would highly recommend getting a high quality name brand SD card so you don't have to worry about any failures.  The reason I chose to go the USB boot route is mainly because we are making a Kubernetes (K3S) cluster.  From the research I have done, USB flash drives have shown more longevity in read/write cycles than SD cards and given that we will be reading/writing a decent amount with this cluster, and setting up USB boot is so simple with the RPi imager, it made more sense to me to go this route.  Additionally, this will allow us to set up persistent stoarge (USB boot is not required for this).  Something worth mentioning is that the SD card will typically have a faster read/write speed, but that's a sacrifice I'm willing to make for the sake of longevity.

-The SanDisk USB flash drives will be used for boot (32GB) and persistent storage (64GB) on each RPi in the cluster.

-The standoff kit will be required if you decide to go the PoE hat/GPIO header extender route .  The official hats render the GPIO pins inaccessible (unless you're wanting to solder, which I did not).  Buying a simple GPIO/PoE header extender allows us to have access to our GPIO pins, however, this increases the standoff distance between the hat and the main board.  This is where the standoff kit comes into play.  I found that a 10mm standoff fit perfectly between the hat and main board.  You can choose to use a standard double-female standoff or you can use a 10mm+ male ended standoff.  This decision can be made much easier by purchasing a standoff kit that has multiple options for you and makes it easier to make the best decision for your build.  You can always just use a GPIO header extender on the top RPi and not use extenders on the ones below it.  We mainly need access to the GPIO pins on the top RPi so that we have a place to connect the fan for the GeekPi case that I picked.  I decided to do the extenders on all of the RPi's because I thought it would be nicer to have them look more uniform and the standoff kit comes with plenty of hardware to extend them all.  

***#LINKS (NON-AFFILIATE)***

- Raspberry Pi: You're going to have to do some work on your own to find these, I got mine mainly from eBay as they're difficult to source right now

- [Official Raspberry Pi PoE+ Hats](https://www.raspberrypi.com/products/poe-plus-hat/)

- [GPIO Header Extender 4 Pack](https://www.amazon.com/dp/B08M5TWWRC?psc=1&ref=ppx_yo2ov_dt_b_product_details)

- [PoE Header Extender](https://www.adafruit.com/product/4855#tutorials)

- [NETGEAR PoE+ Switch (GS305EP)](https://www.amazon.com/dp/B08LR18SC4?ref=ppx_yo2ov_dt_b_product_details&th=1)

- [Cat6 Patch Cabling](https://www.amazon.com/dp/B01IQWGKQ6?psc=1&ref=ppx_yo2ov_dt_b_product_details)

- [GeekPi Cluster Case](https://www.amazon.com/dp/B083FDHPBH?psc=1&ref=ppx_yo2ov_dt_b_product_details)

- [Cheap 32GB SD Card](https://www.amazon.com/dp/B07Q384TPK?psc=1&ref=ppx_yo2ov_dt_b_product_details)

- [SanDisk 32GB USB Drive (Boot)](https://www.amazon.com/dp/B07MPCJDXS?ref=ppx_yo2ov_dt_b_product_details&th=1)

- [SanDisk 64GB USB Drive (Storage)](https://www.amazon.com/dp/B077VYCV37?ref=ppx_yo2ov_dt_b_product_details&th=1)

- [M4 Standoff Kit](https://www.amazon.com/dp/B07PKTVB18/ref=twister_B07D782FJJ?_encoding=UTF8&psc=1)
