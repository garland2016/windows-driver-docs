---
title: ReleaseDeviceRequested
description: ReleaseDeviceRequested
ms.assetid: '0fcb8905-1370-4260-9456-6c80e2186dfc'
---

# ReleaseDeviceRequested


This event occurs when another client attempts to claim a device. The data buffer for this event is as follows.

Syntax
------

``` syntax
typedef struct _PosEventDataHeader
{
    // Event enumeration value
    PosEventType EventType;

    // Size of buffer required to read entire event (including header)
    UINT32 DataLength;
} PosEventDataHeader;
```

The following table shows the memory layout of the data buffer for this event.

| Memory value          | Description                                                     |
|-----------------------|-----------------------------------------------------------------|
| 0x00000001 | **EventType = PosEventType::ReleaseDeviceRequested** |
| 0x00000008 | sizeof(**PosEventDataHeader**)                       |



Remarks
-------

This event is handled on behalf of the device driver by Point of Service Class Extension (PosCx). When a client attempts to claim a device that another client is using, PosCx raises this event in the client that currently has a claim on the scanner device to indicate that another client is attempting to claim the device. The current client is expected to either retain its claim ([IOCTL\_POINT\_OF\_SERVICE\_RETAIN\_DEVICE](https://msdn.microsoft.com/library/windows/hardware/dn772117)) or release its claim ([IOCTL\_POINT\_OF\_SERVICE\_RELEASE\_DEVICE](https://msdn.microsoft.com/library/windows/hardware/dn772112)) of the device in response to this event. If the current client does not retain its claim on the device, its **ClaimedBarcodeScanner** object will no longer be valid.

Requirements
------------

**Header:** pointofservicedriverinterface.h





[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bpos\pos%5D:%20ReleaseDeviceRequested%20%20RELEASE:%20%282/18/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





