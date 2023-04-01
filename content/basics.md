---
title: "Starbook Basics"
date: 2023-03-28T15:25:37+02:00
layout: post
draft: false
hidemeta: true
ShowToc: true
TocOpen: true
---

*Last updated: 2023-04-01*

Here I include information that helps to understand Starbook laptops. I will try to skip over knowledge that can be obtained in a few seconds on internet search engines. I will also not write about the Star Labs company itself, as you can find out everything on their website.

Lots of important information and useful descriptions of activities are published by Star Labs itself [HERE](https://starlabsltd.github.io/firmware/).

## Technical

In this section, I will talk about technical topics and terms, that StarBook user should know.

### What is ITE?

ITE, or ITE Tech. Inc. is a manufacturer of embedded controller. This module is receiving and processing signals fromm keyboard, touchpad, switches or charging. You can see what ITE looks like by removing the bottom cover. The controller has been carefully signed.

### What is EC?

EC stands for "Embedded Controller".

### Are ITE and EC the same thing?

If we are talking about Starbook MK VI, then yes. We can use the words EC and ITE interchangeably. Star Labs itself does so on its GitHub.

### How to check installed ITE/EC version?

This is very simple and we can use fwupd for this. The first option is to type the command in the terminal 
```bash
fwupdmgr get-devices
``` 

Then we look for a device named `SuperIO FuSuperioIt89Device`. 

Alternatively, we can use a GUI application to support fwupd, such as [GNOME Firmware](https://beta.flathub.org/pl/apps/org.gnome.Firmware). Launch the application and look for a device named `SuperIO FuSuperioIt89Device`.

### What is coreboot?

Coreboot is an open source BIOS for laptops and desktops. It is also one of the key features of Starbook, as few laptops are compatible with coreboot. Coreboot is open source and neutralises the Intel Management System. Learn more about [IME online](https://www.intel.com/content/www/us/en/support/articles/000008927/software/chipset-software.html).

Coreboot has quite a few advantages over AMI. We have already mentioned the neutralisation of IME. It is also worth adding the possibility of modifying the BIOS operation directly from the operating system or even a longer operating time (I have not tested this myself, however). Coreboot also gets updates more frequently.

### What is AMI?

AMI, or American Megatrends, is a typical BIOS you have probably encountered. In short, we can say that it is a generic BIOS that just works.

### What problems does coreboot have?

Unfortunately, coreboot is not perfect. The first problem is that any change to the EC makes us have to reboot. Secondly, coreboot does not work with every SSD. I found this out for myself when two different drives (an ADATA XPG and a Toshiba) didn't work immediately after purchase. Instead, a Samsung Evo 980 worked. 
Interestingly, the latest (at the moment) release of coreboot 8.31 includes a special workaround that makes many of the drives supported. Unfortunately, the workourand has been removed in coreboot 8.32, and we don't know when it will return.

### How fan works (valid from EC 1.03)

From EC 1.03, StarBook MK VI has better fan curve. Laptop is silent and should be more power efficient. Sean from Star Labs published code written in C that helps understand how new curve works.

```C

const struct fan_curve code quiet_mode = {
	//				1	2	3	4	5	6	7	8	9	10	11
	/* .start_temp	= */	{	0,	55,	60,	65,	70,	75,	80,	85,	90,	95,	100},
	/* .duty	= */	{	0,	0,	0,	20,	25,	30,	35,	40,	50,	60,	70}
};

const struct fan_curve code normal_mode = {
	//				1	2	3	4	5	6	7	8	9	10	11
	/* .start_temp	= */	{	0,	55,	60,	65,	70,	75,	80,	85,	90,	95,	100},
	/* .duty	= */	{	0,	0,	30,	35,	40,	45,	50,	55,	60,	65,	70}
};

const struct fan_curve code aggressive_mode = {
	//				1	2	3	4	5	6	7	8	9	10	11
	/* .start_temp	= */	{	0,	55,	60,	65,	70,	75,	80,	85,	90,	95,	100},
	/* .duty	= */	{	0,	20,	25,	30,	40,	50,	70,	80,	90,	95,	100}
};

/*
 * Hook:	500ms (b)
 * Purpose:	Update the fan duty
 */
void update_fan_rpm(void)
{
	struct fan_curve fan_profile;

	int required_duty		= 0;
	int i;
	int duty_change;
	int max_change;
	int new_duty;
	int fan_multiplier;

	/* Get the fan profile that is selected */
	switch (emem_fan_mode) {
	case FAN_MODE_0:
		fan_profile		= quiet_mode;
		fan_multiplier		= 1;
		break;
	case FAN_MODE_2:
		fan_profile		= normal_mode;
		fan_multiplier		= 8;
		break;
	default:
		fan_profile		= aggressive_mode;
		fan_multiplier		= 4;
                break;
	}

	for (i = 0; i < 11; i++) {
		if (emem_cpu_temperature < fan_profile.start_temp[i])
			break;
		required_duty = fan_profile.duty[i];
	}

	duty_change = required_duty - eram_fan_duty;
	max_change = (MIN_DUTY_CHANGE * fan_multiplier) * duty_change / 100;

	/* If the duty is descreasing, decrease in smaller increments */
	if (required_duty < eram_fan_duty)
		max_change = max_change / fan_multiplier;

	new_duty = floor(eram_fan_duty + max_change);
```

How we can see, *Quiet mode* turns fan quite late and not that aggresive. Also *Normal mode*  turns fan late, but more aggresively. 

## Firmware updates

In this section I will talk about firmware and handling updates.

### What is fwupd?

fwupd is an open source daemon that allows us to update the firmware of individual hardware. Updates are published on the LVFS platform.

### How to use fwupd?

Check official tutorial made by Star Labs [HERE](https://starlabsltd.github.io/firmware/methods)

### How to upgrade coreboot/BIOS?

Check official tutorial made by Star Labs [HERE](https://starlabsltd.github.io/firmware/methods)

### How to downgrade coreboot/BIOS?

To downgrade the BIOS version, please open a Terminal window and run the following command: 
```bash
fwupdmgr downgrade
```
From here, you will be presented with a list of available BIOS versions to choose from. Select last stable release. You will need to restart once the process has finished going through the steps.

### What is LVFS?

LVFS stands for Linux Vendor Firmware Service. This is a platform, where manufacturers post their firmwares for updates.

### How to look for updates?

New updates are first published on Github [HERE](https://github.com/StarLabsLtd/firmware/) and then on LVFS . It is best to wait for the release in LVFS.

### Can the EC update itself?

Yes. If a particular coreboot or AMI update brings in a new version of ITE, the update will perform itself. It is then best to plug the laptop into the charger using the DC port. The update will be performed if you do a BIOS update and immediately switch off the computer. Then the next time you switch on, the laptop will be unresponsive for a few minutes. This is when the update is performed. Star Labs has a great explanation of this [HERE](https://starlabsltd.github.io/firmware/methods/magic/).

### How to downgrade EC/ITE?

It is really easy to do. You need only pendrive formatted to FAT/FAT32, and zip file with wanted EC version. Unzip archive and copy files to pendrive. Then reboot laptop to EFI shell with connected pendrive. I done it, it's easy.

Full, detailed instructions are provided by Star Labs and published [HERE](https://starlabsltd.github.io/firmware/methods/efi_shell/)

## Getting help

You can do this in a number of ways. 

- Email Star Labs
- Write to Star Labs on their website (embedded chat)
- If you find a bug, please report it on [GitHub](https://github.com/StarLabsLtd/firmware/)
- In very difficult cases, you can call them. You can find the current telephone number on the Star Labs website. Please note, remember that you will have to pay for a phone call to the UK.
- Seek help from the community at [r/starlabs_computers](https://www.reddit.com/r/starlabs_computers/)
