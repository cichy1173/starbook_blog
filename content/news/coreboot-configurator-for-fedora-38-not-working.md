---
title: "Coreboot Configurator for Fedora 38 not available"
date: 2023-04-22T19:06:09+02:00
draft: false
---

If you use Fedora 37 wait with updating to Fedora 38. Coreboot Configurator does not work on Fedora 38 yet. 

According to [this issue](https://github.com/StarLabsLtd/coreboot-configurator/issues/24), Coreboot configurator needs something from Fedora 37. 

```bash
Error: 
 Problem: conflicting requests
  - nothing provides libyaml-cpp.so.0.6()(64bit) needed by coreboot-configurator-8-1.fc37.x86_64
(try to add '--skip-broken' to skip uninstallable packages)
```

We need to wait for update from Star Labs.