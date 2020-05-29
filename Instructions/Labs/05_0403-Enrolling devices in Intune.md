# Practice Lab - Enrolling devices in Microsoft Intune

## Summary

In this lab, you will practice enrolling a client in Azure AD and Microsoft Intune reviewing the post-enrollment experience.

### Scenario

Joni Sherman will be testing the process of joining a device, LON-CL4, to the Azure Active Directory and enrolling in Microsoft Intune. After IT verifies the device is not currently joined, Joni should login using her credentials. 
Joni should then reboot the device to verify organizational settings, such as Windows Hello, are enabled. 

### Task 1: Verify that a Windows 10 device is not enrolled in Microsoft Intune or Azure AD

1.  Switch to **LON-CL4** and sign in as **Admin** with the password
    **Pa55w.rd**

2.  Select **Start**, type **certlm.msc**, press **Enter** and then select **Yes**.

3.  In the **Certificates** console, in the navigation pane, select **Personal**
    and verify that the following certificates are not listed in the details
    pane:

-   Microsoft Intune MDM Device CA

-   MS-Organization-Access

-   MS-Organization-P2P-Access \[2020\]

    _Note: This will indicate that the device is not enrolled in Azure AD or Microsoft Intune._

4.  Close the **Certificates** console.

5.  Right-click **Start**, and then select **Windows PowerShell (Admin)**. When
    prompted select **Yes**.

6.  In the PowerShell console, type the following and press Enter:
```
 dsregcmd /status

```
7.  In the output under **Device State**, verify that **AzureAdJoined : NO** is
    displayed.

8.  Close the PowerShell window.

### Task 2: Enroll a Windows 10 device to Azure AD and Microsoft Intune using Settings app

1.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select **Accounts**.

3.  In the **Access work or school** section, select **Connect**.

4.  In the **Microsoft account** window, select **Join this device to Azure Active Directory**.

5.  On the **Let's get you signed in** page, type **JoniS\@yourtenant.onmicrosoft.com** and then select
    **Next**.

6.  On the **Enter password** page, enter the temporary password from the
    previous lab. When it requests that you update your password, enter
    **Pa55w.rd12345** in the text box and then select **Sign in**.

7.  Wait a few seconds and then on the **Make sure this is your organization** dialog, select **Join**.

8.  On the **You're all set!** page, select **Done**.

9.  In the **Settings** app, in the **Access work or school** section, verify
    that the device is connected to Azure AD and then close the **Settings**
    app.



### Task 3: Verify that the Windows 10 device is enrolled in Intune and Azure AD

1.  On the **LON-CL4** taskbar, select **Start**, type **certlm.msc**, press
    **Enter** and when prompted select **Yes**.

2.  In the **Certificates** console, in the navigation pane, expand **Personal**
    and select the **Certificate** node. Verify that the following certificates
    are listed in the details pane:

-   Microsoft Intune MDM Device CA

-   MS-Organization-Access

-   MS-Organization-P2P-Access \[2020\]

    This will indicate that the device is enrolled in Azure AD and Intune.

3.  Close the Certificates window.

4.  Right-click **Start**, and then select **Windows PowerShell (Admin)**. When
    prompted select **Yes**.

5.  In the PowerShell console, type the following and press **Enter**: 
```
dsregcmd /status
```

6.  In the output under **Device State**, verify that **AzureAdJoined : YES** is
    displayed. This indicates that the device is Azure AD joined.

7.  In the output under **Tenant Details**, verify that the following three entries
    exist:

-   mdmUrl :
    **https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc**

-   mdmToUrl : **https://portal.manage.microsoft.com/TermsofUse.aspx**

-   mdmComplianceUrl : **https://portal.manage.microsoft.com/?portalAction=Compliance**

    This indicates that the device is enrolled in Intune.

### Task 4A: Logon to a Windows 10 Device using Azure AD user (Phone verification)

_Note: this task requires the use of your mobile phone in order to be validated by Microsoft. The task is optional but recommended as it will demonstrate how to setup Windows Hello, the first time you login using your Azure AD credentials. If you prefer or are unable to sign in with phone verification, go to **Task 4B**._

When you're logged on using your Azure AD credentials you will benefit from
Single-Sign-On (SSO) to Azure AD, Intune and Office 365.

1.  On **LON-CL4**, sign out of LON-CL4.

2.  Select **other user**, and sign in with **JoniS\@yourtenant.onmicrosoft.com** with the password **Pa55w.rd12345**.

3.  Wait for the profile to be created.

4.  On the **Your organization requires Windows Hello** screen, select **Set up PIN**.

5.  On the More information required, select **Next**.

6.  On the **Help us protect your account** screen, select **Set it up now**.

7.  On the **Additional security verification** screen, under **How should we contact you?**
    verify that Authentication phone is selected in the drop-down field. In the **Select your country or region** box, select your country and in the **Phone Number** field, type your phone number. Then select **Next**.

8.  Wait for a text message to arrive on your phone, type the 6-digit security
    code in the **Enter Your security code** field and select **Next**.

9.  When the verification is successful, select **Done**.

10.  In the **Set up a PIN** dialog box, type **112233** in the **New PIN** and **Confirm PIN field** and select **OK**.

11. On the **All set!** screen, select **OK**.

_Note: Continue to Task 5._

### Task 4B: Logon to a Windows 10 Device using Azure AD user (no phone verification)

1.  On LON-CL4, right-click **Start**, select **Shutdown or sign out** and then select **Sign out**.

2.  Select **Other user**, and sign in as **JoniS\@yourtenant.onmicrosoft.com** with the password **Pa55w.rd12345**.

3.  Wait for the profile to be created.

4.  On the **Your organization requires Windows Hello** screen, select **Set up
    PIN**.

5.  On the **Help us protect your account** screen, select **Set it up now**.

6.  On the **verify your identity** screen, close the window by selecting the
    **X**.

7.  On the **Something went wrong** screen, select **Skip for now** and then
    select **Next**.

8.  You will be shown the desktop.

### Task 5: Verifying device enrollment in the Intune console

1.  Switch to **LON-CL3**. In the Azure portal, type **Intune** in the search resources
    text box and press **Enter**. In the navigation pane, select **Devices**.

2.  On the **Devices** blade under Intune enrolled devices, verify that 1 is
    displayed next to **Windows**. If no devices are listed refresh the webpage
    and repeat steps 1 and 2.

3.  On the **Devices** blade, select **All devices** and verify that **LON-CL4**
    is listed.

4.  On the **Devices** blade, select **Azure AD devices** and verify that
    **LON-CL4** and the device from the hybrid join lab are listed.  Note that the **MDM** column displays **Microsoft Intune** for **LON-CL4**.  
    
    _Note: This view lists devices that are joined to Azure AD. Remember that you
    configured integration between Azure AD and Intune, and because of that, any
    device that is joined to Azure AD is automatically enrolled to Intune. Any devices
    joined prior to setting up enrollment are only joined to Azure AD, but not enrolled
    in Intune._

5.  Close all Windows.

**END OF LAB**
