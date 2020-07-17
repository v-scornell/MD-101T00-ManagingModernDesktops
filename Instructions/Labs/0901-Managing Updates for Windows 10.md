# Practice Lab - Managing updates for Windows 10

## Summary

In this lab you will practice configuring Windows Update settings using Intune.

### Scenario

You have been asked to configure Update Rings in Intune to manage Windows update settings. Devices should be configured to be in the Semi-Annual channel for Preview builds and Feature updates
deferred 45 days after release. You would like to test the settings using LON-CL3. 

#### Task 1: Verify current update settings for a single device

1.  Sign in to **LON-CL3** as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Select **Start**, and then select the **Settings** icon.

3.  In **Settings**, select **Update & Security**.

4.  On the **Windows Update** tab, select **Advanced options**.

5.  Select **Delivery Optimization**.

6.  On the **Delivery Optimization** page, verify that the **Allow downloads
    from other PCs** option is enabled.

7.  Select **PCs on my local network, and PCs on the Internet**.

8. In the navigation pane, select **Windows Insider Program**. Notice that you must change the level of diagnostic data before you can get Insider Preview builds. 

10. Under **Get Insider Preview builds**, select the **Diagnostics & Feedback** link. 

11. On the Diagnostics and feedback screen, set **Diagnostic data** setting to **Full**. 

12. In the Settings navigation on the left, select **Home**. Select **Update & Security** and then select **Windows Insider Program**. Note that the **Get Started** option is now available.

13. In the navigation pane, select **Windows Update**.

#### Task 2: Review applied settings

1.  On the **Windows Update** page, select **View update history**.

2.  Review the updates listed, if any, and then select **Uninstall updates**. If
    no updates are installed, go to step 4.

3.  Review the updates listed in **Installed Updates**. Close Installed Updates.

4.  On the **View update history** page, select **Back**. Close the **Settings** app.

#### Task 3: Configure update settings by using Intune

1.  On the taskbar, select **Microsoft Edge**. In Microsoft Edge, type 
    **https://endpoint.microsoft.com** in the address bar, and then press **Enter**.

2.  In the navigation pane, select **Devices** and then select **Windows 10 update rings**.

3.  On the **Devices | Windows 10 update rings** blade select **Create profile**.

4.  In the **Basics** blade, enter the following information, and then select **Next**:

    -   Name: **A. Datum Updates - standard**

    -   Description: **Standard Windows updates configuration in A. Datum.** 

5.  In the **Update ring settings** blade, enter the following information, and then select **Next**:

    -   Servicing channel: **Semi-Annual Channel**

    -   Feature update deferrral period \(days\): **45**

    -   Option to pause Windows updates: **Disable**

6.  On the **Assignments** blade, verify that **Assign to** is set to **Selected groups**, then
    select **Select groups to include**. On the **Select groups to include** blade, in the **Search** box, type **A**. Select **A. Datum Developer devices** and then select **Select**.

7.  Select **Next** and on the **Review + create** blade select **Create**

8.  From the navigation bar select **Configuration Profiles**.

9.  On the **Devices | Configuration profiles** blade, in the details
    pane, select **Create profile**.

7.  In the **Create a profile** blade, select the following options, and then select **Create**:

    -   Platform: **Windows 10 and later**

    -   Profile: **Delivery Optimization**

8.  In the **Basics** blade, enter the following information, and then select **Next**:

    -   Name: **A. Datum Developer - Delivery optimization**

    -   Description: **Delivery optimization for Developer in A. Datum.**

9.  In the **Configuration settings** blade, enter the following information, and then select **Next**:

    -   Download Mode: **HTTP only, no peering \(0\)**

10. On the **Assignments** blade, verify that **Assign to** is set to **Selected groups**, then
    select **Select groups to include**. On the **Select groups to include** blade, in the **Search** box, type **A**. Select **A. Datum Developer devices** and then select **Select**.

11.  Select **Next** twice, and on the **Review + create** blade select **Create**

#### Task 4: Verify that the device’s update settings are managed centrally

1.  Select **Start**, and then select the **Settings** icon.

2.  In the **Settings** app, select the **Accounts** tile and then select **Access
    work or school**.

3.  In the **Access work or school** section, select the **Connected to ADATUM's Azure AD** link and then select **Info**.

4.  In the **Managed by ADATUM** dialog box, select **Info**.  On the Managed by Azure
    AD page, select **Sync**. Wait for the synchronization to complete.  
    
5.  Select the left arrow in the upper left corner twice. Select **Update & Security**.

6.  Notice the red banner **Some settings are managed by your organization**. 

7.  Select **Advanced options**. Notice that under the **Choose when updates are
    installed** heading, Semi-Annual Channel is selected and not configurable.
    Also notice that the updates are deferred for 45 days.

8.  Select **Delivery Optimization**. Notice that **Allow downloads from other PCs** is not available.

9.  In the navigation pane, select **Windows Insider Program**.

10. On the **Windows Insider Program** tab, notice the **Some settings are
    hidden or managed by your organization** banner.

11.  Notice that the **Get started** button is unavailable. Close the **Settings** app.

12. In Microsoft Edge in the navigation pane, select **Devices** and then select **Windows 10 update rings**.

13. In the details pane select **A. Datum Updates - standard**. 

14.  In the details pane, under **Profile assignment status Windows 10 and later devices** and 
     under **Profile assignment status Windows 10 and later user**, **1** is displayed under Installed. This indicates that the update policy is set on one device and for one user. 

15.  Close all open apps and windows.

_Note: These labs are configured to prevent Windows Updates from being applied to
avoid delays and unintentional impact during the labs._

**END OF LAB**