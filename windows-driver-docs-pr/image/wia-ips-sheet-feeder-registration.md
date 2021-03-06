---
title: WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION
description: The WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION property contains the registration, or alignment and edge detection, for documents that are placed on the flatbed of a scanner. The WIA minidriver creates and maintains this property.
ms.assetid: d97d5784-3360-48a3-a24e-97b4238c42f5
keywords: ["WIA_IPS_SHEET_FEEDER_REGISTRATION Imaging Devices"]
topic_type:
- apiref
api_name:
- WIA_IPS_SHEET_FEEDER_REGISTRATION
api_location:
- Wiadef.h
api_type:
- HeaderDef
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION


The WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION property contains the registration, or alignment and edge detection, for documents that are placed on the flatbed of a scanner. The WIA minidriver creates and maintains this property.

Property Type: VT\_I4

Valid Values: WIA\_PROP\_NONE

Access Rights: Read-only

Remarks
-------

The WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION property indicates how a document is horizontally positioned on the scanning head of a handheld or sheet-fed scanner. You can use WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION to predict where across the scanning head a document is placed.

The following table describes the constants that are valid with WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Constant</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LEFT_JUSTIFIED</p></td>
<td><p>The document is positioned to the left with respect to the scanning head.</p></td>
</tr>
<tr class="even">
<td><p>CENTERED</p></td>
<td><p>The document is centered on the scanning head.</p></td>
</tr>
<tr class="odd">
<td><p>RIGHT_JUSTIFIED</p></td>
<td><p>The document is positioned to the right with respect to the scanning head.</p></td>
</tr>
</tbody>
</table>

 

For scanners that support more than one scanning head, the WIA\_IPS\_SHEET\_FEEDER\_REGISTRATION property is relative to the topmost scanning head. This property is mandatory for sheet-fed, scroll-fed, and handheld scanners.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Available in Windows Vista and later operating systems. For Windows XP, use the WIA_DPS_SHEET_FEEDER_REGISTRATION property instead.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Wiadef.h (include Wiadef.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**WIA\_DPS\_SHEET\_FEEDER\_REGISTRATION**](wia-dps-sheet-feeder-registration.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bimage\image%5D:%20WIA_IPS_SHEET_FEEDER_REGISTRATION%20%20RELEASE:%20%2811/13/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





