# Ticket #1 — Slow Computer

**Status:** Resolved
**Priority:** Medium
**Category:** Performance
**System:** Windows VM (UTM)

## Issue

User reported that their computer was running slowly. Applications were taking longer than usual to open, and the computer would occasionally freeze for a few seconds.

## What I Checked

I opened Task Manager and checked CPU, memory, and disk usage.

 Resource  Before  After 
 --------  -----:  ----: 
 CPU          17%     5% 
 Memory       78%    63% 
 Disk          5%     2% 

I then checked the Processes tab to see which programs were using the most resources.

**CPU:**

* Windows Module Installer
* Task Manager

**Memory:**

* Windows Module Installer
* Task Manager
* Service Host: Diagnostic Policy Service

## What I Found

Windows was downloading and installing a .NET Framework security update at the time of the investigation.

Windows Module Installer was one of the higher resource-consuming processes while the update was being installed.

## Testing

I waited for the Windows update to finish and checked Task Manager again.

**CPU after update:** 5%

**Memory after update:** 63%

**Disk after update:** 2%

**System responsiveness:** Improved

The system showed lower resource usage after the update completed.

## Resolution

System performance improved after the Windows update finished. CPU, memory, and disk usage all decreased compared to the initial check.


