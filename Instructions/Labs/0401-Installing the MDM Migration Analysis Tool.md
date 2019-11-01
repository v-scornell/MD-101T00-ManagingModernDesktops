# Practice Lab - Installing the MDM Migration Analysis Tool (MMAT)

## Summary

In this lab, you will practice using the MDM Migration Analysis Tool to review Group Polices that can be migrated to Intune.

### Scenario

Your organization is planning a Microsoft Intune implimentation. You have been asked to identify current configurations being applied by Group Policy that can be migrated to Intune. You have decided to review the client GPOs on LON-CL1.

### Task 1: Prepare the Windows 10 device for the MMAT tool

1.  On **LON-CL1**, sign-in as **adatum\\administrator** using **Pa55w.rd** as
    the password.

2.  Right-click the **Start** button and select **Windows PowerShell (Admin)**.

3.  In the PowerShell console, type the following and then press Enter:
    **Get-WindowsCapability -Name RSAT\* -Online \| Add-WindowsCapability
    -Online**

4.  This will install Remote Server Administration Tools (RSAT). Wait for the
    command to complete. It may take up to 5 minutes. **Note**: RSAT is required
    for MMAT to function.

5.  Close the PowerShell window.

### Task 2: Download the MMAT tool from GitHub

1.  On **LON-CL1**, on the taskbar, open **Microsoft Edge**.

2.  In Microsoft Edge, type **https://github.com/WindowsDeviceManagement/MMAT**
    in the address bar, and then press Enter.

3.  On the Github page, click the **Clone or download** link and select
    **Download ZIP**.

4.  When prompted click **Save** and close Microsoft Edge.

### Task 3: Install the MMAT tool on the Windows 10 device

1.  On the Task bar, click the **File Explorer** icon and expand **This PC.**

2.  In **File Explorer**, click **Downloads** and right-click the
    **MMAT-master.zip** file, and then select **Extract All**. In the **Select a
    Destination and Extract Files** dialog box, type **C:\\** and then click
    **Extract**.

3.  Close File Explorer.

### Task 4: Report on an existing Group Policy Object (GPO)

In this task, you are going to run the MMAT tool on a Windows 10 device and
report on the settings in the Group Policy Objects applied to that device. The
MMAT will report whether or not it is possible to migrate those settings
directly to Intune.

1.  Right-click the **Start** button and select **Windows PowerShell (Admin)**.

2.  In the PowerShell console, type the following and then press Enter:
    **set-location -path c:\\mmat-master**

3.  In the PowerShell console, type the following and then press Enter:
    **Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Process**. When
    prompted type **Y** and press Enter.

4.  In the PowerShell console, type the following and then press Enter:
    **\$VerbosePreference="Continue"**

5.  In the PowerShell console, type the following and then press Enter:
    **.\\Invoke-MdmMigrationAnalysisTool.ps1 -collectGPOReports
    -runAnalysisTool**. When prompted, type **R** and press Enter.  
    When **Invoke-MdmMigrationAnalysisTool.ps1** is completed, it will generate
    the following files in the **MMAT-master** folder:

-   MDMMigrationAnalysis.html

-   MDMMigrationAnalysis.xml

-   MDMMigrationAnalysisTool.txt

-   MDMMigrationAnalysisTool-PS1-Invocation.txt

-   GPOReport.{31B2F340-016D-11D2-945F-00C04FB984F9}.xml

-   MDMMigrationAnalysisToolReportInformation.xml

-   MachineRsop.txt

-   UserRsop.TXT

1.  Open File Explorer and browse to the **C:\\MMAT-master** folder.

2.  In the **C:\\MMAT-master** folder, double-click the
    **MDMMigrationAnalysis.html** file.

3.  Examine the content of the file and verify that **Security Account
    Policies**, **Windows Firewall Policies with Advanced Security** and **ADMX
    backed policies (System/Power Management)** are all listed as supported.
    This means that the policies can be directly migrated to Intune. Also notice
    that the mobile device management (MDM) cloud solution provider (CSP)
    setting that you should use is displayed next to Group Policy Setting.

4.  Finally notice the settings displayed under **NOT SUPPORTED: Security
    Account Policies**. For now, they cannot be migrated to Intune.

**END OF LAB**