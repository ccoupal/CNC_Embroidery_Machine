# CNC Embroidery Machine

## Motivation and Overview
I was motivated to work on this project follwing a year working in a CNC machine shop. I have had some expierence programming, setting up, and running these machines. I wanted to build some version of a cnc machine for myself.

I am an avid sewer and designer of oudoor gear, I sell these items to friends and other like minded individials. Doing embridery could add value to my items and not cost me much money.

This machine is made with a scrap Geeetech i3, Singer Featherweight sewing machine, Ardunio Uno, CNC Shield, and GRBL with UGS.
![IMG_4924](https://github.com/user-attachments/assets/9895f5a4-0e28-4214-b53b-293a6f1bfce9)
<img width="574" alt="Screenshot 2025-05-06 at 9 12 26 PM" src="https://github.com/user-attachments/assets/736eb414-3124-4d6c-a385-e6072b2ddf93" />

# Demonstration
[Machine Demo](https://youtube.com/shorts/HnBqnx8TASg)

[Universal G code Sender](https://youtube.com/shorts/SnJd-H4FVdg)

This machine runs off a universal G-code sender using built in tool paths. This application can create tool paths directly from clipart or scaled vector graphic (.svg). 

# Build Materials and Installation Instructions

## Build Materials:

GeeeTech Pruis i3 used for: 
- 1.8 deg; step angle with 1/16 micro-stepping motors
- X-y gantry with pulleys and belts
- 12v power supply
- Limit switches
- Cables

Singer Feather weight with:
- modern electronic foot petal
- free motion foot and plate
- custom spool holder

Arduino Uno with:
- UNO CNC Shield
- A4988 Stepper Drivers

3d printed parts:
- Eletronics housing
- fabric hoop
- sewing machine connection

## Required Software Downloads:

Universal G-Code Sender: https://winder.github.io/ugs_website/

GRBL: https://github.com/gnea/grbl

Arduino IDE: https://www.arduino.cc/en/software/

## Running the CNC as a sewing machine

Complete CNC Shield Guide: https://www.diyengineers.com/2023/01/05/grbl-with-arduino-cnc-shield-complete-guide/

Free Motion Sewing: https://singer-featherweight.com/blogs/schoolhouse/how-to-free-motion-quilt?srsltid=AfmBOoqhx90eNL3T1ediQ6KxdHOiFjEYng9hg91dZrG5tQKM3qK08ryc

1. Building the X-Y gantry was done by taking apart a 3-d printer, removing an axis, and botling 2 axis together. With custom 3-d printed parts and brackets I managed to attach an embrodiery hoop to a sewing machine with a "free motion" sewing attachment. This will be differnet for every machine and gantry. Follow this pinout to connect hardware to Shield.
<img width="403" alt="Screenshot 2025-05-07 at 10 49 42 AM" src="https://github.com/user-attachments/assets/56e46b35-95d3-4e31-aad1-0220c8c34dbb" />

2. Make sure free motion sewing works without gantry use, for me this was most of the troubleshooting with machine settings, thread types, and fabric types.

3. Change config within GRBL to included modified config file for 2-axis use only. This removes Z from the homing cycle.

4. Open .grbl within Arudino and then upload it as an example to Arduino UNO.

5. Use setup wizard to connect machine

6. Import design as .svg or other, select "mill pocket", tool diamater (density)
<img width="993" alt="Screenshot 2025-05-07 at 11 01 32 AM" src="https://github.com/user-attachments/assets/48abdda6-54f2-474b-8c96-d1a6e601f187" />

7. Save file-produces g-code
<img width="625" alt="Screenshot 2025-05-07 at 11 01 52 AM" src="https://github.com/user-attachments/assets/d05c5e1e-c553-468b-bf0c-a8e0ee7b7b26" />

8. Use jog machine to position and test range.
<img width="326" alt="Screenshot 2025-05-07 at 11 02 05 AM" src="https://github.com/user-attachments/assets/bf4af091-b874-4335-a120-36a326a926cf" />

## References
https://www.instructables.com/CNC-SewingEmbroidery-Machine/
https://builds.openbuilds.com/builds/diy-embroidery-machine-v2.8630/
https://inkstitch.org/tutorials/embroidery-machine/

# Future Work
- Implementing a dedicated G-code sender using files made for embrodiery, could be done with a posting, CAM software, and custom .svgs.
- Add relay for sewing machine control futher automating the machine.
- Test build volume and possibly move to a larger machine. 
