# Practice Lab - Deploying apps by using Intune

## Summary

In this lab, you will practice creating and deploying  a Line of Business app using Intune and the Company Portal.

### Scenario

A. Datum Corporation’s has decided to manage all developers in the company using Azure Active Directory (Azure AD) and Intune. Many of the developers use Remote Desktop Protocol (RDP) on a daily basis to connect to various servers when developing apps for A. Datum. They want a solution where they can choose the servers from a list and easily connect to them instead of entering server names each time they need to connect. You have found Remote Desktop Connection Manager from Microsoft that should fit their needs. As part of evaluating Intune, you will make this app available from the Company Portal. 

#### Task 1: Verify installed apps on device before deployment 

1.  Switch to **LON-CL4**, and sign in with
    **DiegoS\@yourtenant.onmicrosoft.com** with the Password **Pa55w.rd**

2.  Click **Start** and then click the **Settings** app.

3.  In the **Settings** app, click the **Apps** tile and on the **Apps &
    features** page, scroll down and click **Programs and Features**.

4.  In the **Program and Features** window, verify that **Remote Desktop
    Connection Manager 2.7** is not listed.

#### Task 2: Create a line-of-business (LOB) app type based on the scenario 

1.  On **LON-CL3**, in the Azure portal, click **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, click **Client apps**.

2.  In the **Client apps** blade, click **Apps**. In the details pane, click **+
    Add**.

3.  In the **Add app** blade, click the **Select an app type** under **App
    type** and select **Line-of-business app**.

4.  Click **App package file Select file**, and in **App package file** blade,
    click the folder icon next to **Select a file**.

5.  In the Open dialog box, browse to **C:\\Software** and click **rdcman.msi**.
    Then click **Open** and **OK**.

6.  Back on the Add app blade, click **App information Configure**. Configure
    the following options:

-   Name: **Remote Desktop Connection Manager**

-   Description: **App for developers in A. Datum**

-   Publisher: **Microsoft**

-   Category: **Computer Management**

7.  Scroll down to the bottom and click **Logo Select image** and in Logo blade,
    click the folder icon next to **Select a file**.

8.  In the **Open** dialog box, browse to **C:\\Software** and click
    **rdcman-icon.jpg**. Then click **Open** and **OK**.

9.  Click **OK** and then click **Add** to create the app in Intune. Wait
    between 10-30 seconds for the app source files to be uploaded to Intune.

10.  On the **Client apps – Apps** blade, in the details pane, click **Remote
    Desktop Connection Manager**.

11.  On the **Remote Desktop Connection Manager** blade, click **Assignments**
    and on the **Remote Desktop Connection Manager - Assignments** blade, click
    **Add group**.

12.  On the **Add group** blade, click **Select assignment type** under
    **Assignment type** and select **Available for enrolled devices**.

13.  Click **No groups selected Included Groups** and on the **Assign** blade,
    click **Select groups to include**.

14.  On the **Select groups** blade, click **A. Datum developers** and then click
    **Select** and **OK** twice.

15.  Back on the **Remote Desktop Connection Manager - Assignments** blade, click
    **Save**. In the details pane verify that **A. Datum Developers** is listed
    under **AVAILABLE FOR ENROLLED DEVICES**.

#### Task 3: Install the Company Portal on a Windows 10 device

1.  On **LON-CL3**, On the taskbar, click **Microsoft Edge**, and navigate to
    <https://businessstore.microsoft.com>.

2.  Sign in as **Admin\@yourtenant.onmicroft.com** with your tenant password.

3.  In the **Search field** on the right, type “**Company Portal**” and press
    **Enter**. Accept the consent dialog if prompted.

4.  Select **Company Portal** in the results list and click **Get the App**.

5.  Accept any agreements you are prompted with. On the Thanks for your order
    dialog, click **Close**.

6.  On the right side, under Unlimited licenses available, click **Assign to
    Users**.

7.  On the **Assign to people** dialog, type
    **DebraB\@yourtenant.onmicroft.com**. Click **Assign** and then **Close**.

8.  Switch to **LON-CL4** and sign in as **DebraB\@yourtenant.onmicroft.com.**

9.  On the taskbar, click **Microsoft Edge** and navigate to
    <https://businessstore.microsoft.com>.

10. Click **Sign In**. Login as **DiegoS\@yourtenant.onmicroft.com** if it does
    not by default.

11. In the search box, type **Company Portal** and press **Enter**.

12. Select **Company Portal** in the results list and click **Install**.

13. In the Windows Store app, click **Install**. This process should take about
    a minute.

14. **Close** the Microsoft Store Window.

#### Task 4: Install an app through the Company Portal

1.  On **LON-CL4**, on the taskbar, click **Start** and in the apps list under
    **C**, click **Company Portal**. You will be signed in to the Company Portal
    automatically using Single-Sign-On, because the device is Azure AD joined.

2.  In the **Company Portal** under **Apps**, click **Remote Desktop
    Connection**. On the **Remote Desktop Connection Manager** page, click
    **Install**.

3.  Wait for the app installation files to download and for the installation to
    complete. When it says **Installed**, the Remote Desktop Connection Manager
    is installed.

#### Task 5: Verify on device that app is installed

1.  On **LON-CL4**, on the taskbar, click **Start** and then click the
    **Settings** app.

2.  In the **Settings** app, click the **Apps** tile and on the **Apps &
    features** page, scroll down and verify that **Remote Desktop Connection
    Manager** is listed.

3.  Close the **Settings** app and click the **Start** button.

4.  In the app list, scroll down to **R** and click **Remote Desktop Connection
    Manager** and verify that the app opens.

5.  Close all open windows.

#### Task 6: Verify app installation in Intune

1.  Switch to **LON-CL3**.

2.  In the Azure portal, click **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, click **Client apps**.

3.  On the **Client apps** blade, click **App install status** under
    **Monitor**. In the details pane, click **Remote Desktop Connection
    Manager**.

    **Note:** If you see no data, click the **Load more** link.

4.  In the details pane, under **Device status** and under **User status**,
    **1** is displayed under Installed. This indicates that the app is installed
    on one device and for one user.

5.  Click **Device install status** to the left of the blue circle. In the
    details pane, you can see the devices that the app is installed on, and also
    the name of the user. The **DEVICE NAME** column should list **LON-CL4** and
    the **USER NAME** column should list DiegoSand the **STATUS** column should
    say **Installed**. This mean that the app is installed on LON-CL4 by the
    user DiegoS.

6.  In the Azure portal, click **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, click **Devices**.

7.  On the **Devices** blade, click **All devices** and then in the details
    pane, click **LON-CL4**.

8.  On the **LON-CL4** blade, click **Managed Apps - Preview** under
    **Monitor**.

9.  On the **LON-CL4 - Managed Apps - Preview** blade, in the details pane,
    click **Remote Desktop Connection Manager**.

10. On the **Remote Desktop Connection Manager - Installation details** blade,
    you can see the entire lifecycle of the application, that is - when it was
    created, assigned, installation time and status and the last time the device
    checked in (synced with Intune).
