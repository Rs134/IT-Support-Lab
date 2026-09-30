# Ticket #2 — Application Won't Open

**Status:** Resolved
**Priority:** Medium
**Category:** Software / Application
**System:** Windows VM (UTM)

## Issue

User reported that an application would not open when clicked. No application window or error message appeared.

## Troubleshooting

### 1. Attempted to Open the Application

Double-clicked the application from the Desktop.

**Result:** Nothing appeared on the screen.

### 2. Checked Task Manager

Opened Task Manager and checked the Processes tab for the application and `cmd.exe`.

**Result:** No related process was running.

### 3. Ran the Application from Command Prompt

Opened Command Prompt and ran:

```cmd
HelpDeskTest.bat
```

**Result:**

```text
The system cannot find the path specified.
```

### 4. Checked the Batch File

Used the following command:

```cmd
type HelpDeskTest.bat
```

The file contained:

```text
@echo off
C:\ThisProgramDoesNotExist\TestApp
```

### 5. Checked the Referenced Path

Ran:

```cmd
dir C:\ThisProgramDoesNotExist
```

**Result:**

```text
File not found
```

This confirmed that the path referenced by the application did not exist.

### 6. Corrected the File

Updated `HelpDeskTest.bat` to use the correct application:

```bat
@echo off
echo Help Desk Test Application
pause
```

### 7. Tested the Application Again

Ran:

```cmd
HelpDeskTest.bat
```

**Result:**

```text
Help Desk Test Application
Press any key to continue . . .
```

The application opened successfully.

## Root Cause

The batch file was pointing to a file path that did not exist.

## Resolution

Corrected the invalid file path and verified that the application launched successfully.

## Notes

This was a controlled troubleshooting scenario created in the Windows VM to practice diagnosing an application launch issue.
