---
title: "Coreboot 8.50 released for Starbook MK VI and LabTop MK IV"
date: 2023-06-14T15:17:19+02:00
draft: false
---

New Coreboot released for Starbook MK VI and LabTop MK IV.

**What's new?**

> - Rebase on coreboot 4.20
> - Rebase on edk2 master
> - Move the configurable options to CFR so they can now be changed in
> - edk2 rather than in coreboot-configurator
> - Rename the pci_hot_plug setting to Third Party SSD Support
> - Tidy up the information displayed in edk2
> - Remove the power_on_after_fail option
> - Fix how ASPM is configured in FSP
> - Fix the size allocations in ramtop
> - Switch to fixed bars
> - Switch to upstream fsp

- [Starbook MK VI commit](https://github.com/StarLabsLtd/firmware/commit/4db902c7a0414b33e97e7001bfd89eaa529d3596)
- [LabTop MK IV commit](https://github.com/StarLabsLtd/firmware/commit/f5ad9ff8c88a5c5d4968fc582133b244e01b68ae)


