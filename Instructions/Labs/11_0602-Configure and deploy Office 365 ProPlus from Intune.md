# Practice Lab - Configure and deploy Office 365 ProPlus from Intune

## Summary

In this lab, you will practice configuring Office 365 ProPlus for deployment in Intune and deploying it to devices.


### Scenario

All the developers at A. Datum require Microsoft Office 365 ProPlus. You've been asked to deploy  64-bit versions of Microsoft Excel, Outlook, PowerPoint and Word to their Windows 10 devices. You also need to ensure they are configured for the Semi-Annual channel for updates. This should be tested on LON-CL4.

#### Task 1: Verify installed apps on device before deployment

1.  On **LON-CL4** sign in as **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant
    password. On the taskbar, select **Start** and then select the **Settings** app.

2.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, select **Programs and Features** under **Related Settings**.

3.  In the **Program and Features** window, verify that **Microsoft Office 365
    ProPlus - en-us** is not listed.

#### Task 2: Create a LOB app type based on the scenario

1.  Switch to **LON-CL3** and sign in as **admin\@yourtenant.onmicrosoft.com** with the 
    default tenant password.

2.  Open **Microsoft Edge**, navigate to **https://endpoint.microsoft.com** and select **Apps**.

3.  In the **Apps | Overview** blade, select **All Apps**. In the details pane, select **Add**.

4.  In the **Select app type** blade, select **Windows 10** under **Microsoft 365 Apps**, and then select **Select**.

5.  On the **App Microsoft 365 Apps** blade, configure
    the following options and select **Next**:

-   Suite Name: **Office 365 ProPlus (A. Datum developers)**

-   Suite Description: **Office 365 ProPlus App for developers in A. Datum**

6.  On the **Configure app suite** blade, expand the **Select Office apps** dropdown, select the following Office 365 apps and select **Next**:

-   Excel

-   Outlook

-   PowerPoint

-   Word

7.  On the **Configure app suite** tab, configure the
    following options and select **Next**:

-   Architecture: **64-bit**

-   Update channel: **Semi-Annual**

-   Accept the Microsoft Software License Terms on behalf of users: **Yes**

8.  On the **Assignments** tab, in the **Required** section, select **Add group.** 

9.  On the **Select groups** blade, select **A. Datum Developer devices**, and then choose **Select**.

10. Select **Next**.  On the **Review + Create** tab, select **Create**.

11.  On the **Office 365 ProPlus (A. Datum Developers)** page, select **Properties**. In the details pane verify that **A. Datum developer devices** in listed next to **Required** in the Assignments section.

#### Task 3: Force synchronization of policy from Intune console

1.  On **LON-DC1**, in the Azure portal, select **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, select **Devices** and then
    select **All devices**.

2.  In the details pane, select **LON-CL3**. On the **LON-CL3** blade, select
    **Sync** and when prompted select **Yes**. Intune will contact the device and
    tell it to synchronize all policies. This may take up to 5 minutes.

#### Task 4: Verify on device that app is installed

1.  Switch to **LON-CL4** and wait approximately 10-15 minutes for the Office
    365 Suite to install on the device.

2.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

3.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, scroll down and verify that **Microsoft Office 365 ProPlus
    - en-us** is listed.

4.  Close the **Settings** app and select the **Start** button.

5.  In the app list, scroll down to **W** and select **Word** and verify that the
    app opens.

6.  Close all open windows.

#### Task 5: Verify app installation in Intune

1.  Switch to **LON-CL3**.

2.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Client apps**.

3.  On the **Client apps** blade, select **App install status** under
    **Monitor**. In the details pane, select **Office 365 ProPlus (A. Datum
    developers)**.

4.  In the details pane, under **Device status** and under **User status**,
    **1** is displayed under Installed. This indicated that the app is installed
    on one device and for one user.

5.  Select **Device install status** to the left of the blue circle. In the
    details pane, you can see the devices that the app is installed on, and also
    the name of the user. The **DEVICE NAME** column should list **LON-CL4** and
    the **USER NAME** column should list **DiegoS** and the **STATUS** column
    should say **Installed**. This mean that the app is installed on LON-CL4 by
    the user DiegoS.

6.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Devices**.

7.  On the **Devices** blade, select **All devices** and then in the details
    pane, select **LON-CL4**.

8.  On the **LON-CL4** blade, select **Managed Apps - Preview** under
    **Monitor**.

9.  On the **LON-CL4 - Managed Apps - Preview** blade, in the details pane,
    select **Office 365 ProPlus (A. Datum developers)**.

10. On the **Office 365 ProPlus (A. Datum developers) - Installation details**
    blade, you can see the entire lifecycle of the application, that is - when
    it was created, assigned, installation time and status and the last time the
    device checked in (synced with Intune).

**END OF LAB**