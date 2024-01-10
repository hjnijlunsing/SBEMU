# SBEMU

This is a fork of crazii/SBEMU attempting to work with the Ali5455 chipset.
The chipset is found in some versions of the HP T5710 Thin Client and currently does not work; from the original source [SC_ICH.C]:
 //{"ALI5455",0x10b9,0x5455, DEVICE_ALI}, // needs extra code

 THP seems to have done it for the SIS_7012; using the intel8x0.c from the Linux source code to check on the differences.

Disclaimer:
- I am not a C-Developer; and the current status is not working and probably never will be ;-)

Action plan:
- Fork Repo (Done)
- Change Readme (Done)
- Try to compile (Done) - Using WSL2
- Check all DEVICE_SIS cases in intel8x0.c check if similar to SIS_7012 code and see how to implement this in SC_ICH.C

To do:
```
[DONE] Line   69: enum { DEVICE_INTEL, DEVICE_INTEL_ICH4, DEVICE_SIS, DEVICE_ALI, DEVICE_NFORCE };
[DONE] Line  409: 	{ PCI_VDEVICE(AL, 0x5455), DEVICE_ALI },   /* Ali5455 */
[DONE] Line  925: 	case DEVICE_ALI:
[SKIP] Line 1598: 	case DEVICE_ALI:  /* No Special code for the NForce PCM table seems to be in sc_ich.h; guess nothing is needed for Ali */
[SKIP] Line 2144: 		case DEVICE_ALI: /* No Special code for the NForce SPDIF seems to be in sc_ich.h; guess nothing is needed for Ali */
Line 2161: 	if (chip->device_type != DEVICE_ALI) {
Line 2203: 	if (chip->device_type == DEVICE_ALI)
Line 2296: 	if (chip->device_type != DEVICE_ALI)
Line 2498: 	if (chip->device_type != DEVICE_ALI) {
Line 2676: 	if (chip->device_type != DEVICE_ALI)
Line 2708: 	if (chip->device_type == DEVICE_ALI) {
Line 2792: 	if (chip->device_type == DEVICE_ALI)
Line 2882: 		6, /* DEVICE_ALI */
Line 2941: 	if (device_type == DEVICE_ALI) {
Line 2962: 	case DEVICE_ALI:
Line 2982: 		if (device_type == DEVICE_ALI)
Line 3007: 	chip->int_sta_reg = device_type == DEVICE_ALI ?
```
