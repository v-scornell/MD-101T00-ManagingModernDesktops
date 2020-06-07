# Practice Lab - Enable device management in Intune

## Summary

In this lab, you will configure Intune to allow users to enroll their devices in Intune and join Azure AD.

### Scenario

You have been asked to setup device enrollment in Intune. It should be configured so that users who join the device to the domain will also enroll in Intune.  You'll need to ensure that Joni Sherman, Megan Bowen and MOD Administrator are licensed with EMS E5 to enroll and that Megan Bowen is a local administrator on Azure AD joined devices.
MFA is not required and the maximum number of devices per user is 50.

#### Task 1: Assign Microsoft Intune and Azure AD Premium licenses to users

1.  Switch to **LON-CL3**. On **LON-CL3**, sign in as **Admin** using
    **Pa55w.rd** as the password.

2.  On **LON-CL3**, on the taskbar, select **Microsoft Edge**.

3.  In Microsoft Edge, type **https://portal.azure.com** in the address bar, and
    then press **Enter**.

4.  Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant
    admin password.

5.  If prompted by the **Stay Signed in?** window, select **No**.

6.  Close any welcome dialogs.

7.  In the Edge browser, in the Azure portal, and in the navigation pane, select
    **Azure Active Directory**.

8.  On the **Azure Active Directory** blade, select **Users**, and then select **Joni
    Sherman**.

9. Under Settings, in the **Usage location** field, verify that **United States** is selected.

10. Select the **Users | All users** in the navigation breadcrumb at the top.
    Select **Megan Bowen**. Under Settings, in the **Usage location** field, verify that **United States** is selected.

11. Scroll the page to the left, on the page, select **MOD Administrator**. Under
    Settings, in the **Usage location** field, verify that **United States** is
    selected.

    _Note: Before you can assign a license to a user, the user must have a usage
location set._

12.  Scroll the page to the left, on the **Azure Active Directory** blade select
    **Licenses** and then in the navigation pane select **All products**.

13.  On the **Licenses | All products** blade, select **Enterprise Mobility + Security E5** and
    then in details pane select **Assign**.

14.  On the **Assign license** blade, select **Users and groups**. In the
    **Users and groups** pane select **Joni Sherman**, **Megan Bowen**, and **MOD
    administrator.** Select **Select**, and then select **Assign**.

    _Note: Note the dialog that indicate the 3 licenses have been assigned._

#### Task 2: Integrate Azure AD with Microsoft Intune

1.  In **LON-CL3**, in the Azure AD portal, close the **Licenses | All products** blade.

2.  On the **Azure AD** blade, select **Mobility (MDM and MAM)**. In the details pane, select **Microsoft Intune**.

3.  In the **MDM user scope** row, select **All** and then select **Save**.

    _**Note**: By performing this step, you allowed all users who join their device to Azure AD to automatically enroll it to Microsoft Intune as well._

#### Task 3: Configure Azure AD join

1.  In **LON-CL3**, in the Azure portal, scroll the page to the left on the page
    and then in the **Azure Active Directory** blade select **Devices**.

2.  In the details pane, verify that only hybrid joined devices are listed from the 
    previous lab.

3.  On the **Devices** pane, select **Device settings**.

4.  In the details pane, in the **Users may join devices to Azure AD** row,
    verify that **All** is selected. This means that all Azure AD users can join
    their devices to Azure Active Directory.

5.  In the **Additional local administrators on Azure AD joined devices** row
    select **Selected**, and under **Selected**, select **No member selected**. In
    **Local administrators on devices**, select **Add**, select **Megan
    Bowen**, select **Select**, and then select **OK.**

6.  Verify that **Require Multi-Factor Auth to join devices** is set to **No**
    and that the **Maximum number of devices per user** is set to **50**, and
    then select **Save**.

7.  Return to the **Azure Active Directory** blade, select **Users** then select
    **Joni Sherman**.

8.  Select **Reset password**, then in the dialog, select the **Reset password** button. 

9.  Take note of the temporary password, which will be needed for the next lab.


**END OF LAB**