# Background
I'm a huge fan of macOS, but I couldn't afford an expensive MacBook, so I chose an ASUS Zenbook one, and managed to get macOS running stable on it (Hackintosh). The only thing I don't like is trackpad, not because the hardware is bad, actually it's working very well in Windows, but because there were no official driver for macOS, so I have to use alexandred's [VoodooI2C](https://github.com/alexandred/VoodooI2C).

VoodooI2C uses [CSGesture](https://github.com/alexandred/VoodooI2C/tree/master/Multitouch%20Support/CSGesture), a multitouch engine by CoolStar, to implement multitouch gestures. Because it's not an official engine so the gestures aren't very good. Therefore, the authors of VoodooI2C decided to make use of Apple's multitouch engine by simulating a Magic Trackpad 2. The simulator isn't completed yet, but it's still very promising. 

To simulate Magic Trackpad 2, we need to understand Magic Trackpad 2's protocol and how macOS handles it. Reverse engineering is needed.

# Achievements:
The simulator is [here](https://github.com/alexandred/VoodooI2C/tree/native/Multitouch%20Support/Native), currently most gestures work well

# Reverse Engineering:
1. Files to RE:
* /System/Library/Extensions/AppleTopCase.kext/Contents/PlugIns/AppleTopCaseHIDEventDriver.kext/Contents/MacOS/AppleTopCaseHIDEventDriver
* /System/Library/PrivateFrameworks/MultitouchSupport.framework/Versions/A/MultitouchSupport
2. [MT2 Report structure](RE/Report%20structure.md)
3. [Logging data from MT2](RE/Logging%20data.md)
4. More coming soon...

# References:
1. [FingerMgmt](https://github.com/jnordberg/FingerMgmt): used for tracking fingers input by utilizing MultitouchSupport.framework
2. [VoodooI2C's Gitter](https://gitter.im/alexandred/VoodooI2C/archives/2017/11/18): I think this is when the authors of VoodooI2C began to reverse engineer MT2

# Credits:
* [alexandred](https://github.com/alexandred)
* [CoolStar](https://github.com/coolstar)
* [blankmac](https://github.com/blankmac)
* [Kishor Prins](https://github.com/kprinssu)
