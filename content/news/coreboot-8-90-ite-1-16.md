---
title: "Coreboot 8.90 & ITE 1.16 released"
date: 2023-08-18T19:17:23+02:00
draft: false
---

Star Labs devs released new Coreboot and ITE for Starbook MK VI. New Coreboot is realased also for older laptops from the company.

**What's new in Coreboot 8.90?**

- Rebased on upstream edk2
- Update EC binary to 1.16
- Rebased on upstream coreboot


**What's new in ITE 1.16?**

- Make the charging LED flicker between red and blue when no
- battery is present
- Fix the ANX7447 initialisation
- Optimise the power sequence
- Adjust the timing of the power button to handle error states


I think both modules are in testing branch. Coreboot 8.90 still isn't released in LVFS. 

Sources: [1](https://github.com/StarLabsLtd/firmware/commit/953a907d4f34ac350946649e993fd0c42a937566), [2](https://github.com/StarLabsLtd/firmware/commit/c9ad48a568864dedf553adcf5c882c3afd92b09c)
