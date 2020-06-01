# Practice Lab - Create and deploy device profiles

## Summary

In this lab, you will practice creating and applying a device profile.

### Exercise 1: Create and deploy a device profile

### Scenario

A. Datum Corporation’s has decided to manage all members of the development department in the company using Azure Active Directory (Azure AD) and Intune. You have been asked to evaluate the solutions that would enable the users to work effectively and securely on Windows 10 devices managed by Intune and Azure AD. Diego Siciliani has volunteered to help you test and evaluate the solution and provide feedback. He has also given you some initial requirements that must be included in the configuration of Intune:

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
    the **X** in the right upper corner.

### Task 2: Enroll Windows 10 device to Azure AD and Intune using the Settings app

1.  On **LON-CL3**, with the Settings app still open, navigate to the **Accounts** page. 

2.  Select **Access work or school**. In the **Access work or school** section, select **Connect**.

4.  In the **Microsoft account** window, on the **Set up a work or school
    account** page, select **Join this device to Azure Active Directory**.

5.  On the **Let’s get you signed in** page, in the **Work or school account**
    text box, type **DiegoS\@yourtenant.onmicrosoft.com** and select **Next**.

6.  On Enter password page, enter the default tenant password in the text box and then select
    **Sign in**.

7.  Wait a few seconds and then on the **Make sure this is your organization**
    dialog, select **Join**.

8.  On the **You’re all set!** page, select **Done**.

9.  In the **Settings** app, in the **Access work or school** section, verify
    that the device is connected to Azure AD and then close the **Settings**
    app.

### Task 3: Logon to a different Windows 10 device using Azure AD user

1.  Sign out of **LON-CL3**. 

2.  Select **other user**, and in the **Email address** field type
    **DiegoS\@yourtenant.onmicrosoft.com**, and then select **Next**. In the
    Password field, enter the default tenant password and then press **Enter**.

3.  Wait for the profile to be created. It will take around 30-60 seconds.  
    
    _Note: When you are logged on using your Azure AD credentials you will
    benefit from Single-Sign-On (SSO) to Azure AD, Intune and Office 365._

### Task 4: Create device profile based on scenario

1.  On **LON-CL3**, on the taskbar, select **Microsoft Edge**.

2.  In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and
    then press Enter. Note that you are automatically signed in as **DiegoS\@yourtenant.onmicrosoft.com**.

3.  At the upper right of the page, select your account name, and then select
    **Sign in with a different account**.

4.  On the **Microsoft Azure** page, select **Use another account** if needed,
    type **admin\@yourtenant.onmicrosoft.com** for the user name, type the
    tenant Admin, and then select **Sign in**.

5.  In the Microsoft Endpoint Manager admin center, select **Devices** from the 
    navigation bar. 
    On the **Devices | Overview** page, select **Configuration Profiles**.

6.  On the **Devices | Configuration profiles** blade, in the details
    pane, select **Create profile**.

7.  In the **Create a profile** blade, select the following options, and then select **Create**:

-   Platform: **Windows 10 and later**

-   Profile: **Device restrictions**

8.  In the **Basics** blade, enter the following information, and then select **Next**:

    -   Name: **A. Datum Developer - standard**

    -   Description: **Basic restrictions and configuration for Developer in A. Datum.**

9.  On the **Configurations settings** blade, expand **Control Panel and Settings**.
    Select **Block** next to **Gaming** and **Privacy**. 

10. On the **Device restrictions** blade, expand **Start**. Scroll down and
    select **Block** next to **Most used apps** and **Recently added apps**.

11.  On the **Device restrictions** blade, scroll down and expand **Microsoft Defender Antivirus**. Under **Microsoft Defender Antivirus,** scroll down and
    expand **Microsoft Defender Antivirus Exclusions**.

12.  Under **Microsoft Defender Antivirus Exclusions** in the **Files and folders** box, type the following:
    **C:\\DevProjects**.

13.  In the **Processes** box, type the following:
    **DevBuild.exe**. 
    
14.  Then select **Next** three times until you reach the **Review + create** blade. Select **Create**.

### Task 5: Create the Adatum Developer device group

1.  In the Microsoft Endpoint Manager admin center, select **Groups** in the navigation pane.

2.  On the **Groups | All groups** blade, select **New group**.

3.  On the **New Group** blade, enter the following information:

-   Group type: **Security**

-   Group name: **A. Datum Developer devices**

-   Group description: **All Windows 10 devices in A. Datum Developer department**

-   Membership type: **Assigned**

4.  Under **Members**, select **No members selected**. On the **Add members** blade, in the **Search** box type **lon**. Select **LON-CL3** and then choose
    **Select**. Repeat the steps to add **LON-CL4** also as group member.

5.  Back on the **New Group** blade, select **Create**. 

6.  On the **Groups | All groups** blade, verify that the **A. Datum developer devices group** is displayed.

### Task 6: Create a dynamic Azure AD device group

1.  On the **Groups | All Groups** blade, on the details pane, select **New group**.

3.  On the **Group** blade, provide the following values:

    1.  Group type: **Security**

    2.  Group name: **Windows Devices**

    3.  Membership type: **Dynamic Device**

4.  Under **Dynamic Device Members** blade, select **Add dynamic query**. 

5.  On the **Dynamic membership rules** blade, in the **Rule syntax** section, select **Edit**. 
    
6.  In the Edit rule syntax text box, add the following simple membership rule and select **Ok**.

```
    device.deviceOSType -contains "Windows"

```
7.  On the **Dynamic membership rules** blade, select **Save** and then **Create**.

### Task 7: Deploy device profile to Windows 10 device

1.  In the Microsoft Endpoint Manager admin center, select **Home** in the 
    breadcrumb navigation menu and then select **Devices**. On the **Devices | Overview** blade, select **Configuration profiles**.

2.  On the **Devices | Configuration profiles** blade, in the details
    pane, select the **A. Datum Developer – standard** profile.

3.  On the **A. Datum Developer – standard** blade, select **Properties**.  Scroll down to the **Assignments** section, and select **Edit**.

4.  On the **Assignments** blade, select **Select groups to include**.

4.  On the **Select groups to include** blade, in the **Search** box, type **A**. Select **A. Datum Developer devices** and then select **Select**.

5.  Back on the **Device restrictions** blade, select **Review + Save**, then select **Save**.

### Task 8: Verify on the device that device profile is applied

1.  On **LON-CL3**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select the **Accounts** tile and then select **Access
    work or school**.

3.  In the **Access work or school** section, select the **Connected to ADATUM's Azure AD** link and then select **Info**.

4.  In the **Managed by ADATUM** dialog box, select **Info**.  On the Managed by Azure
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
    the **X** in the right upper corner. Close the **Settings** app.



### Exercise 2: Change a deployed device policy  

### Scenario

There was an exception to A. Datum's policies initiated where Developer users should not have the Privacy option blocked in Settings on thier devices. This change should be implemented and tested.

### Task 1: Change setting in assigned profile

1.  On **LON-CL3**, in the Microsoft Endpoint Manager admin center, select 
    **Devices | Configuration profiles** in the breadcrumb navigation pane 

2.  On the **Devices | Configuration profiles** blade, in the details
    pane select **A. Datum Developer - standard**.

3.  On the **A. Datum Developer - standard** blade, select **Properties**. On
    the **A. Datum Developer - standard Properties** blade, on the Configuration settings line, select **Edit**.

4.  On the **Configuration settings** blade, expand **Control Panel and Settings**.
    Select **Not configured** next to **Privacy**. 

5.  Select **Review + save**, then select **Save**.

### Task 2: Force synchronization of policy from Intune console

1.  On **LON-CL3**, in the Microsoft Endpoint Manager admin center, select **Devices** 
    in the navigation pane and then select **All devices**.

2.  In the details pane, select **LON-CL3**. On the **LON-CL3** blade, select
    **Sync** and when prompted select **Yes**.  

    Intune will contact the device and tell it to synchronize all policies. This
    may take up to 5 minutes.

### Task 3: Verify profile change on device

1.  On **LON-CL3** and on the taskbar, select **Start** and then select
    the **Settings** app.

2.  In the **Settings** app, select **Privacy** and verify that all of the
    customization options are back.

3.  Close all windows.

**END OF LAB**