---
title: "Cubie"
excerpt: "A Rubik's Cube solving robot with solve times under 4 seconds.<br/><img src='/images/500x300.png'>"
collection: portfolio
priority: 1
---

## Overview

Cubie is a Rubik's Cube solving robot that my friend and I designed, built, and programmed from scratch over the span of 9 months. As students who practiced cubing for over the three years prior and could solve it in under 15 seconds, we wanted to build a robot that could solve the cube not just faster than us, but faster than any human out there. We also aimed to keep the budget within $100, and we challenged ourselves to custom-design and code the robot.

At its core, there are only 12 different moves you can perform on a Rubik's Cube. This is because each center piece is held in place, and thus each side can only turn around its corresponding center piece, either clockwise (CW) or counterclockwise (CCW). Thus, to optimie our solve time, we had two different goals in mind, a hardware goal and a software goal.
- **Hardware goal:** To maximize the number of **Turns Per Second (TPS)** that the robot could perform, where each _turn_ is either a CW or CCW rotation of a face.
- **Software goal:** To minimize the total number of turns required to solve the cube.

## Hardware

### CAD

In order to maximize our robot's TPS, the motors turning the robot needed to have instant access to each face of the cube. We decided to use six different stepper motors, one for each face of the robot. To support this, we needed to CAD and 3D print two different aspects of the robot: the infrastructure to house the motors / cube and adapters that connect the stepper motor's shaft to the cube's center piece.

To generate the CAD for our robot, we used [OnShape](https://www.onshape.com/en/), which allows for easy iteration and version control, and also allows easy contribution by multiple people. ~~However, now with more experience, I would recommend using a tool like [Fusion 360](https://www.autodesk.com/products/fusion-360/overview) which provides better and more versatile tools for making complex CADs.~~ Using OnShape, we generated the following CADs for the housing infrastructure and motor adapters.

<video width="320" height="240" controls>
  <source src="/files/Cubie/Housing Infrastructure.mp4" type="video/mp4">
</video>

<video width="320" height="240" controls>
  <source src="/files/Cubie/Adapters CAD.mp4" type="video/mp4">
</video>

For the adapters to fit snugly onto the motors and into the cubes, the adapter widths had to be slightly larger and smaller than the motor shaft width and cube center piece width, respectively. Too small and it wouldn't fit, and too large and it would be too loose. Looseness in the adapters made it so that a 90-degree rotation via the stepper motor wouldn't turn the cube's face a full 90 degrees, resulting in jams. Thus, the adapters required many iterations to perfect into a just-right size.

<img src="/files/Cubie/Adapters.png" width="400" height="200" />

### Electronics

For the electronics, we used 6 [stepper motors](https://www.amazon.com/STEPPERONLINE-Stepper-Bipolar-Connector-compatible/dp/B00PNEQKC0?crid=32PJM6REFBBB3&dib=eyJ2IjoiMSJ9.EP5HV2rY5n8tJ-MMHFxEfxtyfGangyfKPiGJxcAQs57vnZ11TGl-He8UNqLmzBRMxf4cvJiAAl3UfkQPA-GOvBw1psTBHOfcWR-YbQA64ywSLRGL5yqowgmg3EzFPMf7_KTKw4BoB1ClzwMXS4k6qd0kUn1AVZPUhlmJHGkNi5HKLQpGcUDidAh5dQbkk60YLhM53uLBzZZxvZ0bvTNY9xjpk27z_VnjsRX1DAbRs34.sr9AQo-bSdUWeseI1Nhv69LMXRsFhSOYN01_RagO6fI&dib_tag=se&keywords=stepper+motors&qid=1734759526&sprefix=stepper+motor%2Caps%2C154&sr=8-3) and 6 corresponding [motor drivers](https://www.adafruit.com/product/807) that were paired with an Arduino Mega to control the motors. For power, two [3-cell Lipo Batteries](https://hobbyking.com/en_us/turnigy-2200mah-3s-25c-lipo-pack.html) were used in serial to generate 24V to the motors. While actual wire harnesses would've been cleaner, I opted for the lazier method of just throwing everything into a shoebox!

<img src="/files/Cubie/Shoebox.png" width="500" height="200" />

## Software

### Algorithm Development

In an effort to only use resources that I knew before attempting this challenge, we chose to implement the **CFOP algorithm** for our robot. The [CFOP](https://jperm.net/3x3/cfop), or Cross-F2L-OLL-PLL, algorithm is a way of solving the Rubik's Cube one layer at a time, and is the method that most speedcubers (including me) prefer. Additionally, there are many optimizations on this algorithm, such as [ZBLL](https://www.speedsolving.com/wiki/index.php/ZBLL), which combine the OLL and PLL parts of this algorithm. While it's difficult to use in practice because it requires memorizing hundreds of algorithms, this was an easy task for robots.

Before implementing the CFOP algorithm, I decided to construct an interface that would allow me to easily visualize and debug my code. I created this 3D user interface in JavaScript using [p5js](https://p5js.org/). Since the core of my algorithm would be in Python, I used a Flask infrastructure to handle communication between the webapp and the backend.

For the actual algorithm, I coded each step separately. The OLL and PLL sections were quite simple since it simply required using a lookup to determine which **case** we were in and applying that corresponding algorithm. [JPerm's algorithm list](https://jperm.net/algs/oll) containing all of the OLL and PLL algorithms in order made the accumulation of these algorithms simple. Similarly, while the Cross and F2L sections are often solved _intuitively_, I went through each scenario that you could encounter and came up with a simple case-by-case algorithm to solve them. Additionally, to minimize turns, I ran some optimizations after generating the solution to remove or shorten any unnecessary turns.

<video width="540" height="400" controls>
  <source src="/files/Cubie/CubeJS.mp4" type="video/mp4">
</video>

### Robot Interface

Software
- Tkinter to input cube state
- Arduino code to convert into stepper motor commands

## Final Product

Final product
- Pictures of cubie
- Cubie solve
- Fast solve video w/ kociemba
