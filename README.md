# SMBGhost

## Quick and Dirty POC <- BSOD (CVE-2020-0796)

Python script contains 3 seperate packet payloads.

1. Request <- Start SMB session communication
2. Session <- Session information, negotiate 
3. SMB3 <- SMB3 compression (This is where we send bad offset)

## Usage

```cve-2020-0796.py <serverip>```

**May need to execute the script multiple times, there is no pause or recv check done.** 

## Details

Looking at the script our first packet sends the request, next our 2nd packet sends the negotiate packet. This may not need to be done, but at least the request is sent and response is returned. We do not check for this but can be added easy.

Final packet payload sends the bad offset as shown below. 

![Alt text](/IMGs/offset.jpg?raw=true "SMB3 Compression")

Kernel Debugger sees the crash.

![Alt text](/IMGs/page-fault.jpg?raw=true "Page Fault Windows Kernel")


