# Practice Lab - Create and deploy device profiles

## Summary

In this lab, you will practice creating and applying a device profile.

### Exercise 1: Create and deploy a device profile

### Scenario

A. Datum Corporation’s has decided to manage all developers in the company using Azure Active Directory (Azure AD) and Intune. You have been asked to evaluate the solutions that would enable the developers to work effectively and securely on Windows 10 devices managed by Intune and Azure AD. The head of the developer department, Brenda Mueller, has volunteered to help you test and evaluate the solution and provide feedback. She has also given you some initial requirements that must be included in the configuration of Intune:

•	It should not be possible to access Gaming or Privacy in the Settings app.
•	The C:\DevProjects folder should be excluded from Windows Defender.
•	The process devbuild.exe must be excluded from Windows Defender.
•	Most used apps and Recently added apps should not be displayed on the Start menu.


#### Task 1: Verify settings on device before enrollment

1.  Sign in to **LON-CL3** as **Admin** with the password **Pa55w.rd**.

2.  On **LON-CL3**, on the taskbar, select **Start** and then select the
    **Settings** app.

3.  In the **Settings** app, verify that you can see the **Gaming** tile.

4.  Select **Privacy** and verify that you can see several customization
    options.

5.  Select the left arrow in the upper left corner.

6.  Select the **Personalization** tile and then select **Start**. Verify that
    **Show recently used apps** is set to **On**.

7.  Select the left arrow in the upper left corner.

8.  In the **Settings** app, select **Update and Security**.

9.  On the **Update & Security** page, select **Windows Security** and then
    **Open Windows Security**.

10. On the **Windows Security** page, select the menu and then select the **Virus
    & threat protection**.

11. On the **Virus & threat protection** page, select **Manage settings** under
    **Virus & threat protection settings**. Scroll down to **Exclusions** and
    select **Add or remove exclusions**.

12. On the **Exclusion** page, verify that no exclusions have been configured.

13. Close the **Exclusions page** and the **Windows Security** page by selecting
    the **X** in the right upper corner twice.

### Task 2: Enroll Windows 10 device to Azure AD and Intune using the Settings app

1.  On **LON-CL3**, with the Settings app still open, navigate to the **Accounts** page. 

2.  Select **Access work or school**. In the **Access work or school** section, select **+Connect**.

4.  In the **Microsoft account** window, on the **Set up a work or school
    account** page, select **Join this device to Azure Active Directory**.

5.  On the **Let’s get you signed in** page, in the **Work or school account**
    text box, type **DiegoS\@yourtenant.onmicrosoft.com**

6.  On Enter password page, enter the default tenant password in the text box and then select
    **Sign in**.

7.  Wait a few seconds and then on the **Make sure this is your organization**
    dialog, select **Join**.

8.  On the **You’re all set!** page, select **Done**.

9.  In the **Settings** app, in the **Access work or school** section, verify
    that the device is connected to Azure AD and then close the **Settings**
    app.

10. Right-click the **Start** button and select **Windows PowerShell (Admin)**,
    when prompted select **Yes.**

11. In the PowerShell console, type the following and then press Enter:
```
    REG ADD HKLM\SOFTWARE\Policies\Microsoft\PassportForWork /v Enabled /t REG_DWORD /d 0 /f 

``` 
    
_Note: This will disable Windows Hello on the device and will disable the forced
    creation of a PIN when logging on to the device the first time using an
    Azure AD account. This will also disable the need for access to a mobile
    phone as this requires validation of the Azure AD account being used. You
    can also disable the use of Windows Hello by creating a policy in Intune._

### Task 3: Logon to a different Windows 10 device using Azure AD user

1.  Sign out of **LON-CL3**. 

2.  Select **other user**, and in the **Email address** field type
    DiegoS**\@yourtenant.onmicrosoft.com**, and then select **Next**. In the
    Password field, type **Pa55w.rd** and then press Enter.

3.  Wait for the profile to be created. It will take around 30-60 seconds.  
    **Note:** When you are logged on using your Azure AD credentials you will
    benefit from Single-Sign-On (SSO) to Azure AD, Intune and Office 365.


### Task 4: Create device profile based on scenario

1.  On **LON-CL3**, on the taskbar, select **Microsoft Edge**.

2.  In Microsoft Edge, type **https://portal.azure.com** in the address bar, and
    then press Enter.

3.  Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant
    Admin password.

4.  In the Azure portal, select **Intune** under Azure Services. 
    On the **Microsoft Intune** overview page, select **Device configuration**.

5.  On the **Device configuration** blade, select **Profiles**. In the details
    pane, select **+ Create profile**.

6.  In the **Create profile** blade, enter/select the following information:

-   Name: **A. Datum developers - standard**

-   Description: **Basic restrictions and configuration for developers in A.
    Datum.**

-   Platform: **Windows 10 and later**

-   Profile type: **Device restrictions**

7.  On the **Device restrictions** blade, select **Control Panel and Settings**.
    Select **Block** next to **Gaming** and **Privacy**. Then select **OK**.

8.  Back on the **Device restrictions** blade, select **Start**. Scroll down and
    select **Block** next to **Most used apps** and **Recently added apps**.
    Then select **OK**.

9.  Back on the **Device restrictions** blade, scroll down and select **Windows
    Defender Antivirus**. On the **Windows Defender Antivirus,** scroll down and
    select **Windows Defender Antivirus Exclusions**.

10.  On the **Windows Defender Antivirus Exclusions** blade, in the **Files and
    folders** box, type the following and then select **Add**:
    **C:\\DevProjects**.

11.  In the **Processes** box, type the following and then select **Add**:
    **DevBuild.exe**. Then select **OK** twice.

12.  Back on the **Device restrictions** blade, select **OK** twice and then select
    **Create**.

### Task 5: Create the Adatum developer device group

1.  In the Azure portal, select the ellipsis in the top left and select **Azure Active Directory**.  In the navigation
    pane, and then **Groups**.

2.  On the **Groups** blade, select **+ New group**.

3.  On the **Group** blade, enter/select the following information:

-   Group type: **Security**

-   Group name: **A. Datum developer devices**

-   Group description: **All Windows 10 devices in A. Datum developer
    department**

-   Membership type: **Assigned**

4.  Select **Members** and on the **Select members** blade, in the **Search by
    name or mail address**, type **lon**. Select **LON-CL3** and then select
    **Select**.

5.  Back on the **Group** blade, select **Create**. Close the **Group** blade by
    selecting the **X** in the upper right corner.

6.  On the **Groups – All groups** blade, verify that the **A. Datum developer
    devices group** is displayed.

### Task 6: Create a dynamic Azure AD device group

1.  In **LON-CL3**, in the Azure portal, scroll the page to the left and then in
    the **Azure Active Directory** blade select **Groups**.

2.  On the **Group** blade, on the details pane, select **+New group**.

3.  On the **Group** blade, provide the following values:

    1.  Group type: **Security**

    2.  Group name: **Windows Devices**

    3.  Membership type: **Dynamic Device**

4.  On the **Group** blade, select **Dynamic device members**.

5.  Select **Add dynamic query**. On the **Dynamic membership rules** blade, in the **Rule syntax** section,
    select **Edit**. 
    
6.  In the Edit rule syntax text box, add the following simple membership rule and select **Ok**.

```
    device.deviceOSType -contains "Windows"

```
7.  On the **Dynamic membership rules** blade, select **Save** and then **Create**.

### Task 7: Deploy device profile to Windows 10 device

1.  In the Azure portal, select **Home** in the breadcrumb navigation menu and then select
    **Intune**. On the **Microsoft Intune - Overview** blade, select **Device configuration**.

2.  On the **Device configuration** blade, select **Profiles**. In the details
    pane, select the **A. Datum developers – standard** profile.

3.  On the **A. Datum developers – standard** blade, select **Assignments**. On
    the **A. Datum developers – standard – Assignments** blade, select **Select
    groups to include**.

4.  On the **Select members** blade, in the **Search by name or mail address**,
    type **A**. Select **A. Datum developer devices** and then select **Select**.

5.  Back on the **A. Datum developers – standard** blade, select **Save**.

### Task 8: Verify on the device that device profile is applied

1.  On **LON-CL3**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select the **Accounts** tile and then select **Access
    work or school**.

3.  In the **Access work or school** section, select the **Connected to Contoso’s
    Azure AD** link and then select **Info**.

4.  In the **Managed by Contoso** dialog box, select **Info**.  On the Managed by Azure
    AD page, select **Sync**. Wait for the synchronization to complete.  
    
    _Note: The sync progress should only take a few seconds, however it may take up
    to 15 minutes before the profile is applied to Windows 10 device. Signing out or
    rebooting can accelerate this process._

5.  Close the **Settings** app, and open it again. Verify that the **Gaming**
    and **Privacy** tile has been removed.

6.  Select the **Personalization** tile and then select **Start**. Verify that
    **Show recently used apps** and **Show most used apps** are set to **Off**.
    Select the **left arrow **in the upper left corner.

7.  In the **Settings** app, select **Update and Security**.

8.  On the **Update & Security** page, select **Windows Security** and then
    **Open Windows Security**.

9.  On the **Windows Security** page, select the menu and then select the **Virus
    & threat protection**.

10. On the **Virus & threat protection** page, select **Manage settings** under
    **Virus & threat protection settings**. Scroll down to **Exclusions** and
    select **Add or remove exclusions**.

11. On the **Exclusion** page, verify that **C:\\DevProjects** and
    **DevBuild.exe** are displayed.

12. Close the **Exclusions page** and the **Windows Security** page by selecting
    the **X** in the right upper corner twice.



### Exercise 2: Change deployed device policy  

### Scenario

There was an exception to A. Datum's policies initiated where developers should not have the Privacy option blocked in Settings on thier devices. This change should be implemented and tested.

### Task 1: Change setting in assigned profile

1.  On **LON-CL3**, in the Azure portal, select **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, select **Device
    configuration**.

2.  On the **Device configuration** blade, select **Profiles**. In the details
    pane, select **A. Datum developers - standard**.

3.  On the **A. Datum developers - standard** blade, select **Properties**. On
    the **A. Datum developers - standard** – **Properties** blade, select
    **Settings 6 configured**.

4.  On the **Device restrictions** blade, select **Control Panel and Settings**.
    Select **Not configured** next to **Privacy**. Then select **OK** twice.

5.  Back on the **A. Datum developers - standard** – **Properties** blade, select
    **Save**.

### Task 2: Force synchronization of policy from Intune console

1.  On **LON-CL3**, in the Azure portal, scroll left to the **Microsoft Intune**
    blade, select **Devices** and then select **All devices**.

2.  In the details pane, select **LON-CL3**. On the **LON-CL3** blade, select
    **Sync** and when prompted select **Yes**.  

    Intune will contact the device and tell it to synchronize all policies. This
    may take up to 5 minutes.

### Task 3: Verify profile change on device

1.  Switch toon **LON-CL3** and on the taskbar, select **Start** and then select
    the **Settings** app.

2.  In the **Settings** app, select **Privacy** and verify that all of the
    customization options are back.

3.  Close the **Settings** app.

**END OF LAB**