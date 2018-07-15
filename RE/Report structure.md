# Magic Trackpad 2 report structure

Magic Trackpad 2 (MT2) can connect to Mac via Bluetooth or USB. Since USB is easier to dump raw data sent by MT2, we will focus on USB.

Magic Trackpad 2 uses type5 report. Here is its structure:

```
struct __attribute__((__packed__)) MAGIC_TRACKPAD_INPUT_REPORT_FINGER {
    UInt8 AbsX;                      /* absolute x coodinate */
    UInt8 AbsXY;                     /* absolute x,y coodinate */
    UInt8 AbsY[2];                   /* absolute y coodinate */
    UInt8 Touch_Major;               /* touch area, major axis */
    UInt8 Touch_Minor;               /* touch area, minor axis */
    UInt8 Size;                      /* tool area, size */
    UInt8 Pressure;                  /* pressure on forcetouch touchpad */
    UInt8 Orientation_Origin;        /* orientation and id */
};

struct __attribute__((__packed__)) MAGIC_TRACKPAD_INPUT_REPORT {
    UInt8 ReportID;                  /* report id: 0x02 with Bluetooth, 0x31 with USB */
    UInt8 Button;                    /* 0x1 if you press hard button, 0x0 otherwise */
    UInt8 Unused[5];                 /* padding */
    UInt8 TouchActive;               /* 0x3 if active, 0x2 if not*/
    UInt8 multitouch_report_id;      /* always 0x31 */
    UInt8 timestamp_buffer[3];       /* timestamp */
    MAGIC_TRACKPAD_INPUT_REPORT_FINGER FINGERS[12]; // may support more fingers
};
```

The header is 12 bytes long and each reported finger is additional 9 bytes.

## MAGIC_TRACKPAD_INPUT_REPORT_FINGER
* Touch_Major, Touch_Minor and Orientation are major axis, minor axis and orientation of ellipse touch area, respectively.
* ID is used to identify the finger

## MAGIC_TRACKPAD_INPUT_REPORT
* ReportID: if you connect MT2 via Bluetooth, this byte would be 0x02; if you connect MT2 via USB, this would be 0x31
* Button: 0x1 if you press hard button, 0x0 otherwise. MT2 doesn't report whether it's left or right
* Unused[5]: used for padding
* TouchActive: used to identify when all fingers are lifted. Example use is to release dragging
* Timestamp is the number of milliseconds since MT2's boot-up time 

## How these are encoded
Coming soon
