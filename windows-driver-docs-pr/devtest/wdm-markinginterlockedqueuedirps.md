---
title: MarkingInterlockedQueuedIrps rule (wdm)
description: The MarkingInterlockedQueuedIrps rule specifies that the driver correctly marks the IRP as pending before it queues it in an interlocked fashion for further processing.
ms.assetid: a065b28f-f02a-45af-b9d9-754a36519b99
keywords: ["MarkingInterlockedQueuedIrps rule (wdm)"]
topic_type:
- apiref
api_name:
- MarkingInterlockedQueuedIrps
api_type:
- NA
---

# MarkingInterlockedQueuedIrps rule (wdm)


The **MarkingInterlockedQueuedIrps** rule specifies that the driver correctly marks the IRP as pending before it queues it in an interlocked fashion for further processing.

This rule also specifies that the driver calls [**IoMarkIrpPending**](https://msdn.microsoft.com/library/windows/hardware/ff549422) and correctly marks the IRP as pending before it calls any of the following functions to add the IRP to an interlocked queue:

-   [**ExInterlockedInsertHeadList**](https://msdn.microsoft.com/library/windows/hardware/ff545397)

-   [**ExInterlockedInsertTailList**](https://msdn.microsoft.com/library/windows/hardware/ff545402)

-   [**ExInterlockedPushEntryList**](https://msdn.microsoft.com/library/windows/hardware/ff545418)

Drivers should call [**IoMarkIrpPending**](https://msdn.microsoft.com/library/windows/hardware/ff549422) before adding an IRP that requires more processing to an interlocked queue. Otherwise, an IRP could be dequeued, completed by another driver routine, and freed by the system before the call to **IoMarkIrpPending** occurs, thereby causing a crash.

For more information, see [**Synchronizing IRP Cancellation**](https://msdn.microsoft.com/library/windows/hardware/ff564531).

|              |     |
|--------------|-----|
| Driver model | WDM |

How to test
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">At compile time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Run [Static Driver Verifier](https://msdn.microsoft.com/library/windows/hardware/ff552808) and specify the <strong>MarkingInterlockedQueuedIrps</strong> rule.</p>
Use the following steps to run an analysis of your code:
<ol>
<li>[Prepare your code (use role type declarations).](https://msdn.microsoft.com/library/windows/hardware/hh454281#preparing-your-source-code)</li>
<li>[Run Static Driver Verifier.](https://msdn.microsoft.com/library/windows/hardware/hh454281#running-static-driver-verifier)</li>
<li>[View and analyze the results.](https://msdn.microsoft.com/library/windows/hardware/hh454281#viewing-and-analyzing-the-results)</li>
</ol>
<p>For more information, see [Using Static Driver Verifier to Find Defects in Drivers](https://msdn.microsoft.com/library/windows/hardware/hh454281).</p></td>
</tr>
</tbody>
</table>

Applies to
----------

[**ExInterlockedInsertHeadList**](https://msdn.microsoft.com/library/windows/hardware/ff545397)
[**ExInterlockedInsertTailList**](https://msdn.microsoft.com/library/windows/hardware/ff545402)
[**ExInterlockedPushEntryList**](https://msdn.microsoft.com/library/windows/hardware/ff545418)
[**IoMarkIrpPending**](https://msdn.microsoft.com/library/windows/hardware/ff549422)
[**RemoveHeadList**](https://msdn.microsoft.com/library/windows/hardware/ff561032)
See also
--------

[**MarkIrpPending**](wdm-markirppending.md)
[**Synchronizing IRP Cancellation**](https://msdn.microsoft.com/library/windows/hardware/ff564531)
 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bdevtest\devtest%5D:%20MarkingInterlockedQueuedIrps%20rule%20%28wdm%29%20%20RELEASE:%20%281/17/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




