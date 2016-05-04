---
author: joshbax-msft
title: Named Pipe State
description: Named Pipe State
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ed8d074b-2b7b-4673-a67f-131ff942a57d
---

# Named Pipe State


This automated test validates the behavior of all named-pipe operations for each distinct state of a pipe instance.

The test evaluates the following states:

-   **NO\_INSTANCE.** The instance does not exist.

-   **SERVER\_ONLY.** The server side of the instance has been created.

-   **CONNECTED.** The client side has been created and connects to server.

-   **CLIENT\_DISCONNECTED.** The client disconnects by closing its handle.

-   **SERVER\_DISCONNECTED.** The server disconnects by using the **DisconnectNamedPipe** API.

The named-pipe operations that the test evaluates include the following:

-   **Server CreateNP.** Server calls **CreateNamedPipe**.

-   **Server ConnectNP.** Server calls **ConnectNamedPipe**.

-   **Server DisconnectNP.** Server calls **DisconnectNamedPipe**.

-   **Server CloseHandle.** Server calls **CloseHandle**.

-   **Client CreateFile.** Client calls **CreateFile**.

-   **Client WaitNP.** Client calls **WaitNamedPipe**.

-   **Client CallNP.** Client calls **CallNamedPipe**.

-   **Client CloseHandle.** Client calls **CloseHandle**.

-   **Server Write.** Server calls **WriteFile**.

-   **Server Read.** Server calls **ReadFile**.

-   **Client Write.** Client calls **WriteFile**.

-   **Client Read.** Client calls **ReadFile**.

The test selects each state in random order and calls each action in random order. If any action moves the pipe away from the current state, the test brings it back to the current state.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Filter.Driver.AntiVirus.MiniFilter Filter.Driver.AntiVirus.NamedPipeAndMailSlots Filter.Driver.FileSystem.MiniFilter Filter.Driver.FileSystem.NamedPipeAndMailSlots</p>
<p>[See the filter hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254485)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows 8 (x64) Windows 8 (x86) Windows Server 2012 (x64) Windows 8.1 x64 Windows 8.1 x86 Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~30 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


For more information about requirements, see [File System Testing Prerequisites](file-system-testing-prerequisites.md).

To run this test, follow these steps:

1.  Copy the test binaries that are listed in the **File List** section locally.

2.  Run the following command: **npstate.exe regress**

3.  The expected Pass count is 600. Inspect the log file for the presence of +SEV error tags. If you do not find any instances of this tag, the test has passed.

## Troubleshooting


For troubleshooting information, see [Troubleshooting File System Testing](troubleshooting-file-system-testing.md).

This test returns Pass or Fail. To review test details, review the test log from Windows Hardware Certification Kit (Windows HCK) Studio.

## More information


### Command syntax

This test accepts a single parameter that indicates the server host name.

### File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Npstate.exe</p></td>
<td><p>[WTT\TestBinRoot]\NTTEST\BASETEST\kernel\misc\npstate.exe</p></td>
</tr>
<tr class="even">
<td><p>Ntlog.dll</p></td>
<td><p>[WTT\OsBinRoot]\ddk_flat\DTM\tests\ntlog\ntlog.dll</p></td>
</tr>
<tr class="odd">
<td><p>Ntlogger.ini</p></td>
<td><p>[WTT\OsBinRoot]\ddk_flat\DTM\tests\ntlog\ntlogger.ini</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Named%20Pipe%20State%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



