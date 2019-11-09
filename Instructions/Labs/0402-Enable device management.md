# Practice Lab - Enable device management in Intune

## Summary

In this lab, you will configure Intune to allow users to enroll their devices in Intune and join Azure AD.

### Scenario

You have been asked to setup device enrollment in Intune. It should be configured so that users who join the device to the domain will also enroll in Intune.  You'll need to ensure that Joni Sherman, Megan Bowen and MOD Administrator are licensed with EMS E5 to enroll and that Megan Bowen is a local administrator on Azure AD joined devices.
MFA is not required and the maximum number of devices per user is 50.

### Task 1: Assign Intune and Azure AD Premium licenses to users

1.  Switch to **LON-CL3**. On **LON-CL3**, sign-in as **Admin** using
    **Pa55w.rd** as the password.

2.  On **LON-CL3**, on the taskbar, click **Microsoft Edge**.

3.  In Microsoft Edge, type **https://portal.azure.com** in the address bar, and
    then press **Enter**.

4.  Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant
    Admin password.

5.  If prompted by the **Stay Signed in?** windows, click **No**.

6.  Close any welcome dialogs.

7.  In the Edge browser, in the Azure portal, and in the navigation pane, click
    **Azure Active Directory**.

8.  On the **Azure Active Directory** blade, click **Users**, click **Joni
    Sherman**.

9. Under Settings, in the **Usage location** field, verify that **United
    States** is selected.

10. Click the **Users-All users** in the navigation breadcrumb at the top.
    Scroll the page to the left, on the page, click **Megan Bowen**. Under
    Settings, in the **Usage location** field, verify that **United States** is
    selected.

12. Scroll the page to the left, on the page, click **MOD Administrator**. Under
    Settings, in the **Usage location** field, verify that **United States** is
    selected.

**Note:** Before you can assign a license to a user, the user must have a usage
location set.

1.  Scroll the page to the left, on the **Azure Active Directory** blade click
    **Licenses** and then in the details pane click **All products**.

2.  On the **Products** blade, select **Enterprise Mobility + Security E5** and
    then in details pane click **+ Assign**.

3.  On the **Assign license** blade, click **Users and groups**. In the
    **Users** pane click **Joni Sherman**, **Megan Bowen**, and **MOD
    administrator.** Click **Select**, and then click **Assign**.

    _**Note:** Note the dialog that indicate the 3 licenses have been assigned._

### Task 2: Integrate Azure AD with Intune

1.  In **LON-CL3**, in the Azure portal, in the navigation pane, click **Azure
    Active Directory**.

2.  On the **Azure AD** blade, select Mobility (MDM and MAM). In the details pane, select Microsoft Intune.

3.  In the **MDM user scope** row, click **All** and
    then click **Save**.

    _**Note**: By performing this step, you allowed all users who join their device to Azure AD to automatically enroll it to Intune as well._

### Task 3: Configure Azure AD join

1.  In **LON-CL3**, in the Azure portal, scroll the page to the left on the page
    and then in the **Azure Active Directory** blade click **Devices**.

2.  In the details pane, verify that only one device is listed (the desktop you provisioned in the previous Autopilot lab)

3.  On the **Devices** pane, click **Device settings**.

4.  In the details pane, in the **Users may join devices to Azure AD** row,
    verify that **All** is selected. This means that all Azure AD users can join
    their devices to Azure Active Directory.

5.  In the **Additional local administrators on Azure AD joined devices** row
    click **Selected**, and under **Selected**, click **No member selected**. In
    **Local administrators on devices**, click **+Add members**, select **Megan
    Bowen**, click **Select**, and then click **OK.**

6.  Verify that **Require Multi-Factor Auth to join devices** is set to **No**
    and that the **Maximum number of devices per user** is set to **50**, and
    then click **Save**.

7.  Return to the **Azure Active Directory** blade, select **Users** then select
    **Joni Sherman**.

8.  Select **Reset password**, then in the dialog, select the **Reset password** button. 

9.  Take note of the temporary password, which will be needed for the next lab.



**END OF LAB**