# Practice Lab - Managing updates for Windows 10

## Summary

In this lab you will practice configuring Windows Update settings using Group Policy.

### Scenario

You have been asked to configure Group Policy to manage Windows update settings. Devices should be
configured to be in the Semi-Annual channel for Preview builds and Feature updates
deferred 45 days after release. You would like to test the settings first using the local Group Policy editor on LON-CL1. 

### Task 1: Verify current update settings for a single device

1.  Switch to **LON-CL1**.

2.  Sign in as **Adatum\\Administrator** with the password of **Pa55w.rd**.

3.  Click **Start**, and then select the **Settings** icon.

4.  In **Settings**, select **Update & Security**.

5.  On the **Windows Update** tab, select **Advanced options**.

6.  Click **Delivery Optimization**.

7.  On the **Delivery Optimization** page, verify that the **Allow downloads
    from other PCs** option is enabled.

8.  Select **PCs on my local network, and PCs on the Internet**, and then click
    **Back**.

9.  Click **Back**.

10. In the navigation pane, select **Windows Insider Program**. Notice that the
    **Get Started** option is available.

11. In the navigation pane, select **Windows Update**.

### Task 2: Review applied settings

1.  On the **Windows Update** page, select **View update history**.

2.  Review the updates listed, if any, and then click **Uninstall updates**. If
    no updates are installed, go to step 4.

3.  Review the updates listed in **Installed Updates**. Close Installed Updates.

4.  On the **View update history** page, click **Back**.

### Task 3: Configure update settings by using GPOs

1.  Right-click **Start** and then click **Run**.

2.  In Run, type **gpedit.msc**, and then press Enter.

3.  In **Local Group Policy Editor**, navigate to **Computer
    Configuration/Administrative Templates/Windows Components/Data Collection
    and Preview Builds**.

4.  In the right pane, double-click **Toggle user control over Insider builds**.

5.  In the **Toggle user control over Insider builds** dialog box, click
    **Disabled**, and then click **OK**.

6.  In **Local Group Policy Editor**, navigate to **Computer
    Configuration/Administrative Templates/Windows Components/Windows
    Update/Windows Update for Business**.

7.  In the right pane, double-click **Select when Preview Builds and Feature
    Updates are received**.

8.  In the **Select when Preview Builds and Feature Updates are received**
    dialog box, click **Enabled**.

9.  In the **Select the Windows readiness level for the updates you want to
    receive** list, click **Semi-Annual Channel**.

10. In the **After a Preview build or Feature Update is released, defer
    receiving it for this many days** text box, type **45**, and then click
    **OK**.

11. In the navigation pane, click **Windows Update**.

12. In the right pane, double-click **Do not connect to any Windows Update
    Internet locations**.

13. In the **Do not connect to any Windows Update Internet locations** dialog
    box, click **Enabled**, and then click **OK**.

14. Close the Local Group Policy Editor.

### Task 4: Verify that the device’s update settings are managed centrally

1.  Right-click **Start**, and then click **Windows PowerShell (Admin)**.

2.  In the command prompt, type **gpupdate /force**, and then press Enter.

3.  Switch to **Windows Settings**.

4.  In the navigation pane, click **Windows Insider Program**.

5.  On the **Windows Insider Program** tab, notice the **Some settings are
    hidden or managed by your organization** banner.

6.  Notice that the **Get started** button is unavailable.

7.  Click **Windows Update**.

8.  Click **Advanced options**. Notice that under the **Choose when updates are
    installed** heading, Semi-Annual Channel is selected and not configurable.
    Also notice that the updates are deferred for 45 days.

9.  Close all open apps and windows.

_Note: These labs are configured to prevent Windows Updates from being applied to
avoid delays and unintentional impact during the labs._

**END OF LAB**