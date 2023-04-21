---
title: "Coreboot 8.40 Stable for Starbook MKVI-Intel released!"
date: 2023-04-21T16:32:04+02:00
draft: false
---

Finally Star Labs relased new Coreboot for StarBook MKVI-Intel in Stable branch.

**What's new in Coreboot 8.40?**

> - Rebased on edk2 master
> - Rebased on coreboot master
> - Switch to custom FSP based on 3385
> - Disable clock request detect
> - Let coreboot configure ASPM
> - Speed up boot times by not trying to send EOP when the ME is disabled
> - Speed up boot times by caching ramtop
> - Remove the Intel sound entries from the verb table, to fix an issue
> - resuming from suspend thats initiated by a display manager
> - Dont let coreboot try to change variables in the EC memory
> - Fix the verb table not loading completely
> - Enable OC3 Pin
> - Correct the OC Pin for the left USB Type-A
> - Move the mirror flag to a CMOS option


Check more [HERE](https://github.com/StarLabsLtd/firmware/commit/e0c3c59eb4afe6e3f03f2a1f4b1f3dcb044be95e) and [HERE](https://fwupd.org/lvfs/devices/com.starlabs.B6-I.coreboot#186cc4159a8c5fb6f43c3e3122db1d35)

