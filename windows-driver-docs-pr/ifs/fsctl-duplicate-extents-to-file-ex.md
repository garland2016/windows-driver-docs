---
title: FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE\_EX control code
description: The FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE\_EX control code instructs the file system to copy a range of file bytes on behalf of an application. The destination file may be the same as, or different from, the source file.
ms.assetid: B13C6415-5593-43CF-90AC-7D2DC844EC41
keywords: ["FSCTL_DUPLICATE_EXTENTS_TO_FILE_EX control code Installable File System Drivers"]
topic_type:
- apiref
api_name:
- FSCTL_DUPLICATE_EXTENTS_TO_FILE_EX
api_location:
- WinIoctl.h
- Ntifs.h
api_type:
- HeaderDef
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE\_EX control code


The [**FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE\_EX**](fsctl-duplicate-extents-to-file-ex.md) control code instructs the file system to copy a range of file bytes on behalf of an application. The destination file may be the same as, or different from, the source file.

To perform this operation, call the [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) function with the following parameters.

```ManagedCPlusPlus
BOOL 
   WINAPI 
   DeviceIoControl( (HANDLE)       hDevice,         // handle to device
                    (DWORD)        FSCTL_DUPLICATE_EXTENTS_TO_FILE_EX, // dwIoControlCode
                    (LPDWORD)      lpInBuffer,      // input buffer
                    (DWORD)        nInBufferSize,   // size of input buffer
                    (LPDWORD)      lpOutBuffer,     // output buffer
                    (DWORD)        nOutBufferSize,  // size of output buffer
                    (LPDWORD)      lpBytesReturned, // number of bytes returned
                    (LPOVERLAPPED) lpOverlapped );  // OVERLAPPED structure
```

Parameters
----------

*hDevice* \[in\]  
A handle to the device. To obtain a device handle, call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function.

*dwIoControlCode* \[in\]  
The control code for the operation. Use [**FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE\_EX**](fsctl-duplicate-extents-to-file-ex.md) for this operation.

*lpInBuffer*   
A pointer to a **DUPLICATE\_EXTENTS\_DATA\_EX** structure that specifies the source file, the source byte range, and the destination file offset to copy the range to.

*nInBufferSize* \[in\]  
The size of the input buffer, in bytes.

*lpOutBuffer* \[out\]  
Not used with this operation. Set to NULL.

*nOutBufferSize* \[in\]  
Not used with this operation. Set to zero (0).

*lpBytesReturned* \[out\]  
A pointer to a variable that receives the size of the data stored in the output buffer, in bytes.

If the output buffer is too small, the call fails, [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_INSUFFICIENT\_BUFFER**, and *lpBytesReturned* is zero.

If *lpOverlapped* is **NULL**, *lpBytesReturned* cannot be **NULL**. Even when an operation returns no output data and *lpOutBuffer* is **NULL**, [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) makes use of *lpBytesReturned*. After such an operation, the value of *lpBytesReturned* is meaningless.

If *lpOverlapped* is not **NULL**, *lpBytesReturned* can be **NULL**. If this parameter is not **NULL** and the operation returns data, *lpBytesReturned* is meaningless until the overlapped operation has completed. To retrieve the number of bytes returned, call [**GetOverlappedResult**](https://msdn.microsoft.com/library/windows/desktop/ms683209). If the *hDevice* parameter is associated with an I/O completion port, you can retrieve the number of bytes returned by calling [**GetQueuedCompletionStatus**](https://msdn.microsoft.com/library/windows/desktop/aa364986).

*lpOverlapped* \[in\]  
A pointer to an [**OVERLAPPED**](https://msdn.microsoft.com/library/windows/desktop/ms684342) structure.

If *hDevice* was opened without specifying **FILE\_FLAG\_OVERLAPPED**, *lpOverlapped* is ignored.

If *hDevice* was opened with the **FILE\_FLAG\_OVERLAPPED** flag, the operation is performed as an overlapped (asynchronous) operation. In this case, *lpOverlapped* must point to a valid [**OVERLAPPED**](https://msdn.microsoft.com/library/windows/desktop/ms684342) structure that contains a handle to an event object. Otherwise, the function fails in unpredictable ways.

For overlapped operations, [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) returns immediately, and the event object is signaled when the operation has been completed. Otherwise, the function does not return until the operation has been completed or an error occurs.

Return value
------------

If the operation completes successfully, [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) returns a nonzero value.

If the operation fails or is pending, [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) returns zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

For the implications of overlapped I/O on this operation, see the Remarks section of the [**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216) topic.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">WinIoctl.h;
Ntifs.h</td>
</tr>
</tbody>
</table>

## See also


[**DeviceIoControl**](https://msdn.microsoft.com/library/windows/desktop/aa363216)

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bifsk\ifsk%5D:%20FSCTL_DUPLICATE_EXTENTS_TO_FILE_EX%20control%20code%20%20RELEASE:%20%281/9/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





