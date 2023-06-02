---
title: "Coreboot 8.43 released for StarBook MKVI-Intel, StarBook MK V and LabTop MK IV"
date: 2023-06-01T08:37:33+02:00
draft: false
---

Coreboot 8.43 is here and it is based on Coreboot 4.20. 

**What's new?**

- Rebase on coreboot 4.20
- Rebase on edk2 master
- Moving configurable options to CFR so they can now be changed in edk2
- rather than via coreboot-configurator
- Add TPM control to edk2
- Tidy up the information displayed in edk2
- Remove the power_on_after_fail option
- Fix how ASPM is configured in FSP
- Fix the size allocations in ramtop

src: https://github.com/StarLabsLtd/firmware/commits/master

New coreboot is not released in LVFS yet. I think, It will be `testing`. 

UPDATE 22.06.2023: It is testing: https://fwupd.org/lvfs/devices/com.starlabs.B6-I.coreboot#9a32c44f76a019ff132d88daed6afb8e
