# Practice Lab - Configuring user profiles

## Summary

In this lab, you will practice configuring user profiles in AD DS and setting up folder direction. 

## Exercise 1: Configuring roaming user profiles and Folder Redirection

### Scenario

Ada Russel frequently uses both LON-CL1 and LON-CL2 and is struggling with accessing documents between machines.  She's requested that the files in the documents folder are the same regardless of which device she is using. You've been asked to use Folder Redirection.

### Task 1: Prepare the environment for roaming profiles and Folder Redirection

1.  On **LON-DC1**, sign-in as **adatum\\administrator** using **Pa55w.rd** as
    the password.

2.  On **LON-DC1**, on the taskbar, click **File Explorer**. In the navigation
    pane, select **Allfiles (E:)**.

3.  In **File Explorer**, in the details pane, right-click an empty space, point
    to **New**, and then select **Folder**. Type **Profiles** as the folder
    name, and then press Enter.

4.  Right-click the **Profiles** folder, select **Share with**, and then select
    **Specific people**.

5.  In the **File Sharing** dialog box, in the text box, type **domain users**,
    click **Add**, select the arrow near **Read for Domain Users**, select
    **Read/Write**, select **Share** and then select **Done**.

6.  In **File Explorer**, in the details pane, right-click an empty space, point
    to **New**, and then select **Folder**. Type **Redirected** as the folder
    name, and then press Enter.

7.  Right-click the **Redirected** folder, select **Share with** and then select
    **Specific people**.

8.  In the **File Sharing** dialog box, in the text box, type **domain users**,
    click **Add**, select the arrow near **Read for Domain Users**, select
    **Read/Write**, select **Share**, select **Done**, and then close File
    Explorer.

### Task 2: Configure roaming user profiles

1.  On **LON-DC1**, on the taskbar, click **Server Manager**.

2.  In **Server Manager**, click **Tools**, and then select **Active Directory
    Users and Computers**.

3.  In **Active Directory Users and Computers**, in the navigation pane, expand
    **Adatum.com**, and then select the **Marketing** OU.

4.  In the details pane, right-click **Ada Russell**, and then select
    **Properties**.

5.  In the **Ada Russell Properties** dialog box, on the **Profile** tab, in the
    **Profile path** text box, type **\\\\LON-DC1\\Profiles\\%username%**, and
    then select **OK**.

6.  Minimize the **Active Directory Users and Computers** window.

### Task 3: Configure Folder Redirection

1.  On **LON-DC1**, in **Server Manager**, click **Tools**, and then click
    **Group Policy Management**.

2.  In the **Group Policy Management** console (GPMC), in the navigation pane,
    expand **Forest: Adatum.com**, expand **Domains**, and then expand
    **Adatum.com**.

3.  In the navigation pane, right-click the **Marketing** OU, and then click
    **Create a GPO in this domain, and Link it here**.

4.  In the **Name** text box, type **Folder Redirection**, and then click
    **OK**.

5.  In the GPMC, in the navigation pane, expand the **Marketing** OU,
    right-click **Folder Redirection**, and then click **Edit**. The **Group
    Policy Management Editor** window opens.

6.  In the **Group Policy Management Editor** window, under **User
    Configuration** in the navigation pane, expand **Policies**, expand
    **Windows Settings**, and then expand **Folder Redirection**.

7.  Right-click **Documents**, and then click **Properties**.

8.  In the **Documents Properties** dialog box, in the **Setting** drop-down
    box, select **Basic – Redirect everyone’s folder to the same location**.

9.  In the **Target folder location** section, in the **Root Path** text box,
    type **\\\\LON-DC1\\Redirected**, and then click **OK**.

10. In the **Warning** dialog box, select **Yes**.

11. Close the **Group Policy Management Editor** window, and then minimize the
    GPMC.

### Task 4: Test roaming user profiles and Folder Redirection

1.  On **LON-DC1**, on the taskbar, click **File Explorer**.

2.  In **File Explorer**, in the navigation pane, click **Local Disk (E:)**, and
    then verify that the **Profiles** and **Redirected** folders are empty.

3.  Sign in to **LON-CL1** as **Adatum\\Ada** with the password **Pa55w.rd**.

4.  Right-click anywhere on the desktop, point to **New**, and then click
    **Folder**. Type **Presentations** as the folder name, and then press Enter.

5.  On the desktop, right-click anywhere, point to **New**, and then select
    **Shortcut**.

6.  Click **Browse**, expand **This PC**, select **Local Disk (C:)**, select
    **OK**, select **Next**, and then click **Finish**. A shortcut to local disk
    C is added to the desktop.

7.  On the taskbar, select **Start**, type **notepad**, and then press Enter.

8.  In **Notepad**, type your name. On the **File** menu, click **Save As**,
    select the **Documents** folder in the navigation pane, enter your name in
    the **File Name** text box, click **Save**, and then close **Notepad**.

9.  On the taskbar, click **File Explorer**, and then in the navigation pane,
    select **Documents**. In the details pane, right-click the file with your
    name, and then click **Properties**. Verify that the location of that file
    points to the network, to **\\\\LON-DC1\\Redirected\\Ada\\Documents**, and
    that it’s not stored inside Ada Russell’s local profile. Also, verify that
    there is an **Offline Files** tab in the **File Properties** dialog box, and
    then click **OK**.

10. On the taskbar, right-click **Start**, select **Shut down or sign out**, and
    then click **Sign out**.

11. On **LON-DC1**, in **File Explorer**, verify that the **E:\\Profiles** and
    **E:\\Redirected** folders are no longer empty. The **Profiles** folder
    contains the Ada Russell roaming user profile (**Ada.V6**), while the
    **Redirected** folder contains Ada Russell’s redirected **Documents**
    folder.

12. Sign in to **LON-CL2** as **Adatum\\Ada** with the password **Pa55w.rd**.

13. Verify that the **Presentations** folder and the **Local Disk (C)** shortcut
    are on the desktop.

14. On the taskbar, click **File Explorer**, and then in the navigation pane,
    select **Documents**. In the details pane, right-click the file with your
    name, and then click **Properties**. Verify that the location of that file
    points to the network, to **\\\\LON-DC1\\Redirected\\Ada\\Documents**, and
    that it’s not stored inside Ada Russell’s local profile.

15. On the taskbar, right-click **Start**, select **Shut down or sign out**, and
    then click **Sign out**.

## Exercise 2: Configuring Enterprise State Roaming

### Scenario

Users are requesting that their Windows settings and application data be the same when using different computers. You have decided to implement Enterprise State Roaming. You will need to enable ESR, and verify that it is working.  Diego Siciliani has offered to test, as he frequently switches between LON-CL3 and LON-CL4.

On **LON-CL3**, on the taskbar,

1.  Right-click the **Start** button and select **Windows PowerShell (Admin)**, when
prompted click **Yes.**

2.  In the PowerShell console, type the following and then press Enter: 
    
   ` REG ADD HKLM\\SOFTWARE\\Policies\\Microsoft\\PassportForWork /v Enabled /t
    REG_DWORD /d 0 /f `  

This will disable Windows Hello on the device and will disable the forced creation of a PIN when logging on to the device the first time using an Azure AD account. This will also disable the need for access to a mobile phone as this requires validation of the Azure AD account being used. You can also disable the use of Windows Hallo by creating a policy in Intune.

### Task 2: Logon to second Windows 10 device using Azure AD user

1.  On **LON-CL3**, right-click **Start**, click **Shutdown or sign out** and
    then click **Sign out**.

2.  Click **other user**, and in the **Email address** field type
    DiegoS**\@yourtenant.onmicrosoft.com**, and then click **Next**. In the
    **Password** field, type **Pa55w.rd** and then press Enter.

    Wait for the profile to be created. It will take around 15 seconds.

3.  On **LON-CL3**, on the taskbar, click **Start** and then click the
    **Settings** app.

4.  In the **Settings** app, click the **Accounts** tile and then click **Access
    work or school**.

5.  In the **Access work or school** section, click the **Connected to Contoso’s
    Azure AD** link and then click **Info**.

6.  In the **Managed by Contoso** dialog box, click **Sync**. Wait for the
    synchronization to complete.  
    It may take up to 15 minutes before the profile is applied to Windows 10
    device.

7.  Click the left arrow in the upper left corner and In the **Settings** app,
    and then click **Sync your settings**.

8.  On the **Sync your settings** page, verify that **Sync settings** is set to
    **On**. You can control the individual sync settings by toggling them either
    on or off.

9.  You should already be logged on as **Diego Siciliani** on **LON-CL4**.

### Task 3: Enable Enterprise State Roaming

1.  **On LON-DC1**, on the taskbar, right-click **Internet Explorer**, and then
    select **Start InPrivate Browsing**.

2.  In **Internet Explorer**, in the address bar, type
    **https://portal.azure.com** and press Enter.

3.  On the **Microsoft Azure** page, Sign in as user
    **Admin\@yourtenant.onmicrosoft.com**, and use the tenant Admin password.

4.  In the Azure Portal, in the navigation pane, select **Azure Active
    Directory**.

5.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Devices**.

6.  On the **Devices** blade, make a note of devices that are listed in the
    details pane. In the navigation pane, click **Enterprise State Roaming**.

7.  On the **Devices – Enterprise State Roaming** blade, in the details pane, in
    the **Users may sync settings and app data across devices** section, click
    **Selected**.

8.  Click **Selected No member selected**, click **+ Add members** and type **Diego
    Sicilian** in the text box.
9.  Click **Diego Siciliani** and then click **Select**.
10. Click **OK**, and then select **Save**.  
    By performing this task, you enabled Enterprise State Roaming for **Diego
    Siciliani**.


### Task 4: Verify Enterprise State Roaming

1.  On **LON-CL3**, on the taskbar, click Microsoft Edge and in the address bar,
    type **www.microsoft.com/learning**, and then press Enter. When the page
    loads, click the star and the end of the address bar (or press CTRL+D). In
    the Favorites pop-up, click **Add**.

2.  Switch to **LON-CL4**, and on the taskbar, click **Microsoft Edge**.

3.  In **Microsoft Edge**, press CTRL+I to view favorites. Verify if **Computer
    Training** favorites page is already synced from **LON-CL3**.  
    Usually, Enterprise State Roaming syncs settings fairly quickly. If it is
    not synced, wait a few minutes and repeat steps 2 and 3.

4.  On **LON-DC1**, in **Internet Explorer**, on the **Devices – Device
    settings** blade, in the navigation pane, select **All devices**.

5.  In the details pane, in the **OWNER** column, click **Diego Siciliani**.

6.  In the **Diego Siciliani** blade, in the navigation pane, select
    **Devices**.

7.  In the details pane, verify that **Devices** is selected in the **Show**
    dropdown list. This shows all the devices that Diego Siciliani owns.

8.  In the **Show** drop-down list, select **Devices syncing settings and app
    data**. This view shows the devices that are synced by Enterprise State
    Roaming. It also shows when each device was last synced.

** END OF LAB **