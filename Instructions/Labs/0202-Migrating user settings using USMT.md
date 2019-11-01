# Practice Lab - Migrating user settings using USMT

## Summary

In this lab you will learn how to use the USMT tool with customized settings to migrate user settings and data from one computer to another.

### Scenario

IT is replacing Vera's current PC, LON-CL2, with a new device, LON-CL1.  LON-CL1 has already been provisioned, and Vera's data now must be transferred.  This will require custom settings to ensure the correct data is migrated, and other data is not migrated.

### Exercise 1: Migrating user settings using USMT

#### Task 1: Create a custom XML migration file

1.  Sign in to **LON-CL2** as **Adatum\\Vera** with the password **Pa55w.rd**.

2.  Verify that Vera has a black desktop and the following custom configuration:

    -   **This PC** and **Vera Pace** folders are on the desktop

    -   Calculator and Weather apps are pinned to the taskbar

    -   Store and Mail apps are not pinned to the taskbar

3.  On the desktop, right-click anywhere, select **New**, select **Text
    Document**, type: *\<your name\>*, and then press **Enter**.

4.  On the taskbar, select **File Explorer**. In File Explorer, in the
    navigation pane, expand **This PC**, expand **Local Disk (C:)**, expand
    **Users**, expand **Public**, and then select **Public Documents**. In the
    details pane, right-click anywhere, select **New**, select **Text
    Document**, type: **Vera’s Public Documents**, and then press Enter.

5.  In the navigation pane, select **Public Music**, in the details pane,
    right-click anywhere, select **New**, select **Text Document**, type:
    **Vera’s Public Music** and then press **Enter**.

6.  Sign out of **LON-CL2**, and then sign in to LON-CL2 as
    **Adatum\\Administrator** with the password **Pa55w.rd**.

7.  On the taskbar, right-click **Start**, and then select **Windows PowerShell
    (Admin)**.

8.  In an administrator Command Prompt, type the following three commands,
    pressing **Enter** after each command:

```
Net Use F: \\LON-DC1\USMT  
F:  
F:\scanstate /i:migapp.xml /i:miguser.xml /genconfig:Config.xml

```
    **Note:** The creation of the **Config.xml** file begins. Wait until the command finishes.

1.  In the Command Prompt, type: **notepad Config.xml**, and then press
    **Enter**.

2.  To verify that the content of **Shared Documents** will be migrated, under
    the **Documents** node, make sure that the **migrate** attribute for
    **Shared Documents** is set to **yes**. The line should be similar to the
    following:

```
<component displayname="Shared Documents" migrate="yes">

```
1.  To exclude **Shared Music** from the migration, under the **Documents**
    node, modify the **migrate** attribute for **Shared Music** to value
    **"no"**. The line should look as shown here:

```
<component displayname="Shared Music" migrate="no">

```
1.  To exclude Windows Defender settings from the migration, select **Edit**,
    select **Find**, type: **defender**, select **Find Next**, and then modify
    the **migrate** attribute for **Windows-Defender-AM-Sigs** to value
    **"no"**.

2.  Repeat the previous step and modify the **migrate** attribute from yes to
    **no** for the following two components:

    -   Windows-Defender-AM-Engine

    -   Security-Malware-Windows-Defender

3.  Close Notepad, and then select **Save**.

4.  In the Command Prompt, type: **notepad folders.xml**, and then press Enter.
    **Folders.xml** is a custom XML file that will be used to migrate a folder
    named **Projects** to the new computer.

5.  Change the **\<Foldername\>** string to **Projects**. Do not forget to
    remove the **\<** and **\>** symbols. The entire line should look similar to
    the following:

```
<pattern type= "File">C:\Projects\* [*]\</pattern>

```
1.  Close Notepad, and then select **Save**.

2.  On the taskbar, select **File Explorer**.

3.  In File Explorer, in the navigation pane, expand **This PC**, expand **Local
    Disk (C:)**, and then select **Projects**. In the details pane, verify that
    files named **Project1.txt** and **Project2.txt** are in the folder.

4.  In File Explorer, right-click in the details pane, select **New**, select
    **Text Document**, type: *\<your name\>*, and then press Enter.

Task 2: Capture the user state

1.  On **LON-CL2**, in File Explorer, right-click **This PC**, and then select
    **Manage**.

2.  In Computer Management, in the navigation pane, expand **Local Users and
    Groups**, and then select **Users**.

3.  In the details pane, verify that user named **LocalAdmin** is listed, and
    then close **Computer Management**.

4.  In the Command Prompt, verify that no content is on the
    **\\\\LON-DC1\\MigStore** shared folder, by typing the following command and
    then pressing Enter:

```
Dir \\lon-dc1\MigStore

```
1.  Capture the **LON-CL2** user state by typing the following command and then
    pressing Enter:

```
F:\Scanstate \\LON-DC1\MigStore /i:migapp.xml /i:miguser.xml
/i:folders.xml /config:Config.xml /ue:\* /ui:adatum\vera /o

```
1.  Wait until ScanState finishes, and then verify that the user state is
    captured in the shared folder by typing the following command and then
    pressing Enter:

```
Dir \\lon-dc1\MigStore -Recurse /s

```

Task 3: Restore the user state

1.  If necessary, sign in to **LON-CL1** as **Adatum\\Administrator** with the
    password **Pa55w.rd**.

2.  On **LON-CL1**, on the taskbar, select **File Explorer**.

3.  In File Explorer, in the navigation pane, expand **Local Disk (C:)**, expand
    **Users**, and then verify that there is no subfolder named **Vera**.

4.  In File Explorer, in the navigation pane, select **Local Disk (C:)**, and
    then in the details pane, verify that there is no folder named **Projects**.

5.  On the taskbar, right-click **Start**, and then select **Computer
    Management**.

6.  In Computer Management, in the navigation pane, expand **Local Users and
    Groups**, and then select **Users**.

7.  In the details pane, verify that no user named **LocalAdmin** is listed, and
    then close Computer Management.

8.  On the taskbar, right-click **Start**, select **Windows PowerShell
    (Admin)**, and then select **Yes** at the **User Account Control** prompt.

9.  In Windows PowerShell, type the following command, and then press Enter:

```
Net Use F: \\LON-DC1\USMT

```
1.  In Windows PowerShell, type: **F:**, and then press Enter.

2.  In Windows PowerShell, type the following command, press Enter, and then
    wait for LoadState to finish:

```
F:.\Loadstate \\LON-DC1\MigStore /i:migapp.xml /i:miguser.xml /i:folders.xml /c

```
1.  On the taskbar, select **File Explorer**.

2.  In File Explorer, in the navigation pane, expand **Local Disc (C:)**, expand
    **Users**, and then verify that the subfolder named **Vera** now exists.

3.  On the taskbar, right-click **Start**, and then select **Computer
    Management**.

4.  In Computer Management, in the navigation pane, expand **Local Users and
    Groups**, and then select **Users**.

5.  In the details pane, verify that a user named **LocalAdmin** does not exist,
    because it was excluded from the migration.

6.  On the taskbar, right-click **Start**, select **Shutdown or sign out**, and
    then select **Sign out**.

Task 4: Verify migration of user settings

1.  Sign in to **LON-CL1** as **Adatum\\Vera** with the password **Pa55w.rd**.

2.  Verify that Vera has a black desktop, file with *\<your name\>* on the
    desktop and the same customizations as on **LON-CL2**:

    -   **This PC** and **Vera Pace** folders are on the desktop

    -   Calculator and Weather apps are pinned to the taskbar

    -   Store and Mail apps are not pinned to the taskbar

3.  On the taskbar, select **File Explorer**.

4.  In File Explorer, in the navigation pane, expand **This PC**, expand **Local
    Disk (C:)**, select **Projects**, and then in the details pane, verify that
    all files from **LON-CL2** have migrated, including the file with *\<your
    name\>*.

5.  In the navigation pane, expand **Users**, expand **Public**, select **Public
    Documents**, and then in the details pane, verify that **Vera’s Public
    Documents** appears.

6.  In the navigation pane, select **Public Music**, and in the details pane,
    verify that the folder is empty. This is because the folder content did not
    migrate.


** END OF LAB **