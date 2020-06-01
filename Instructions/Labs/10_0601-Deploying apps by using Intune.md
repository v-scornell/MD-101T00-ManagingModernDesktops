# Practice Lab - Deploying apps by using Intune

## Summary

In this lab, you will practice creating and deploying  a Line of Business app using Intune and the Company Portal.

### Scenario

A. Datum Corporation’s has decided to manage all developers in the company using Azure Active Directory (Azure AD) and Intune. Many of the developers use Remote Desktop Protocol (RDP) on a daily basis to connect to various servers when developing apps for A. Datum. They want a solution where they can choose the servers from a list and easily connect to them instead of entering server names each time they need to connect. You have found Remote Desktop Connection Manager from Microsoft that should fit their needs. As part of evaluating Intune, you will make this app available from the Company Portal. 

#### Task 1: Verify installed apps on device before deployment 

1.  Switch to **LON-CL4**, and sign in with
    **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Select **Start** and then select the **Settings** app.

3.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, scroll down and select **Programs and Features** on the right under **Related Settings**.

4.  In the **Program and Features** window, verify that **Remote Desktop
    Connection Manager 2.7** is not listed.

5.  Close all Windows.

#### Task 2: Add LON-CL4 to the A.Datum Developer Devices Group

1. Sign in to **LON-CL3** as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  In Microsoft Edge, navigate to **https://portal.azure.com** and select
    **Azure Active Directory**.

3.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Devices**.

4.  In the details pane select **LON-CL4** where the owner is **Joni Sherman** and select
    **Delete**, confirm with **Yes**, and then close the **Devices | All Devices** blade.

5.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Groups**.

6. Select **A. Datum developer devices** and then select **Members**. Select 
   **Add Members**. In the Add Members panel, select **LON-CL4** and then select **Select**. 

#### Task 3: Create a line-of-business (LOB) app type based on the scenario 

1.  In Microsoft Edge, navigate to **https://endpoint.microsoft.com**, and then select 
    **Apps** in the navigation pane. On the **Apps | Overview** blade, select **All apps**.

2.  In the **Apps | All apps** blade, in the details pane, select **Add**.

3.  In the **Select app type** blade, under **App type** select from the dropdown 
    **Line-of-business app** and then select **Select**

4.  In the **Add App** blade under **App information** select **Select app package file**.

5.  In **App package file** blade select the folder icon next to the **Select a file** box.
    In the **Open** dialog box, browse to **C:\\Software** and select **rdcman.msi**.
    Then select **Open** and **OK**.

6.  Back on the **Add app** blade configure the following options:

-   Name: **Remote Desktop Connection Manager**

-   Description: **App for developers in A. Datum**

-   Publisher: **Microsoft**

-   Category: **Computer Management**

7.  Scroll down to the bottom and select **Select image** and in the **Logo** blade,
    select the folder icon next to **Select a file**.

8.  In the **Open** dialog box, browse to **C:\\Software** and select
    **rdcman-icon.jpg**. Then select **Open** and **OK**.

9.  Select **Next** twice and then select **Create** to create the app in Intune. Notice the
    app is not yet available. 

10. On navigation pane select **Tenant administration**, then select **Audit logs**.  As the
    RDC app is being created, you will see log entries created.  When there are 4 entries,
    the app should be available.  This can take up to a couple minutes.

11. Select **Apps** in the navigation pane. On the **Apps | Overview** blade, select
    **All apps**. On the **Apps | All Apps** blade, in the details pane, select **Remote
    Desktop Connection Manager**.

12.  On the **Remote Desktop Connection Manager** blade, select **Properties**, then scroll 
    down  and select **Edit** next to **Assignments**. On the **Edit Application** blade,below of **Available for enrolled devices** select **Add all users**.

13. Select **Review + save** and then select **Save**.

14. Back on the **Remote Desktop Connection Manager | Properties** blade in the details pane
    verify that **All users** is listed under **Available for enrolled devices**.

#### Task 4: Install the Company Portal on a Windows 10 device

1.  On **LON-CL3**, On the taskbar, select **Microsoft Edge**, and navigate to
    **https://businessstore.microsoft.com**.

2.  Sign in to the store as **Admin\@yourtenant.onmicroft.com** with your tenant password.

3.  In the **Search field** on the right, type **Company Portal** and press
    **Enter**. Accept the consent dialog if prompted.

4.  Select **Company Portal** in the results list and select **Get the App**.

5.  Accept any agreements you are prompted with. On the Thanks for your order
    dialog, select **Close**.

6.  On the right side, under Unlimited licenses available, select **Assign to
    Users**.

7.  On the **Assign to people** dialog, type
    **DiegoS\@yourtenant.onmicroft.com**. Select **Assign** and then **Close**.

8.  Switch to **LON-CL4** and sign in as **DiegoS\@yourtenant.onmicroft.com.**

9.  On the taskbar, select **Microsoft Edge** and navigate to
    **https://businessstore.microsoft.com**.

10. Select **Sign In**. Login as **DiegoS\@yourtenant.onmicroft.com** if it does
    not by default.

11. In the search box, type **Company Portal** and press **Enter**.

12. Select **Company Portal** in the results list and select **Install**.

13. In the Windows Store app, select **Install**. This process should take about
    a minute.

14. **Close** the Microsoft Store Window.

#### Task 5: Install an app through the Company Portal

1.  On **LON-CL4**, on the taskbar, select **Start** and in the apps list under
    **C**, select **Company Portal**. You will be signed in to the Company Portal
    automatically using Single-Sign-On, because the device is Azure AD joined.

2.  In the **Company Portal** under **Apps**, select **Remote Desktop Connection Manager**.
    On the **Remote Desktop Connection Manager** page, select **Install**.

3.  Wait for the app installation files to download and for the installation to
    complete. When it says **Installed**, the Remote Desktop Connection Manager
    is installed.

#### Task 6: Verify on device that app is installed

1.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, scroll down and verify that **Remote Desktop Connection
    Manager** is listed.

3.  Close the **Settings** app and select the **Start** button.

4.  In the app list, scroll down to **R** and select **Remote Desktop Connection
    Manager** and verify that the app opens.

5.  Close all open windows.

#### Task 7: Verify app installation in Intune

1.  Switch to **LON-CL3**.

2.   In Microsoft Edge, navigate to **https://endpoint.microsoft.com**, in the navigation
     pane select **Apps**.

3.  On the **Apps | Overview** blade, select **Monitor**, and then select **App install status**. In the details pane, select **Remote Desktop Connection Manager**.

    _Note: If you see no data, select the **Load more** link._

4.  In the details pane, under **Device status** and under **User status**,
    **1** is displayed under Installed. This indicates that the app is installed
    on one device and for one user.

    _Note: The graph may take time before it's updated.  If it still displays
    **0**, continue on._ 

5.  Select **Device install status** to the left of the blue circle. In the
    details pane, you can see the devices that the app is installed on, and also
    the name of the user. The **Device name** column should list **LON-CL4** and
    the **User Name** column should list DiegoS in the **Status** column should
    say **Installed**. 
    _Note: This means that the app is installed on LON-CL4 VM by the user DiegoS._

6.  Select **Devices** from the navigation bar.

7.  On the **Devices | Overview** blade, select **All devices** and then in the details
    pane, select **LON-CL4**.

8.  On the **LON-CL4** blade, select **Managed Apps** under **Monitor**.

9.  On the **LON-CL4 | Managed Apps** blade, in the details pane,
    select **Remote Desktop Connection Manager**.

10. On the **Remote Desktop Connection Manager - Installation details** blade,
    you can see the entire lifecycle of the application, that is - when it was
    created, assigned, installation time and status and the last time the device
    checked in (synced with Intune).

**END OF LAB**