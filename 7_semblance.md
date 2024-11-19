# How to execute the PowerShell script, including steps to resolve potential access issues:

---

## Executing PowerShell Script

## Prerequisites
- Windows 10 or Windows 11
- PowerShell 5.1 or later

## Script Overview
This PowerShell script extracts and displays metadata entries from specified log files. It checks for entries within the last 24 hours and outputs relevant information.

## Steps to Execute the Script

### 1. Save the Script
Save the PowerShell script to a file, for example, `extract_metadata.ps1`.

### 2. Open PowerShell with Administrative Privileges
To ensure you have the necessary permissions, open PowerShell as an administrator:
1. Click on the **Start** menu.
2. Type `PowerShell`.
3. Right-click on **Windows PowerShell** and select **Run as administrator**.

### 3. Set Execution Policy
If you encounter an error regarding script execution policies, you may need to change the execution policy:
1. In the PowerShell window, run the following command:
   ```powershell
   Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```
2. When prompted, type `Y` and press **Enter** to confirm.

### 4. Execute the Script
Navigate to the directory where your script is saved and run it:
1. Use the `cd` command to change to the script's directory. For example:
   ```powershell
   cd C:\Users\rifat.sahin\Downloads
   ```
2. Execute the script by typing:
   ```powershell
   .\extract_metadata.ps1
   ```

### Troubleshooting Access Issues
If you encounter issues with PowerShell not having the right access to execute the script, follow these steps:

1. **Check User Permissions**:
   - Ensure your user account has the necessary permissions to access the log files and execute scripts.

2. **Run PowerShell as Administrator**:
   - Always run PowerShell with administrative privileges to avoid permission issues.

3. **Adjust Execution Policy**:
   - If the execution policy is too restrictive, adjust it as mentioned above.

4. **File Permissions**:
   - Ensure the script file and log files have the appropriate permissions set. You can adjust file permissions by right-clicking the file, selecting **Properties**, and modifying the permissions under the **Security** tab.

### Example Output
After running the script, you should see output similar to the following:
```
Results for main.log:
logfile=main.log logdate=2024-11-18T12:34:56 mymetadata=example1
logfile=main.log logdate=2024-11-18T14:22:33 mymetadata=example2
...
Results for sublog1.log:
logfile=sublog1.log logdate=2024-11-18T09:15:42 mymetadata=example3
...
```

If you have any questions or run into issues, feel free to reach out for help!

---
