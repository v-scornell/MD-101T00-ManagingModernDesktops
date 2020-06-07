# Practice Lab - Configuring Windows Defender using Intune

## Summary

In this lab, you will practice creating a policy to configure Windows Defender for a group of devices.

### Scenario

You've been asked to ensure that the A. Datum Developers Group have Windows Defender correctly configured. It's been requested that:
* Family options, Hardware protection and Device Performance and Health are hidden.
* IT contact name and department phone number must be added. 

Settings should be verified by testing on an enrolled device, LON-CL3 and a non-enrolled device, LON-CL1.


#### Task 1: Perform a quick scan in Windows Defender

1.  On **LON-CL1** sign in as **Adatum\\Administrator** with the password **Pa55w.rd**.

2.  Select **Start**, and then select **Settings**.

3.  In the **Settings** app, open **Update & Security**, and then open the **Windows Security** tab.

4.  In the **Windows Security** pane, select **Open Windows Security**.

5.  In **Windows Security** window, in the **Security at a glance** pane, select **Virus & threat protection**.

6.  On the **Virus & threat protection** page, select **Quick scan**.

7.  Review the results and close the **Windows Security** window.

#### Task 2: Configure Windows Defender in Intune

1.  Switch to **LON-CL3** and sign in as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Open **Microsoft Edge**, and then navigate to **https://endpoint.microsoft.com**.

3.  Select **Devices**, then select **Configuration profiles**

4.  In the **Devices | Configuration profiles** pane, select **Create profile**.

5.  In the **Create a profile** pane, select **Windows 10 and later** for Platform. In the Profile  list, select **Endpoint protection**. Then select **Create**.

6.  On the Basics tab, in the **Name** field, enter **Windows Defender**. Select **Next**.

7.  On the **Configuration settings** tab, expand the **Windows Defender Security Center** option. 

8.  Set the **Family options**, **Hardware protection** and **Device Performance and Health** options to **Hide**.

9.  For the **IT contact information** option select **Display in app and in notifications**.

10. In the **IT organization name** field, enter **Adatum IT**.

11. For **IT department phone number or Skype ID**, enter **123-456**.

12. On the **Configuration settings** tab, expand **Windows Defender Firewall**.

13. Set the **File Transfer Protocol** option to **Block**.

14. Expand **Public (non-discoverable) network**, set the **Microsoft Defender Firewall** option 
    to **Enable** and set the **Stealth mode** option to **Block**.

15. Select **Next** .  On the **Assignments** tab, select **Select groups to include**. Choose the **A. Datum Developers Devices** group and then choose **Select**.

16. Select **Next** twice. On the **Review + Create** tab, review the information and select **Create**.

17. Select **Devices** and then **All Devices**.   

18. On the **Devices | All devices** pane, select **LON-CL3** and then on the **LON-CL3** blade, select **Sync** on the toolbar, and then select **Yes**.

19. Wait for 3-4 minutes.

#### Task 3: Verify the configuration

1.  On **LON-CL3**, right-click the **Windows Security icon** in the taskbar and select 
    **View security dashboard** to open Windows Security. Ensure that you don’t see the Device performance & health icon.

    _Note: This is because settings that prevent showing device and performance health were applied from Intune._

2.  Switch to **LON-CL1** and open **Windows Security**. Ensure that you see the device performance & health icon. 

    _Note: This is because LON-CL1 is not enrolled to Intune._

**END OF LAB**