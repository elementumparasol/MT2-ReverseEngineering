# Logging data from Magic Trackpad 2

## Boot arguments (haven't tested)
Use these boot arguments: "mt-strings=0x1 mt-bytes=0x1"  
Search for "AppleMultitouchDriver" in system log.

## IOHIDDumper
This kext is created by [CoolStar](https://github.com/coolstar) to dump raw data from MT2. It hasn't been open-sourced yet. You  can find it on [VoodooI2C's Gitter](https://gitter.im/alexandred/VoodooI2C).
