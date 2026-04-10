# Boogeyman-2

## Objective
Perform digital forensics on a phishing email and a Windows memory dump
to reconstruct the full malware execution chain using olevba and Volatility3.

### Skills Learned
- Phishing email artifact analysis (Evolution Mail)
- VBA macro extraction with olevba (C2 URL, JS dropper, LOLBin execution)
- MD5 hash extraction for IOC documentation
- Volatility3: pslist, pstree, netscan, filescan, memmap dump
- Process tree reconstruction from memory
- Scheduled task persistence detection via string extraction
- C2 IP identification via windows.netscan

### Tools Used
- olevba (oletools)
- Volatility3 (windows.pslist, windows.pstree, windows.netscan,
  windows.filescan, windows.memmap)
- strings + grep
- Evolution Mail

## Steps
Email opened in Evolution Mail — malicious Word doc attached. olevba revealed
macro with C2 URL (`boogeymanisback` domain), `update.js` dropper, and LOLBin
execution. Memory dump analyzed with Volatility3 — `updater.exe` identified
via pstree. C2 IP confirmed via netscan. File location found via filescan.
Process memory dumped, strings extracted — scheduled task revealed via
`strings | grep schtasks`.

*Ref 1: olevba output — C2 URL, update.js path, LOLBin execution*
*Ref 2: Volatility3 pstree and netscan confirming updater.exe and C2 IP*
