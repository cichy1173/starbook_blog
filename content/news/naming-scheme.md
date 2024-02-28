---
title: "Coreboot new naming scheme and 100 W charging"
date: 2024-02-28T20:37:23+01:00
draft: false
---

Star Labs changed naming scheme of Coreboot releases for almost the same like in LibreOffice - YY.MM. First new version is named Coreboot 24.02 and has a lot of new features:

- Resolved an issue blocking the scheduler on StarBook Mk VI
- **Added support for 100W USB-C chargers for StarBook Mk VI**
- Implemented various power optimizations for enhanced efficiency
- Achieved faster power transitions for a smoother user experience
- Tweaked lid behaviour for better functionality
- Introduced new options to disable the card reader and fingerprint readers for increased customization

Yeah, looks like now we can charge laptop even faster with better charger. It is important to know that original charger is 65 W. 

Also Star Labs changed changed compiler to open-source SDCC (replacing Keil), which helps inn sharign EC code under GPL2. 

**New update should be available in LVFS.**