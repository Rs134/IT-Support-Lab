# Ticket #4 — File and Folder Access Problem

**Status:** Resolved
**Priority:** Medium
**Category:** File Access / Permissions
**System:** Windows VM (UTM)
**Scenario:** Controlled troubleshooting lab

## Issue

User reported that they could see a file but could not open or modify it. Windows displayed an **Access Denied** message.

## Troubleshooting

1. Created a test folder and file on the Windows desktop:

   * `HelpDeskLab`
   * `CompanyFile.txt`

2. Ran `whoami` to confirm the Windows account being used.

3. Ran `icacls` against the test file to check its current permissions.

4. The account initially had inherited Full Control:

   * `(I)(F)` = Inherited Full Control

5. A Deny permission was intentionally added to simulate the user's access problem.

6. Attempted to open the file and received an **Access Denied** message.

7. Ran `icacls` again to investigate the permissions.

8. Found two permission entries for the user:

   * `(N)` = No access / explicit Deny
   * `(I)(F)` = Inherited Full Control

9. Determined that the explicit Deny permission was overriding the inherited Full Control permission.

10. Removed the incorrect Deny entry using:

11. Ran `icacls` again and confirmed that the inherited Full Control permission remained.

12. Opened `CompanyFile.txt` and successfully edited and saved the file.

## Root Cause

An explicit **Deny** permission had been assigned to the user's account. The Deny entry overrode the account's inherited Full Control permission and caused Windows to return **Access Denied**.

## Resolution

Removed the incorrect explicit Deny permission while leaving the inherited Full Control permission intact.

## Verification

Confirmed that:

* The file could be opened.
* The file could be edited.
* Changes could be saved.
* The inherited `(I)(F)` permission remained in place.
* The Access Denied error was resolved.


