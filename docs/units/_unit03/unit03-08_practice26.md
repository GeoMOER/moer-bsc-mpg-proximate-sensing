---
title: Three challenges
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

# Unit Challenges — Team Session
 
> This unit consists of **three parallel challenges**. You will split into three teams, each tackling a different challenge simultaneously.
 
---
 
## Hybrid Session Rules
 
To keep online participants fully involved, every team assigns a **Communicator** role:
 
- One person in the room is responsible for actively including the online participants throughout the session.
- Tasks that require physical hardware are handled by the people on-site; online participants take care of software, documentation, and research tasks.

---
 
## Challenge 1 — Reverse Engineering a Sensor Box
 
**Format:** Mostly offline · max. 2 online participants  
 
### Goal
Reverse-engineer an unknown sensor box using only hardware inspection — no software, no AI assistance apart from google lens or similar to identify the components.
 
### Steps
 
1. **Examine the hardware** — open the enclosure and carefully inspect all visible components.
2. **Identify components** — look for labels, markings, chip numbers, connector types etc. Try to retrace the cables to identify connections. Please try to not destroy it / be able to set it back together afterwards.
3. **Draw the circuit diagram** — sketch the layout by hand or on paper; capture how components are connected.
5. **Determine component functions** — for each identified component, describe what it likely does (sensor, power regulator, microcontroller, etc.).
6. **Document findings** — write a brief summary: what components were found, what each does, and any open questions.

 
---
 
## Challenge 2 — Pico Super Script
 
**Format:** Online + offline  
**Focus:** Software integration, hardware testing
 
### Goal
Combine your teammates' individual Pico scripts into one unified "super script", verify which hardware elements are actually available, and test it physically.
 
### Steps
 
1. **Collect all submissions** — gather the scripts submitted by team members from Ilias.
2. **Audit available hardware** — check which sensors, actuators, and modules are physically present and can actually be used.
3. **Review and merge scripts:**
   - Identify overlapping or conflicting code sections.
   - Resolve pin conflicts and naming inconsistencies.
   - Create a single, clean combined script.
4. **Test incrementally** — test it online.
5. **Write on Pico** -  write the combined script to the Pico (see below) .
5. **Recreate physically** — wire up the components on a breadboard or enclosure to match the script's expected hardware layout.
6. **Document the final setup** — note which features work, which were excluded, and why.

---
 
## Challenge 3 — Camera Setup & Cron Job
 
**Format:** Split task — offline (hardware) + online (software)
 
### Goal
Test different cameras with a Raspberry Pi and set up an automated cron job to run a script on the Pi Zero headlessly.
 
### On-site Team — Camera Testing
 
1. **Set up the Pi with camera support** — together with me.
2. **Connect and test each available camera** — note the camera module name and resolution.
3. **Determine optimal distance** — for each camera, find the minimum and maximum distance that yields a sharp, usable image.
4. **Compare image quality** — photograph two insects of different sizes (e.g., a large beetle vs. a small fly) with each camera. Note differences in detail and sharpness.
5. **Document results** — create a simple comparison table


### Online Team — Cron Job / Automation Script
 
1. **Review the headless Pi Zero setup** — see the setup notes below for how the Pi Zero was configured with a local Wi-Fi connection.
2. **Write a shell or Python script** with basic functionality (e.g., capture an image, log a timestamp, or ping a service).
3. **Create a cron job entry** — format: `* * * * * /path/to/script.sh`
4. **Test the cron syntax** — use [crontab.guru](https://crontab.guru) to verify your schedule expression.
5. **Deploy to the Pi Zero** — transfer the script (help will be provided by me)
6. **Verify execution** — check logs (`/var/log/syslog` or a custom log file) to confirm the cron job runs as expected.

---
 