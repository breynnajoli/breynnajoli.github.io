---
title: "🚦 Smart Roundabout Traffic Control System (SCADA/HMI)"
date: 2026-04-22 22:50:00 +0300
categories: [Projects, Industrial Automation]
tags: [scada, hmi, wonderware-intouch, quickscript, traffic-control]
---

A major challenge in urban infrastructure is managing traffic flow at busy intersections. To explore a solution, I designed and simulated a fully functional **4-Way Roundabout Traffic Control System** using **Wonderware InTouch SCADA**.

![Traffic Light HMI](/assets/traffic-hmi.png)
_Top-down HMI view of the 4-way roundabout system displaying active countdowns and sensor overrides._

### 🎮 Interactive Simulation
To demonstrate the underlying QuickScript logic, I translated the SCADA state machine into the interactive web simulation below. 

**Try it out:** Click the sensor buttons to simulate cars leaving the lane. If the light is green and the sensor detects no cars, the system will optimize traffic flow by skipping the rest of the phase!

<div style="text-align: center; margin-top: 20px; margin-bottom: 30px;">
  <iframe src="/assets/simulations/traffic-sim.html" width="100%" height="700px" style="border: 2px solid #555; border-radius: 10px; background: #8c8c8c;"></iframe>
</div>

## ⚙️ Project Overview

This project is a standalone SCADA simulation built entirely using Memory Discrete and Memory Integer tags. This approach allowed me to rapidly prototype, test, and validate the complex state-machine logic within InTouch before linking it to a physical PLC.

The system relies on a **120-second master cycle** managed by InTouch QuickScript, ensuring the sequence never gets stuck in infinite loops and operates predictably.

## 🚀 Key Engineering Features

* **Smart Sensor Optimization:** The most robust feature of this system is its dynamic adaptability. I programmed virtual inductive loops (`Stop_sensor`). If a lane has a green light but the sensor detects no cars after a 10-second minimum, the QuickScript automatically forces the timer forward, skipping empty phases to optimize overall traffic flow.
* **Pre-Green Amber Sequence:** Unlike standard lights that only use Amber for stopping, I implemented a "Red-to-Amber-to-Green" sequence. This prompts drivers to engage their gears before the light turns green, improving launch times from a dead stop.
* **Dynamic HMI Countdowns:** To assist virtual control room operators, the HMI calculates and displays real-time countdowns (`countdown_timer = Phase_End - Traffic_Timer`), eliminating the need to guess phase durations.

---

## 💻 The QuickScript Logic

Here is a snippet of the core logic I wrote for the traffic monitoring sensors and the switching sequence:

```text
{SENSOR FOR TRAFFIC MONITORING - SKIP EMPTY LANES}

IF Traffic_Timer >= 10 AND Traffic_Timer <= 25 AND Stop_sensor == 0 THEN
     Traffic_Timer = 26;
ENDIF;

IF Traffic_Timer >= 40 AND Traffic_Timer <= 55 AND Stop_sensor2 == 0 THEN
     Traffic_Timer = 56;
ENDIF;

IF Traffic_Timer >= 70 AND Traffic_Timer <= 85 AND Stop_sensor3 == 0 THEN
     Traffic_Timer = 86;
ENDIF;

IF Traffic_Timer >= 100 AND Traffic_Timer <= 115 AND Stop_sensor4 == 0 THEN
     Traffic_Timer = 116;
ENDIF;

{TRAFFIC LIGHT SWITCHING CORE CYCLE}
Traffic_Timer = Traffic_Timer + 1;

IF Traffic_Timer > 120 THEN
    Traffic_Timer = 0;
ENDIF;

IF Traffic_Timer <= 25 THEN
    Red_light   = 0;
    Amber_light = 0;
    Green_light = 1;
    Red_light2  = 1;
    Amber_light2= 0;
    Green_light2= 0;
    Red_light3  = 1;
    Amber_light3= 0;
    Green_light3= 0;
    Red_light4  = 1;
    Amber_light4= 0;
    Green_light4= 0;
ENDIF;

{... Logic continues for the remaining 95 seconds of the cycle ...}


{COUNTER COUNTDOWN TIMER}

IF Traffic_Timer <= 25 THEN
 countdown_timer1=25-Traffic_Timer;
ELSE 
countdown_timer1=0;
ENDIF;
IF Traffic_Timer <= 55  AND Traffic_Timer  > 30 THEN
     countdown_timer2=55-Traffic_Timer;
ELSE
  countdown_timer2=0;
ENDIF;
IF Traffic_Timer <= 85 AND Traffic_Timer  > 60 THEN
 countdown_timer3=85-Traffic_Timer;
ELSE 
countdown_timer3=0;
ENDIF;
{... Logic continues for the remaining seconds of the cycle ...}
