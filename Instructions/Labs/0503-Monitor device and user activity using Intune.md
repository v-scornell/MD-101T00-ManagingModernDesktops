# Practice Lab - Monitor device and user activity using Intune

## Summary

In this lab, you will practice monitoring user activity and device profiles.

### Scenario

You have been asked to review Diego Siciliani's sign-in activity.  You have also been asked to verify the hardware on his device, LON-CL4, and confirm the device profile assigned to his device is successfully applied. 

#### Task 1: Monitor user activity

1.  On **LON-CL3**, in the Azure portal, click **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, click **Users**.

2.  Click **Sign-ins**, in the details pane, you can see sign-ins for your
    users. Click on the first entry where the **Name** column says **Diego
    Siciliani**.

3.  In the details pane, you can see information about Diego Siciliani´s
    sign-in. Scroll to examine the information. Some of them will not contain
    any information because of the configuration.

4.  Click **Audit logs** and in the details pane, you will see audit information
    about changes made to users. Examine the information by clicking the various
    entries.

#### Task 2: Monitor device activity

1.  Click **Intune** in the navigation pane, and then on the **Microsoft
    Intune** blade, click **Devices**.

2.  On the **Devices** blade, in the details pane, you will see information
    about enrolled devices.

3.  Click **All devices**, and on the **All device** blade in the details pane,
    click **LON-CL4**. You will see information about the device such as name,
    associated user and operating system.

4.  Click **Hardware** and examine the hardware inventory.

5.  Click **Device configuration** and in the details pane, you can see
    information about profiles deployed to the device. The **STATE** column
    should display **Succeeded**, which means that they profiles were applied
    successfully to the device.

6.  Click **A. Datum developer – standard** in the details pane. On the **A.
    Datum developers – standard** blade, you will see the state of each setting
    you configured in the profile. The **STATE** should say **Succeeded** next
    to all of them.
