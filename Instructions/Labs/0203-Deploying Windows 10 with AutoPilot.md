# Practice Lab - Deploying Windows 10 with AutoPilot

## Summary

In this lab you will learn how setup and deploy a device with Autopilot using User-driven mode.

### Scenario

IT is planning to rollout a deployment of new devices using Autopilot. The devices have a default installation of Windows 10. Users should be able to connect the device, turn it on, and answer minimal questions during the OOBE, using their Azure AD credentials to login. The process should automatically enroll and join the Azure AD domain.  You have been asked to configure and test the experience using the VM LON-CL5.

_Note: The following lab uses LON-CL5, which is a nested virtual machine
hosted on LON-HOST1. LON-CL5 is automatically provisioned using a script
when the MD-101 lab environment is first launched, which prepares the client
for this lab. This process takes approximately 30 mins, and should be ready
by the time the student is ready to perform this exercise._

Task 1: Customize Azure AD company branding

1.  Switch to LON-CL3 and sign in as **Admin** with the password of
    **Pa55w.rd**.

2.  On **LON-CL3**, on the taskbar, click **Microsoft Edge**.

3.  In Microsoft Edge, in the address bar, type <https://portal.azure.com>, and
    then press Enter.

4.  Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant
    Admin password.

5.  In the Microsoft Azure portal, in the navigation pane, select **Azure Active
    Directory**.

6.  On the **Azure Active Directory** blade, select **Company branding**, and
    then select **Configure**.

7.  On the **Configure company branding** blade, configure the following
    settings:

-   Sign-in page text: **Adatum.com sign-in page**

-   Show option to remain signed in: Select **Yes**.

1.  Select **Save**, and then close the **Configure company branding** blade.

2.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Properties**.

3.  In the **Name** text box, type **Azure AD**, and then select **Save**.

### Task 2: Create a user and group in Azure AD

1.  On the Azure Active Directory blade, select **Users**.

2.  In the Users - All users blade, select **+ New user**.

3.  In the User blade, enter the following information:

    * Name: _Your name_

    * Username: **Yourname\@yourtenant.onmicrosoft.com**

    * First name: _Your first name_

    * Last name: _Your second name_

    * Department: **IT**

    _Note: Leave no spaces in your username._

1.  Select the **Show Password** check box and note the password for later use.

2.  Select **Create**.

3.  In the navigation pane, click **Azure Active Directory**, and then click
    **Groups**.

4.  In the Groups - All groups blade, select **+ New group**.

5.  In the Group blade, in the **Group type** list, select **Security**.

6.  In the **Group name** box, type **IT Devices**.

7.  In the **Group description** box, type **IT Department Devices**.

8.  In the **Membership type** list, select **Dynamic device**.

9.  Click **Add dynamic query**.

10. Click **Edit** above the **Rule syntax** box.

11. In the Rule syntax text box, replace any existing text with the following
    text and then click **OK**.

```
    (device.devicePhysicalIDs -any \_ -contains "[ZTDId]")
```
1.  Click **Save** to close Dynamic membership rules.

2.  Click **Create** to create the group.

3.  Navigate to All groups. Notice the IT Devices group.

### Task 3: Generate a device-specific comma-separated value (CSV) file

1.  Switch to **LON-HOST1** and sign in as **Admin** with the password of
    **Pa55w.rd**.

2.  Select **Hyper-V Manager** in the task bar to launch.

3.  Under Virtual Machines, right-click LON-CL5 and select Connect.

    _Note: When connecting to LON-CL5, you should see the Windows 10 desktop.  If there is a process still running, allow it to finish before continuing._

4.  At the desktop on **LON-CL5** on the taskbar, right-click **Start**, select
    **Windows PowerShell (Admin)**, and then select **Yes** at the **User
    Account Control** prompt.

5.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Install-Script -Name Get-WindowsAutoPilotInfo
```
1.  You will receive two prompts. Each time, type **Y**, and then press Enter.

2.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Set-ExecutionPolicy RemoteSigned
```
1.  When prompted, type **Y**, and then press Enter.

2.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv
```
1.  At the Windows PowerShell command-line prompt, type the following command,
    press **Enter**, and then review the file content:

```
type C:\Computer.csv
```
### Task 4: Work with a Windows AutoPilot deployment profile

1.  On **LON-CL5**, in **Microsoft Edge**, open a new tab and navigate to
    **https://office.com**. If prompted, sign in with your
    **Admin\@yourtenant.onmicrosoft.com**.

2.  Click **Admin**, and then, in the **Microsoft 365 admin center**, click
    **Show all**, click **All admin centers**, and then click the **Device
    Management** tile. A new tab opens.

3.  In the **Microsoft 365 Device Management** console, in the navigation pane,
    click **Device enrollment**.

4.  On the **Choose MDM Authority** blade which appears on the right, select
    **Intune MDM Authority** and click **Choose**.  
      
    *Note: Setting the MDM Authority is not an exclusive step for Autopilot, but
    must be configured for using Intune and Autopilot.*

5.  On the Device enrollment blade, click **Windows enrollment**.

6.  In the details pane, select **Devices**.

7.  On the menu bar, select **Import**, browse to **c:\\**, select
    **Computer.csv**, click **Open**, and then select **Import**. The import
    process can take up to 15 minutes, but normally takes around 5 minutes.  
      
    Note: After the process is complete, the device may not show. If this is the
    case, select the **Sync** button, wait a few minutes, and then select
    **Refresh**.

8.  Click **X** to close the Windows Autopilot devices blade, and then, on the
    Windows enrollment blade, click **Deployment Profiles**.

9.  On the **Windows AutoPilot deployment profiles** blade, select **Create
    profile**.

10. In the details pane, in the **Name** text box, type **Contoso profile1**.

11. Click **No**, and then click **Next**.

12. On the **Out-of-box experience** blade, ensure that the **Deployment mode**
    is **User-Driven**.

13. Ensure that **Join to Azure AD as** is **Azure AD Joined**.

14. Ensure that the following options are set:

    -   Microsoft Software License Terms: **Hide**

    -   Privacy Settings: **Hide**

    -   Hide change account options: **Hide**

    -   User account type: **Administrator**.

    -   Allow White Glove OOBE: **No**.

    -   Apply device name template: **No**.

1.  Click **Next**.

2.  On the **Scope tags** blade, click **Next**.

3.  On the **Assignments** blade, click **Select groups to include**.

4.  Select the **IT Devices** group and click **Select**.

5.  Click **Next**.

6.  On the **Review + create** blade, review the information then click
    **Create**.

7.  Click the newly created profile.

### Task 5: Reset the PC

*Note: Normally this step is not required for physical devices, the device’s
autopilot info is either provided by the manufacturer or can be obtained from
the device prior to the OOBE. For the purposes of this lab, we must initiate a
reset to simulate a new device OOBE.*

1.  On LON-CL5, select **Start** and type **reset** and select **Reset this
    PC**.

2.  Under **Reset this PC**, select **Get Started**.

3.  Select **Remove everything**, then **Just remove my** files.

4.  Click **Reset**.

_Note: This process can take 30-45 minutes and will reboot several times during
the process. When LON-CL5 reboots, do not press a key to boot from media, allow
the reset to continue._

### Task 6: Verify Autopilot deployment

1.  At the **Let’s start with region. Is this right?** Screen, select **Yes**.

2.  At the **Is this the right keyboard layout?** Screen, select **Yes**

3.  At the **Want to add a second keyboard layout?** screen, select **Skip**

4.  At the **Welcome to Azure AD** screen, enter
    *yourname\@yourtenant.onmicrosoft.com (from Task 2)* and select **Next**.

5.  Enter the temporary password you were given and select **Next**.

6.  At the **Update your password** screen, enter your *current password*, then
    enter a new password twice, and then click **Sign in.**

7.  At the screen to setup a pin, select **Setup a Pin**.

8.  Click the **X** at the top of the **More information required** window.

9.  At the Something went wrong screen, select **Skip for now**  
      
    _The provisioning process will complete and arrive at the desktop. Note that
    the privacy settings and options to change the account did not display._

10. Click **Start** and type *access work* and select **Access work or school**

11. Verify the device is joined to Azure AD.

12. Switch to **LON-CL3**.

13. In the Azure portal, select **Azure Active Directory** and then **Devices**.

14. Note that the device is showing as enabled and you are the owner.

**END OF LAB**