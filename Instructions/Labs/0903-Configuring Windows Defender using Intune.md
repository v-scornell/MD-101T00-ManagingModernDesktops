# Practice Lab - Configuring Windows Defender using Intune

## Summary

In this lab, you will practice creating a policy to configure Windows Defender for a group of devices.

### Scenario

You've been asked to ensure that the A. Datum Developers Group have Windows Defender correctly configured. It's been requested that:
* Family options, Hardware protection and Device Performance and Health are hidden.
* IT contact name and department phone number must be added. 

Settings should be verified by testing on an enrolled device, LON-CL3 and a non-enrolled device, LON-CL1.


#### Task 1: Perform a quick scan in Windows Defender

1.  On **LON-CL1** select **Start**, and then select **Settings**.

2.  In the **Settings** app, open **Update & Security**, and then open the **Windows Security** tab.

3.  In the **Windows Security** pane, select **Open Windows Security**.

4.  In **Windows Security** window, in the **Security at a glance** pane, select **Virus & threat protection**.

5.  On the **Virus & threat protection** page, select **Quick scan**.

6.  Review the results and **close** the **Windows Security** window.

#### Task 2: Configure Windows Defender in Intune

1.  On **LON-CL3**, restore the browser windows with the Azure portal. If needed
    navigate to Intune.

2.  In the Intune console, select on **Device configuration**

3.  In the **Device configuration – Profiles** pane, select **Profiles**, then select **Create profile**.

4.  In the **Create a profile** pane, select **Windows 10 and later** for Platform. In the Profile type list, select **Endpoint protection**.

5.  Select **Create**. On the Basics tab, in the **Name** field, enter **Windows Defender**. Select **Next**.

6.  On the **Configuration settings** tab, expand **Windows Defender Security Center** option. 

7.  Set the **Family options**, **Hardware protection** and **Device Performance and Health** options to **Hide**.

8.  For the **IT contact information** option select **Display in app and in notifications**.

9.  In the **IT organization name** field, enter **Adatum IT**.

10. For **IT department phone number or Skype ID**, enter **123-456**.

11. On the **Configuration settings** tab, expand **Windows Defender Firewall**.

12. Set the **File Transfer Protocol** option to **Block**.

13. Expand **Public (non-discoverable) network** and set the
**Stealth mode** option to **Block**.

14. Select **Next** twice.  On the **Assignments** tab, select **+ Select groups to include**. Choose the **A. Datum Developers Devices** group and then choose **Select**.

15. Select **Next** twice. On the **Review + Create** tab, review the information and select **Create**.

16. In the breadcrumb menu, select **Microsoft Intune**. Select **Devices** and then **All Devices**.   

17. On the **All devices** pane, select **LON-CL3** and then on the LON-CL3 blade, select **Sync** on the toolbar, and then select **Yes**.

18. Wait for 3-4 minutes.

#### Task 3: Verify the configuration

1. On **LON-CL3**, right-click the **Windows Security icon** in the taskbar to open Windows Security. Ensure that you don’t see the Device performance & health icon.

    This is because settings that prevent showing device and performance health were applied from Intune.

2. Switch to **LON-CL1** and open **Windows Security**. Ensure that you see the device performance & health icon. 

    This is because LON-CL1 is not enrolled to Intune.

**END OF LAB**