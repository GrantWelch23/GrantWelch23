# Grant Welch

Software Engineering major who is passionate about drones and the software that controls them

## Information Swarm

A ground control station for end-to-end command of PX4 drone systems.

<img src="assets/gcs-missions.png" alt="Information Swarm ground control station — Missions view" width="820" />


## Highlights

- One station for missions, offboard and pilot-control modes, live telemetry, and vision
- Companion software on the aircraft so autonomy is not stuck to a laptop
- Safety layer: heartbeat watchdog, RTL if the app dies, geofence, clean airborne shutdown
- Same stack in Pegasus / Isaac Sim — live movements get a sim pass first
- One repo on the laptop and the Jetson; a local profile picks the role


## Overview

Information Swarm is control software that fulfills two roles: provide a safety layer, and run missions.

The safety layer covers return-to-launch on low battery, geofence breach, or critical sensor errors, plus tested handoffs from flight to hold and from flight to RTL, so the aircraft does not crash while those actions run. Additional testing covers app crashes and freezes: a calm transition to hold, then to return-to-launch. The app handles handoff between the RC transmitter, the companion computer, and the laptop, so there are multiple levels of failsafe.

That safety layer is what makes missions possible — a place to store and execute flight code. Flight code already in Information Swarm includes basic movement (gain or lose altitude, fly forward, turn), pattern flying (circle, square), and missions that expect and react to sensor data. The landing-pad mission is the last of those: the aircraft uses computer-vision from the downward camera to find the pad and adjusts descent to stay on target.

The source is private. I can walk through the code in an interview.
