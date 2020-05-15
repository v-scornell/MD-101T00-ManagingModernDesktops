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

2.  On **LON-CL3**, on the taskbar, select **Microsoft Edge**.

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

8.  Select **Save**, and then close the **Configure company branding** blade.

9.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Properties**.

10.  In the **Name** text box, type **ADATUM**, and then select **Save**.

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

4.  Select the **Show Password** check box and note the password for later use.

5.  Select **Create**.

6.  In the navigation pane, select **Azure Active Directory**, and then select
    **Groups**.

7.  In the Groups - All groups blade, select **+ New group**.

8.  In the Group blade, in the **Group type** list, select **Security**.

9.  In the **Group name** box, type **IT Devices**.

10.  In the **Group description** box, type **IT Department Devices**.

11.  In the **Membership type** list, select **Dynamic device**.

12.  select **Add dynamic query**.

13. select **Edit** above the **Rule syntax** box.

14. In the Rule syntax text box, replace any existing text with the following
    text and then select **OK**.

```
    (device.devicePhysicalIDs -any _ -contains "[ZTDId]")
```
15.  select **Save** to close Dynamic membership rules.

16.  select **Create** to create the group.

17.  Navigate to All groups. Notice the IT Devices group.

### Task 3: Generate a device-specific comma-separated value (CSV) file

1.  Switch to **LON-HOST1** and sign in as **Adatum\Administrator** with the password of
    **Pa55w.rd**.

2.  Select **Hyper-V Manager** in the task bar to launch.

3.  Under Virtual Machines, right-click **LON-CL5** and select **Connect**.

    _Note: When connecting to LON-CL5, you should see the Windows 10 desktop.  If there is a process still running, allow it to finish before continuing._

4.  At the desktop on **LON-CL5** on the taskbar, right-click **Start**, select
    **Windows PowerShell (Admin)**, and then select **Yes** at the **User
    Account Control** prompt.

5.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Install-Script -Name Get-WindowsAutoPilotInfo
```
6.  You will receive two prompts. Each time, type **Y**, and then press Enter.

7.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Set-ExecutionPolicy RemoteSigned
```
8.  When prompted, type **Y**, and then press Enter.

9.  At the Windows PowerShell command-line prompt, type the following cmdlet,
    and then press **Enter**:

```
Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv
```
10.  At the Windows PowerShell command-line prompt, type the following command,
    press **Enter**, and then review the file content:

```
type C:\Computer.csv
```
### Task 4: Work with a Windows AutoPilot deployment profile

1.  On **LON-CL5**, in **Microsoft Edge**, open a new tab and navigate to
    **https://endpoint.microsoft.com**. If prompted, sign in with your
    **Admin\@yourtenant.onmicrosoft.com**.

2.  In the **Microsoft Endpoint Manager admin center**, select the orange banner to open the **Mobile Device Management Authority** setting. 

    _Note: The orange banner is only displayed if you haven't yet set the MDM authority. If you do not see the banner, your MDM authority is already set and you may **proceed to step 4**._

3.  On the **Choose MDM Authority** blade which appears on the right, select
    **Intune MDM Authority** and select **Choose**.  
      
    _Note: Setting the MDM Authority is not an exclusive step for Autopilot, but
    must be configured for using Intune and Autopilot._

4.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the left rail.

5.  In the **Device enrollment** section, select **Enroll devices**. 

6.  In the details pane, select **Devices**.

7.  On the menu bar, select **Import**, browse to **c:\\**, select
    **Computer.csv**, select **Open**, and then select **Import**. The import
    process can take up to 15 minutes, but normally takes around 5 minutes.  
      
    **Important**: After the process is complete, the device may not show. If this is the
    case, select the **Sync** button, wait a few minutes, and then select
    **Refresh**.

8.  Select **X** to close the Windows Autopilot devices blade. On the
    Windows enrollment blade, in the details pane, select **Deployment Profiles**.

9.  On the **Windows AutoPilot deployment profiles** blade, select **Create profile**.

10. In the details pane, in the **Name** text box, type **Contoso profile1**.

11. select **No**, and then select **Next**.

12. On the **Out-of-box experience** blade, ensure that the **Deployment mode**
    is set to **User-Driven**.

13. Ensure that **Join to Azure AD as** is set to **Azure AD Joined**.

14. Ensure that the following options are set:

    -   Microsoft Software License Terms: **Hide**

    -   Privacy Settings: **Hide**

    -   Hide change account options: **Hide**

    -   User account type: **Administrator**.

    -   Allow White Glove OOBE: **No**.

    -   Apply device name template: **No**.

15.  Select **Next**.

16.  On the **Assignments** blade, select **Select groups to include**.

17.  Select the **IT Devices** group and select **Select**.

18.  Select **Next**.

19.  On the **Review + create** blade, review the information then select
    **Create**.

### Task 5: Reset the PC


1.  On LON-CL5, select **Start** and type **reset** and select **Reset this
    PC**.

2.  Under **Reset this PC**, select **Get Started**.

3.  Select **Remove everything**, then **Just remove my** files.

4.  select **Reset**.

_Note: Normally this task is not required for new deployment of physical devices. The device’s
autopilot info is either provided by the manufacturer or can be obtained from
the device prior to the OOBE. For the purposes of this lab, we must initiate a
reset to simulate a new device OOBE._

_Note: This process can take 30-45 minutes and will reboot several times during
the process. When LON-CL5 reboots, do not press a key to boot from media, allow
the reset to continue._

### Task 6: Verify Autopilot deployment

1.  At the **Let’s start with region. Is this right?** Screen, select **Yes**.

2.  At the **Is this the right keyboard layout?** Screen, select **Yes**

3.  At the **Want to add a second keyboard layout?** screen, select **Skip**

4.  At the **Welcome to ADATUM** screen, enter
    *yourname\@yourtenant.onmicrosoft.com (from Task 2)* and select **Next**.

5.  Enter the temporary password you were given and select **Next**.

6.  At the **Update your password** screen, enter your *current password*, then
    enter a new password twice, and then select **Sign in.**

7.  At the screen to setup a pin, select **Setup a Pin**.

8.  select the **X** at the top of the **More information required** window.

9.  At the Something went wrong screen, select **Skip for now**  
      
    _The provisioning process will complete and arrive at the desktop. Note that
    the privacy settings and options to change the account did not display._

10. select **Start** and type *access work* and select **Access work or school**

11. Verify the device is joined to Azure AD.

12. Switch to **LON-CL3**.

13. In the Azure portal, select **Azure Active Directory** and then **Devices**.

14. Note that the device is showing as enabled and you are the owner.

**END OF LAB**