
# CNC Embroidery Machine

## Motivation and Overview

This project was inspired by my year working in a CNC machine shop, where I gained hands-on experience programming, setting up, and running CNC equipment. Wanting to build a CNC machine of my own, I combined my background in machining with my passion for sewing and outdoor gear design.

I design and sell custom gear to friends and other enthusiasts. Adding embroidery to my products not only enhances their value but also lets me customize them affordably and creatively.

This project repurposes an old Geeetech Prusa i3 3D printer and a Singer Featherweight sewing machine. It uses an Arduino Uno, CNC Shield, and GRBL firmware, and is operated via Universal G-Code Sender (UGS).

---

## Demonstration

- [Machine Demo](https://youtube.com/shorts/HnBqnx8TASg)
- [Universal G-code Sender in Action](https://youtube.com/shorts/SnJd-H4FVdg)

This machine runs via Universal G-code Sender (UGS), which allows you to create toolpaths directly from clipart or SVG (Scalable Vector Graphics) files. Designs can be imported and converted into G-code for the embroidery process.

Screenshots:

![Machine Overview](https://github.com/user-attachments/assets/9895f5a4-0e28-4214-b53b-293a6f1bfce9)  
![Software Screenshot](https://github.com/user-attachments/assets/736eb414-3124-4d6c-a385-e6072b2ddf93)

---

## Build Materials and Installation Instructions

### Hardware Components

**Repurposed Geeetech Prusa i3:**
- NEMA stepper motors (1.8° step angle with 1/16 microstepping)
- X-Y gantry with pulleys and belts
- 12V power supply
- Limit switches
- Wiring and connectors

**Singer Featherweight Sewing Machine:**
- Modern electronic foot pedal
- Free-motion quilting foot and plate
- Custom spool holder

**Electronics:**
- Arduino Uno
- CNC Shield for Arduino
- A4988 Stepper Motor Drivers

**3D Printed Parts:**
- Electronics enclosure
- Fabric hoop mount
- Sewing machine brackets

---

### Required Software

- [Universal G-Code Sender (UGS)](https://winder.github.io/ugs_website/)
- [GRBL Firmware](https://github.com/gnea/grbl)
- [Arduino IDE](https://www.arduino.cc/en/software/)

---

## How to Run the Code

### 1. Free Motion Setup

Make sure your sewing machine is capable of free-motion sewing. I used a Singer Featherweight 221, along with aftermarket accessories that block the feed dogs and allow the presser foot to move freely.

Helpful guide: [Free Motion Quilting for Singer 221](https://singer-featherweight.com/blogs/schoolhouse/how-to-free-motion-quilt)

![Free Motion Example](https://github.com/user-attachments/assets/ea42d88c-b9fa-4687-8270-843378b90fcb)

---

### 2. Build the X-Y Gantry

Repurpose components from the Prusa i3 to build a stable X-Y gantry. It must be level with the sewing surface and allow for greater travel than the embroidery hoop.

Custom 3D-printed parts and mounts help integrate the gantry with the sewing machine.

![Machine Schematic](https://github.com/user-attachments/assets/c4d2eacb-80c9-48df-9c93-9f9a5d4b145f)

---

### 3. Wiring and Electronics Enclosure

Wire up the stepper motors, power supply, and sewing machine foot pedal. I modified the foot pedal by 3D-printing a slider handle to manually control sewing speed, avoiding the need for relays or digital potentiometers.

Once wired, house all electronics in a custom 3D-printed enclosure.

![Wiring Setup](https://github.com/user-attachments/assets/c7238a1e-75eb-444b-aa97-6f73c433a57c)

---

### 4. Flash GRBL to Arduino

Use the Arduino IDE to flash GRBL firmware. In the `config.h` file, modify the homing cycle for 2-axis use only. This is already done in the provided code.

Before:  
![3-Axis Homing](https://github.com/user-attachments/assets/1744ba7b-50f5-4f8d-b2f2-043eaa9f90f2)

After:  
![2-Axis Homing](https://github.com/user-attachments/assets/e33e76cf-c9ed-4e46-85cc-c5f6d001c82a)

To upload GRBL:

1. Open Arduino IDE
2. Go to File > Examples > grbl > grblUpload
3. Select your Arduino Uno board
4. Upload the code to the Arduino

![Flashing GRBL](https://github.com/user-attachments/assets/53f56fed-0207-4a68-b0de-e353d147b256)

---

### 5. Connect to UGS

Use the UGS setup wizard to connect to your machine. Recommended settings:

![UGS Setup 1](https://github.com/user-attachments/assets/c0be8943-7ddf-404c-bbaa-f2114846b442)  
![UGS Setup 2](https://github.com/user-attachments/assets/b259fc5f-6e54-453a-8eb3-15d7db0552a8)

---

### 6. Create Embroidery Toolpaths

1. Click “New Design” and import an SVG file.
2. Adjust tool density (thread spacing).
3. Recommended speed: 50 mm/min.

![SVG Import](https://github.com/user-attachments/assets/48abdda6-54f2-474b-8c96-d1a6e601f187)

4. Save the file to export G-code.  
![G-code Export](https://github.com/user-attachments/assets/d05c5e1e-c553-468b-bf0c-a8e0ee7b7b26)

5. Use the jog feature to position the needle and test range.
6. Start the embroidery process by pressing "Send" in UGS and manually activating the sewing machine.

![Sending G-code](https://github.com/user-attachments/assets/bf4af091-b874-4335-a120-36a326a926cf)

---

## References

Helpful:
- [DIY CNC Sewing/Embroidery Machine – Instructables](https://www.instructables.com/CNC-SewingEmbroidery-Machine/)
- [DIY Embroidery Machine v2 – OpenBuilds](https://builds.openbuilds.com/builds/diy-embroidery-machine-v2.8630/)
- [Ink/Stitch: Open-Source Embroidery Tools](https://inkstitch.org/tutorials/embroidery-machine/)

Less Helpful:
- Some general GRBL tutorials that lacked specific information for 2-axis machines.

---

## Future Work

- Implement a relay to automate sewing machine control via G-code.
- Test and optimize build volume; consider scaling to a larger frame for more complex embroidery designs.
- Explore post-processing options for embroidery-specific G-code generation from SVGs using CAM software.
- Improve thread tension control and motor tuning to avoid missed steps.
- Optional homing routines for more advanced users.
- Develop a custom design interface for simplified SVG import and toolpath generation.
