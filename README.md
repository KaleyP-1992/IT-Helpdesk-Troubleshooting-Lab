# IT Help Desk Troubleshooting Lab

## Project Overview

This project demonstrates hands-on IT Help Desk troubleshooting using Windows Server 2025 in a VirtualBox environment. I investigated common technical issues involving network connectivity, DNS, Windows services, system startup events, and disk health.

The goal was to develop practical troubleshooting skills, practice using Windows administrative tools, and document technical findings.

## Lab Environment

- Windows Server 2025
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- Domain: `helpdesklab.local`
- Server: `PT-DC01`
- Windows PowerShell
- DNS Manager
- Event Viewer
- Windows Services

## Help Desk Troubleshooting Scenarios

### Ticket #001: Network Connectivity Troubleshooting

**Issue:** Verify that the server has network connectivity and can communicate with external resources.

**Tools and Commands:**
- `ipconfig /all`
- `ping 10.0.2.2`
- `ping 8.8.8.8`
- `ping google.com`

**Resolution:** Confirmed successful network connectivity with no packet loss during the tests.

### Ticket #002: DNS Resolution Troubleshooting

**Issue:** Investigate DNS lookup timeouts and a failed DNS forwarder diagnostic.

**Tools and Commands:**
- `nslookup google.com`
- `nslookup google.com 8.8.8.8`
- `dcdiag /test:dns /v`
- DNS Manager

**Resolution:** Identified an unresponsive DNS forwarder, configured a working forwarder, and verified that DNS diagnostic tests passed.

### Ticket #003: Print Spooler Troubleshooting

**Issue:** Simulate a stopped Print Spooler service and restore functionality.

**Tools and Commands:**
- `services.msc`
- `sc query spooler`
- `net start spooler`

**Resolution:** Restarted the Print Spooler service and verified that its status returned to RUNNING.

### Ticket #004: Event Viewer Investigation

**Issue:** Verify Windows service activity through system event logs.

**Tools:**
- Windows Event Viewer
- Windows Logs → System
- Event ID 7036

**Resolution:** Located Service Control Manager events documenting Print Spooler service state changes.

### Ticket #005: Windows Startup Investigation

**Issue:** Investigate startup activity and check for unexpected shutdowns.

**Tools:**
- Task Manager → Startup apps
- Event Viewer
- Event IDs 6005, 6006, and 6008

**Findings:** Reviewed startup applications, confirmed an Event Log service startup event, and found no Event ID 6008 entries in the filtered logs. No configuration changes were required.

### Ticket #006: Disk Health and File System Troubleshooting

**Issue:** Investigate Disk Event ID 34, reporting that the driver disabled write caching.

**Tools and Commands:**
- Event Viewer
- `Get-PhysicalDisk`
- `Get-PSDrive C`
- `chkdsk C: /scan`

**Findings:**
- Disk health reported Healthy.
- Available storage: 29.63 GB.
- File system: NTFS.
- CHKDSK reported no file system problems.

**Resolution:** Completed disk diagnostics without identifying a reported disk health or file system problem. No repairs were performed.

## Skills Demonstrated

- Windows Server administration
- Network connectivity testing
- DNS troubleshooting and configuration
- Active Directory DNS verification
- Windows service troubleshooting
- Event Viewer log analysis
- PowerShell diagnostics
- Disk health verification
- Technical documentation
- Help Desk ticket investigation

## Screenshots

Supporting screenshots are available in the [Screenshots](Screenshots) folder.

## Project Outcome

Successfully completed six simulated Help Desk troubleshooting scenarios using Windows Server 2025. This project demonstrates a structured approach to investigating technical issues, verifying results, and documenting findings in a virtualized enterprise-style environment.
