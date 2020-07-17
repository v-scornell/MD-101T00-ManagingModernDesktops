# Lab: Creating and deploying provisioning package

## Summary

In this lab you will learn how to create and apply a Provisioning Package. 

## Lab Scenario

Adatum has purchased a new computer, LON-CL4. It has Windows 10 already installed, but is a default install, and must be properly configured for use in the Marketing Department and joined to the Adatum.com AD DS domain. The computer is already in use, and the manager there is requesting minimal user interruption.  

### Exercise 1: Creating and deploying provisioning package

#### Task 1: Review the current computer settings

1.  On **LON-DC1**, sign in as **Adatum\\administrator** with the password of
    **Pa55w.rd**.

2.  In **Server Manager**, select **Tools**, and then select **Active Directory
    Users and Computers**.

3.  In Active Directory Users and Computers, in the navigation pane, expand
    **Adatum.com**, expand **Marketing**, and then select **Computers**. In the
    details pane, verify that no computer account is present.

4.  On the taskbar, select **File Explorer**.

5.  In File Explorer, select **Allfiles (E:)**.

6.  In the details pane, right-click an area of free space, point to **New** and
    then select **Folder**.

7.  Name the Folder "**Provision"** and press Enter.

8.  Right-click **Provision**, point to **Share with** and then select **Specific
    people**.

9.  In the text box, type **Everyone** and then select **Add**.

10. Next to **Everyone**, select **Read** and then select **Read/Write**.

11. Select **Share** and when prompted, select **Done**.

12. Switch to **LON-CL4**.

13. On **LON-CL4**, sign in as **Admin** with the password of **Pa55w.rd**.

14. On the taskbar, select **Start** and then select the **Settings** icon. Select
    **Accounts** then select **Access work or school**.  

15. Select the Azure AD connection and select **Disconnect**. Select **Yes** and then select **Disconnect** to confirm. In the **Windows Security** dialog enter **Admin** as **Email Address** and **Pa55w.rd** as **Password**.

16. Restart the VM and sign in as **Admin**, with the password **Pa55w.rd**. On the taskbar, select the **File Explorer** icon.

17. In **File Explorer**, in the navigation pane, right-click **This PC**, and then
    select **Properties**.

18. In the **System** section, in the **Computer name, domain, and workgroup
    settings** section, verify that the computer name is **LON-CL4** and that
    it's in a workgroup named **WORKGROUP**.

19. Close the **System** window.

20. In File Explorer, in the navigation pane, right-click **This PC**, and then
    select **Manage**.

21. In **Computer Management**, in the navigation pane, expand **Local Users and
    Groups**, select **Users**, and then in the details pane, verify that
    **LocalAdmin** isn't present.

22. Close **Computer Management**.

23. In File Explorer, in the navigation pane, expand **This PC**, expand **Local
    Disk (C:)**, expand **Users**, expand **Public**, select **Public
    Documents**, and then in the details pane, verify that the newly created
    "Provision" Folder isn't present as a subfolder. (You can ignore the
    subfolders, if any).

24. In the navigation pane, right-click **This PC** and then select **Map network
    drive**.

25. In the **Folder** box, type **\\\\LON-DC1\\Provision** and then select the
    **Connect using different credentials** check box.

26. Select **Finish**, and in the **Windows Security** dialog box, enter the User
    name of **Adatum\\administrator**. In the **Password** box, type
    **Pa55w.rd**. Select **OK**.

### Task 2: Create a provisioning package

1.  Switch to **LON-CL1**.

2.  Sign in to LON-CL1 as **Adatum\\administrator** with the password of
    **Pa55w.rd**.

3.  On **LON-CL1**, on the taskbar, select **File Explorer**.

4.  In the navigation pane, right-click **This PC** and then select **Map network
    drive**.

5.  In the **Folder** box, type **\\\\LON-DC1\\Provision** and then select
    **Finish**.

6.  Navigate to **C:\\Files**, right-click an area of free space, point to
    **New**, and then select **Text Document**.

7.  Type **document** and press Enter.

8.  Double-click **document.txt**, type **my file**, close notepad, and select
    **Save**.

9.  On the taskbar, select **Start**, type **designer**, and then select
    **Windows Imaging and Configuration Designer**.

10. After **Windows Configuration Designer** opens, select the **Provision desktop
    devices** tile.

11. On the **Enter project details** page, in the **Name** text box,
    type **Marketing Computer**, and then select **Finish**.

12. In the **Device name** section, in the text box, type
    **Marketing-%RAND:3%**, review the other sections, and then select **Account
    Management**.

13. In the **Manage organization/school accounts** section, provide values for
    the following text boxes:

    -   Domain Name: **Adatum.com**

    -   User name: **Adatum\\Ada**

    -   User password: **Pa55w.rd**

14. In the **Optional: Create a local administrator account** section, provide
    values for the following text boxes

    -   User name: **LocalAdmin**

    -   Password: **Pa55w.rd**

15. In the lower-left corner of Windows Configuration Designer, select **Switch
    to advanced editor**, and then select **Yes**.

16. In the navigation pane, expand **Runtime settings**, expand **Accounts**,
    expand **ComputerAccount**, and then select **AccountOU**.

17. In the details pane, in the **Any text** text box, type
    **OU=Computers,OU=Marketing,DC=Adatum,DC=com**.

18. In the navigation pane, select **Users**.

19. In the details pane, in the **UserName** text box, type your name, and then
    select **Add**.

20. In the navigation pane, select **UserName:_Yourname_**. In the details pane,
    select the **Password** text box, and then type **Pa55w.rd**.

21. In the navigation pane, expand **Folders**, and then select
    **PublicDocuments**. In the details pane, select **Browse**, select **Local
    Disk (C:)**, double-click **Files**, select **document.txt**, select
    **Open**, and then select **Add**.

22. In Windows Configuration Designer, on the toolbar, select **Export**, and
    then select **Provisioning package**.

23. In the **Build** wizard, on the **Describe the provisioning package** page,
    select **Next**.

24. On the **Select security details for the provisioning package** page, select
    **Next**.

25. On the **Select where to save the provisioning package** page, select
    **Browse**, select **This PC**, and then double-click **Provision
    (\\\\LON-DC1) (Z:)**. Note that the drive letter might vary.

26. In the **File name** text box, type **Marketing Computer**, select **Save**,
    select **Next**, select **Build**, and then select **Finish**

### Task 3: Install the provisioning package

1.  On **LON-CL4**, on the taskbar, switch to **File Explorer**. You should be
    looking at the provision shared folder which should contain two files.

2.  Select both files. Then right-click the files, and choose **Copy**.

3.  In the navigation pane, select **Downloads**.

4.  Right-click an area of free space and then select **Paste**.

5.  In **Downloads**, double-click **Marketing Computer.ppkg**.

6.  In the **User Account Control** dialog box, select **Yes**, read the note on
    the **Is this package from a source you trust** page, and then select **Yes,
    add it**.

7.  Restart **LON-CL4** if the Client PC doesn't automatically reboot, and then
    sign in as **Admin** with the password **Pa55w.rd**. Note that it can take a
    few minutes for **LON-CL4** to restart.

### Task 4: Verify that the computer was provisioned

1.  On **LON-DC1**, on the taskbar, select **Server Manager**.

2.  In **Server Manager**, select **Tools**, and then select **Active Directory
    Users and Computers** if it is not already open.

3.  In Active Directory Users and Computers, in the navigation pane, expand
    **Adatum.com**, expand **Marketing**, and then select **Computers**. In the
    details pane, verify that a computer account is present. The name of the
    computer starts with **Marketing-** followed by three digits.

    _**Important:** If the **Computers** organizational unit (OU) is empty, right-click the OU, and then select **Refresh**._

4.  Switch to **LON-CL4** where you should already be signed in as **Admin**.

5.  On **LON-CL4**, on the taskbar, select the **File Explorer** icon.

6.  In File Explorer, in the navigation pane, right-click **This PC**, and then
    select **Properties**. In the **Computer name, domain, and workgroup
    settings** section, verify that the computer name is **Marketing-** followed
    by three digits and that the computer is in the **Adatum.com** domain.

7.  Close the **System** window.

8.  In File Explorer, in the navigation pane, right-click **This PC**, and then
    select **Manage**.

9.  In **Computer Management**, in the navigation pane, expand **Local Users and
    Groups**, select **Users**, and then in the details pane, verify that
    **LocalAdmin** and the user with your name are both present.

10.  Close **Computer Management**.

11.  In File Explorer, in the navigation pane, expand **This PC**, expand **Local
    Disk (C:)**, expand **Users**, expand **Public**, and then select **Public
    Documents**.

12.  Verify the presence of the **document.txt** file.

**END OF LAB**