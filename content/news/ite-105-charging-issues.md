---
title: "ITE 1.0.5 Charging issues"
date: 2023-03-29T20:31:10+02:00
draft: false
---

As some of you may know, EC 1.03 and 1.04 are huge changes to how StarBook MK VI works. I'm referring to a much quieter and more pleasant fan operation, more LED functions or improved touchpad performance. Unfortunately, charging issues started with version 1.03 (see more [here](https://github.com/StarLabsLtd/firmware/issues/89) and [here](https://github.com/StarLabsLtd/firmware/issues/90)). I myself fell victim to this with EC 1.04. EC 1.05 probably fixes this (if I understand the changelog correctly).

Unfortunately, someone reported an issue on GitHub describing the loading problems. These, however, are different from those on EC 1.03 and 1.04. Well, it is possible to restore battery charging simply by unplugging and plugging in the charger. No charging occurs only when the charge reaches 100%. For the time being, the thread is not closed, so we are treating it as an actual bug in the EC firmware.

More is explained below. (This is copied from GitHub)


> After the latest update, having followed along with the other charging issues (#89, #90), a new issue has appeared:
>
> - laptop is powered on, running on battery
> - connect power (DC jack) and external monitor (usb-c, also with charging)
> - battery starts charging
> - eventually battery is full and the power appears to disconnect so that I'm running > on battery
> - battery slowly discharges until I notice
> - unplug the DC jack and plug it back in and it starts charging again

*Full thread is available [here](https://github.com/StarLabsLtd/firmware/issues/95)*
