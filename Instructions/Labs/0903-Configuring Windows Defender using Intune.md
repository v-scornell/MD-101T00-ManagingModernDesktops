# Practice Lab - Configuring Windows Defender using Intune

## Summary

In this lab, you will practice creating a policy to configure Windows Defender for enrolled devices.

### Scenario

You've been asked to ensure that enrolled devices have Windows Defender correctly configured. It's been requested that:
* Family options, Hardware protection and Device Performance and Health are hidden.
* IT contact name and department phone number must be added. 

Settings should be verified by testing on an enrolled device, LON-CL3 and a non-enrolled device, LON-CL1.


#### Task 1: Perform a quick scan in Windows Defender

1.  On **LON-CL1** selectselect **Start**, and then select **Settings**.

2.  In the Settings app, open **Update & Security**, and then open the **Windows
    Defender** tab.

3.  Select **Open Windows Defender Security Center**.

4.  In Windows Defender Security Center, select **Virus & threat protection**.

5.  On the Virus & threat protection page, select **Quick scan**.

6.  Review the results.

7.  Close Windows Defender Security Center.

#### Task 2: Configure Windows Defender in Intune

1.  On **LON-CL3**, restore the browser windows with the Azure portal. If needed
    navigate to Intune.

2.  In the Intune console, selectselect on **Device configuration**

3.  In the Device configuration – Profiles pane, selectselect **Profiles**.

4.  Select **Create profile**.

5.  In the Create a profile pane, type **Windows Defender** for the profile
    name. Select **Windows 10 and later** for Platform. In the Profile type
    list, select **Endpoint protection**.

6.  In the Endpoint protection pane, selectselect the **Windows Defender
    Security Center** option.

7.  In the Windows Defender Security Center pane, selectselect **Hide** for
    **Family options**, **Hardware protection** and **Device Performance and
    Health**.

8.  For the **IT contact information** option select **Display in app and in
    notifications**.

9.  In the **IT organization name** field, type **Adatum IT**.

10. For **IT department phone number or Skype ID**, type **123-456** and then
    selectselect **OK**.

11. In the Endpoint protection pane selectselect **Windows Defender Firewall**.

12. In the Windows Firewall pane, selectselect **Block for File Transfer
    Protocol**.

13. Select on **Public (non-discoverable) network** and then selectselect
    **Block** for **Stealth mode** and selectselect **OK** three times.

14. On Create profile pane, selectselect **Create**.

15. Select **Assignments** and then selectselect **Select groups to include**.
    Choose the **Enrolled Devices** group and then selectselect **Select**.
    Select **Save**.

16. In the Microsoft Intune main pane, selectselect **Devices** and then
    selectselect the **Enrolled devices** icon.

17. On the All devices pane, selectselect **LON-CL3** and then on the LON-CL3
    pane, selectselect **Sync** on the toolbar. Select **Yes**.

18. Wait for 3-4 minutes.

#### Task 3: Verify the configuration

1.  On LON-CL3, open Windows Defender Security Center, by right-clicking the
    Defender icon in the taskbar and then selectselecting **View security
    dashboard**. Ensure that you don’t see the device performance & health icon.
    This is because settings that prevent showing device and performance health
    were applied from Intune.

2.  Switch to LON-CL1 and open Windows Defender Security Center. Ensure that you
    see the device performance & health icon. This is because LON-CL1 is not
    enrolled to Intune.

** END OF LAB **