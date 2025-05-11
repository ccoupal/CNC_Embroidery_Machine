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

GeeeTech Prusa i3 used for: 
- 1.8 deg; step angle with 1/16 micro-stepping motors
- X-y gantry with pulleys and belts
- 12v power supply
- Limit switches
- Cables

Singer Feather weight with:
- Modern electronic foot petal
- Free motion foot and plate
- Custom spool holder

Arduino Uno with:
- UNO CNC Shield
- A4988 Stepper Drivers

3d printed parts:
- Eletronics housing
- Fabric hoop and mount
- Sewing machine brackets
## Required Software Downloads:

Universal G-Code Sender: https://winder.github.io/ugs_website/

GRBL: https://github.com/gnea/grbl

Arduino IDE: https://www.arduino.cc/en/software/

## Running the CNC as a sewing machine

Complete CNC Shield Guide: https://www.diyengineers.com/2023/01/05/grbl-with-arduino-cnc-shield-complete-guide/

Free Motion Sewing: https://singer-featherweight.com/blogs/schoolhouse/how-to-free-motion-quilt?srsltid=AfmBOoqhx90eNL3T1ediQ6KxdHOiFjEYng9hg91dZrG5tQKM3qK08ryc

1. Make your sewing machine "free motion". This was done with a singer featherweight and custom aftermarket parts. They block the feed dogs of the machine, and change the foot to a hoop which presses the fabric down. It's essential that your machine works well as a free motion sewing mahcine before you attempt cnc embroidery. This guide helped me and made use with my machine easy.

Free Motion Sewing for Singer 221: https://singer-featherweight.com/blogs/schoolhouse/how-to-free-motion-quilt?srsltid=AfmBOoqhx90eNL3T1ediQ6KxdHOiFjEYng9hg91dZrG5tQKM3qK08ryc
 
![How_to_Free-Motion_Quilt_12_large](https://github.com/user-attachments/assets/ea42d88c-b9fa-4687-8270-843378b90fcb)

2. Build the X-Y gantry. This was doen by using parts from the scrapped prusa 3-d printer. Usiing as many exisiting parts I had from the printer, items around the house, and 3-d printed brackets I created an x-y gantry that could be controlled with the CNC shield. This gantry needs to be level with the sewing machine table and allow for more travel than the embridery hoop. #-d printable examples of a gantry like shown can be produced, removing the need for many parts. Each machine is custom to each sewing machine. Below is a schematic of my machine showing required parts and a detailed view.

 <img width="1259" alt="Screenshot 2025-05-11 at 1 12 01 PM" src="https://github.com/user-attachments/assets/c4d2eacb-80c9-48df-9c93-9f9a5d4b145f" />


3. Wire the machine. At a minimum each motor, the power supply, and the sewing machine will require wiring. I decided to disassemble the foot pedat included with the machine and 3-d print a handle for the slider. This allowed me to adjust the sewing speed on the fly, without having to figure out relays, a digital potientiometer or anything else. After my entire machine was working, I build a electronics enclosure to house these parts.

![IMG_4925](https://github.com/user-attachments/assets/c7238a1e-75eb-444b-aa97-6f73c433a57c)

<img width="403" alt="Screenshot 2025-05-07 at 10 49 42 AM" src="https://github.com/user-attachments/assets/56e46b35-95d3-4e31-aad1-0220c8c34dbb" />

4. Change config within GRBL to included modified config file for 2-axis use only. In the included code package I already did this so it's ready to be used as a sewing machine. This was done in the config.h file and changes the homing cycle to not include the y-axis.

![Homing-3-Axis](https://github.com/user-attachments/assets/1744ba7b-50f5-4f8d-b2f2-043eaa9f90f2)
I changed this.

![Homing-2-Axis](https://github.com/user-attachments/assets/e33e76cf-c9ed-4e46-85cc-c5f6d001c82a)
To this!

6. Open Arduino IDE, connect Arduino to computer, and load GRBL. Follow this path and select "grblupload". 

<img width="600" alt="Screenshot 2025-05-11 at 1 33 40 PM" src="https://github.com/user-attachments/assets/53f56fed-0207-4a68-b0de-e353d147b256" />

7. Use setup wizard to connect machine within Universal G-Code Sender. Use these paramters.

![Screenshot 2025-05-11 at 1 35 12 PM](https://github.com/user-attachments/assets/c0be8943-7ddf-404c-bbaa-f2114846b442)

![Screenshot 2025-05-11 at 1 35 26 PM](https://github.com/user-attachments/assets/b259fc5f-6e54-453a-8eb3-15d7db0552a8)

9. Import design as .svg or other, select "mill pocket", tool diamater (density)
<img width="993" alt="Screenshot 2025-05-07 at 11 01 32 AM" src="https://github.com/user-attachments/assets/48abdda6-54f2-474b-8c96-d1a6e601f187" />

10. Save file-produces g-code
<img width="625" alt="Screenshot 2025-05-07 at 11 01 52 AM" src="https://github.com/user-attachments/assets/d05c5e1e-c553-468b-bf0c-a8e0ee7b7b26" />

11. Use jog machine to position and test range.
<img width="326" alt="Screenshot 2025-05-07 at 11 02 05 AM" src="https://github.com/user-attachments/assets/bf4af091-b874-4335-a120-36a326a926cf" />

## References
https://www.instructables.com/CNC-SewingEmbroidery-Machine/
https://builds.openbuilds.com/builds/diy-embroidery-machine-v2.8630/
https://inkstitch.org/tutorials/embroidery-machine/

# Future Work
- Implementing a dedicated G-code sender using files made for embrodiery, could be done with a posting, CAM software, and custom .svgs.
- Add relay for sewing machine control futher automating the machine.
- Test build volume and possibly move to a larger machine. 
