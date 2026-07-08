---
title: Project SoSe 2026
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---
 
This page gives an overview of the three projects in this year's course
*Proximity Sensing of Biological Diversity*, along with the tasks available for each.
 

---
 
## How this course works
 
The core idea is straightforward: you pick a task of one project, dive into it, and figure it out.
There are no textbooks that cover exactly what you'll be doing.
You will need to experiment, search, fail, try again — and that is entirely intentional.
 

> **The journey is the goal** — but to make that journey gradable, you need to document it.
 
### What we expect from you
 
- Keep a **working log** as you go: what you searched for, what you read, what you tried, what worked and what didn't. Include rough time estimates (e.g. *literature research ~4h, sensor wiring ~2h*).
- Each person is **primarily responsible for one task**. Individual contributions must be clearly identifiable.
- The final deliverable is a **GitLab page** for each project and its associated features (tasks) that is detailed enough for others to reproduce your work — a step-by-step guide (for technical tasks) or a structured report (for analysis tasks). Include technical diagrams and make sure all connections and steps are unambiguous.
- the working log and the github page should together be around 4000 to 8000 words (incl. code if applicable)


# Deadline

19th August 2026


### Use of generative AI
 
| | Allowed | Not allowed |
|-|---------|-------------|
| Code | ✅ Using AI to help write code is fine — but you must be able to explain every line | ❌ Submitting code you don't understand |
| Text | ✅ Revising and improving your own bullet points or drafts | ❌ Having AI write the text from scratch |
 
---
 
## Project 1: Phytoakmeter
 
Despite centuries of forestry research, fundamental questions remain open about the phenotypic plasticity of forest trees, their interaction with microbial communities, and how these interactions drive acclimation and adaptation. To close this gap, the project [Phytoakmeter](https://www.uni-marburg.de/en/fb17/phytoakmeter/phytoakmeter-subprojecs) was established.
 
Our contribution: the Environmental Informatics group uses **optical monitoring** to identify tree growth and herbivory at high temporal resolution.
 
### Tasks
 
#### P1 🔧 Hardware *(offline only)*
Rebuild the [PiCAM](https://besjournals.onlinelibrary.wiley.com/doi/10.1111/2041-210X.14231), design a 3D-printed enclosure, and extend its functionality where sensible.
 
#### P2 💻 Software
Document the existing codebase and extend its functionality — for example by adding temperature or other environmental sensor readings.
 
#### 📊 Analysis
- P3: Extract and visualise RGB values over time
- P4: Manual measurement of herbivory from images
- P5: **Live measurement of herbivory** *(offline)* ⭐


---
 
## Project 2: FlowerPower
 
Last semester, a sensor box was developed and installed at the New Botanical Garden in Marburg as part of this course. The goal is to analyse whether certain insects show a preference for particular flower colours, shapes, or sizes.
 
Each box consisted of a Raspberry Pi Zero W, a 32 GB flash drive, a Witty Pi 4 Mini for scheduled on/off cycles, and a Raspberry Pi Camera Module 3. Various 3D-printed artificial flowers in different colours were used as stimuli.
 
### Tasks
 
#### F1 💻 Software
- F1: Write a script which can be executed on a pi to capture images at regular intervals and add features such as an error log *(note: Pi Zero W, not Pico — document the differences)*
- F2: Add and connect environmental sensors using WokWi, so that they would run in real life (work together with F1)

#### F3 🤖 Machine Learning 
compare existing models for insect detection.
 
####  📊 Analysis
- F4: Compare the attractiveness of different flower **colours**
- F5: Compare the attractiveness of different flower **shapes**
- F6: Compare the attractiveness of different flower **sizes**
- F7: Analyse **activity patterns over time**
---
 
## Project 3: Sensor Map
 
A mini-review of proximity sensors currently available for ecological monitoring: how do they differ in principle, range, resolution, power consumption, and suitable use cases?
 
#### S1 📡 Sensor Review
*2 persons — deliverable is a structured, well-illustrated review page.*
 
---
 
## Next Steps
 
### 1. Form your group
Sign up for one of the three projects. Students who are absent will be assigned
to open projects.
 
### 2. Discuss and distribute tasks
The tasks listed above are **suggestions, not a fixed list**. As a group, discuss:
- Which tasks make sense given your interests and skills?
- Are there features missing that would strengthen the project?
- How do you split the work so each person owns one clear task?
Every person must be responsible for at least one feature.
If you come up with your own idea, great — just run it by us first.
 
### 3. Create your feature branch and page
Once your task is decided:
1. Clone the project repo
2. Create a branch: `feature/yourname-taskname`
3. Copy `example-feature.md`, rename it, and fill in your task description
4. Push and open a merge request
Not sure what your feature should cover yet? Start with a rough draft —
you can always refine the scope as you go.