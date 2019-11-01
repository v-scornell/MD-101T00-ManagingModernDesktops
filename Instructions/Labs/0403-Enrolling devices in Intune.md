# Practice Lab - Enrolling devices in Intune

## Summary

In this lab, you will practice enrolling a client in Azure AD and Intune reviewing the post-enrollment experience.

### Scenario

Joni Sherman will be testing the process of joining a device, LON-CL3, to the domain and enrolling in Intune. After IT verifies the device is not currently joined, Joni should login using her credentials. 
Joni should then reboot the device to verify organizational settings, such as Windows Hello, are enabled. 

### Task 1: Verify that a Windows 10 device is not enrolled in Intune or Azure AD

1.  Switch to **LON-CL4** and sign in as **Admin** with the password
    **Pa55w.rd**

2.  Click **Start**, type **certlm.msc**, press Enter and then click **Yes**.

3.  In the **Certificates** console, in the navigation pane, click **Personal**
    and verify that the following certificates are not listed in the details
    pane:

-   Microsoft Intune MDM Device CA

-   MS-Organization-Access

-   MS-Organization-P2P-Access [2018]

    _Note: This will indicate that the device is not enrolled in Azure AD or Intune._

1.  Close the **Certificates** console.

2.  Right-click **Start**, and then click **Windows PowerShell (Admin)**. When
    prompted click **Yes**.

3.  In the PowerShell console, type the following and press Enter: **dsregcmd
    /status**

4.  In the output under **Device State**, verify that **AzureAdJoined : NO** is
    displayed.

5.  Close the PowerShell window.

### Task 2: Enroll a Windows 10 device to Azure AD and Intune using Settings app

1.  On **LON-CL4**, on the taskbar, click **Start** and then click the
    **Settings** app.

2.  In the **Settings** app, click the **Accounts** tile and then click **Access
    work or school**.

3.  In the **Access work or school** section, click **+Connect**.

4.  In the **Microsoft account** window, on the **Set up a work or school
    account** page, type **JoniS\@yourtenant.onmicrosoft.com** and then click
    **Next**.

5.  On the **Enter password** page, enter the temporary password from the
    previous lab. When it requests that you update your password, enter
    **Pa55w.rd12345** in the text box and then click **Sign in**.

6.  Wait a few seconds and then on the **Make sure this is your organization**
    dialog, click **Join**.

7.  On the **You’re all set!** page, click **Done**.

8.  On the right hand side you will see under Related settings that theres a
    highlighted text stating manage your computer with MDM or intune. Select the
    text and repeat steps 4 through 8.

9.  You will see two of the same accounts ones associated with Azure AD MDM and
    the other is related to work or school.

10. In the **Settings** app, in the **Access work or school** section, verify
    that the device is connected to Azure AD and then close the **Settings**
    app.

### Task 3: Verify that the Windows 10 device is enrolled in Intune and Azure AD

1.  On the **LON-CL4** taskbar, click **Start**, type **certlm.msc**, press
    Enter and when prompted click **Yes**.

2.  In the **Certificates** console, in the navigation pane, expand **Personal**
    and click the **Certificate** node. Verify that the following certificates
    are listed in the details pane:

-   Microsoft Intune MDM Device CA

-   MS-Organization-Access

-   MS-Organization-P2P-Access [2018]

    This will indicate that the device is enrolled in Azure AD and Intune.

1.  Close the Certificates window.

2.  Right-click **Start**, and then click **Windows PowerShell (Admin)**. When
    prompted click **Yes**.

3.  In the PowerShell console, type the following and press Enter: **dsregcmd
    /status**

4.  In the output under **Device State**, verify that **AzureAdJoined : YES** is
    displayed. This indicates that the device is Azure AD joined.

5.  In the output under Tenant Details, verify that the following three entries
    exist:

-   mdmUrl :
    **https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc**

-   mdmToUrl : **https://portal.manage.microsoft.com/TermsofUse.aspx**

-   mdmComplianceUrl : **https://portal.manage,microsoft.com/?portalAction**

    This indicates that the device is enrolled in Intune.

### Task 4A: Logon to a Windows 10 Device using Azure AD user (Phone verification)

_Note: this task requires the use of your mobile phone in order to be validated by Microsoft. The task is optional but recommended as it will demonstrate how to setup Windows Hello, the first time you login using your Azure AD credentials. If you prefer or are unable to sign in with phone verification, go to **Task 4B**._

When you’re logged on using your Azure AD credentials you will benefit from
Single-Sign-On (SSO) to Azure AD, Intune and Office 365.

1.  On LON-CL4, right-click **Start**, click **Shutdown or sign out** and then
    click **Sign out**.

2.  Click **other user**, and in the **Email address** field type
    **JoniS\@yourtenant.onmicrosoft.com**. In the password, type the password
    for the user and then press Enter.

3.  Wait for the profile to be created. It will take about 15 seconds.

4.  On the **Your organization requires Windows Hello** screen, click **Set up
    PIN**.

5.  On the **Help us protect your account** screen, click **Set it up now**.

6.  On the **verify your identity** screen, click the **Pick a verification
    method** drop-down arrow and select **Text message**. In the **Select your
    country or region** box, select your country and in the **Phone Number**
    field, type your phone number.

7.  Then click **Next**.

8.  Wait for a text message to arrive on your phone, type the 6-digit security
    code in the **Enter Your security code** field and click **Next**.

9.  In the **Set up a PIN** dialog box, type **132435** in the **New PIN** and
    **Confirm PIN field** and click **OK**.

10. On the **All set!** screen, click **OK**.

### Task 4B: Logon to a Windows 10 Device using Azure AD user (no phone verification)

1.  On LON-CL4, right-click **Start**, click **Shutdown or sign out** and then
    click **Sign out**.

2.  Click **Other user**, and in the **Email address** field type
    **JoniS**\@yourtenant.onmicrosoft.com**, and** in the **Password** field,
    type **Pa55w.rd** as the password for the user and then press Enter.

3.  Wait for the profile to be created. It may take up to 60 seconds.

4.  On the **Your organization requires Windows Hello** screen, click **Set up
    PIN**.

5.  On the **Help us protect your account** screen, click **Set it up now**.

6.  On the **verify your identity** screen, close the window by clicking the
    **X**.

7.  On the **Something went wrong** screen, click **Skip for now** and then
    click **Next**.

8.  You will be shown the desktop.

### Task 5: Verifying device enrollment in the Intune console

1.  Switch to **LON-CL3**, on **LON-CL3**, in the Azure portal, click **Intune**
    in the navigation pane and then click **Devices**.

2.  On the **Devices** blade under Intune enrolled devices, verify that 2 is
    displayed next to **Windows**. If no devices are listed refresh the webpage
    and repeat steps 1 and 2.

3.  On the **Devices** blade, click **All devices** and verify that **LON-CL4**
    is listed.

4.  On the **Devices** blade, click **Azure AD devices** and verify that
    **LON-CL4** is displayed in the details pane. Note that the **MDM** column
    displays **Microsoft Intune**.  
    Note: This view lists devices that are joined to Azure AD. Remember that you
    configured integration between Azure AD and Intune, and because of that, any
    device that is joined to Azure AD is automatically enrolled to Intune.

** END OF LAB **