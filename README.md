# IpCamCore
A short writeup of my Ip-cam adventures

I recently acquired a cheap YI Home 3 camera. As I really do not have any clue on what to use this cam for, I will try to get it working without using the manufacturer's app.

On github, I discovered the various "Yi-Hack", especially roleo's yi-hack-MStar repository, which matches my camera.
Without the input of the net, I would have had no idea where to start.

# Fundamentals
Unlike webcams, the ip-cam is a sophisticated piece of hardware. Besides the mere image acquisition, it offers advanded features like noise and motion detection and streaming.

Unfortunately, to operate the camera, you have to use a vendor supplied app (Android or IOS), so basically all data transfer is via some external servers you have no control over.

As there are plenty of "hacks" to free this type (and many others) from their vendor lock, I started to investigate.

The prerequisite to gaining control over the camera (or hacking, if you like) is to have access to the operating system of the camera, typically a light weigth embedded LINUX.

There are two principles on achieving this:
1. A physical/serial connection between the camera and a host. Just like flashing the Arduinos. I won't go into details on this option, it is well documented and there is an even simpler method:

2. Use a prepared SD card
During it's boot process, the firmware checks if a SD card is present and tries to access some files. I think the main intention for this is to enable firmware updates and allow debugging.
My camera accepts FAT32 formatted cards. The card will be mounted to /tmp/sd. It tries to execute a script /tmp/sd/test/factory_test.sh .

My inital test were simply creating such a file (on my PC) with the content "echo 11 > /tmp/sd/alive". I then inserted the card and fired up the camera. After some 30sec, I cut the power and checked the card with the PC: Success, the file alive was created.

[more to come]


