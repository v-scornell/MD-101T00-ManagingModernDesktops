# Practice Lab - Creating compliance and conditional access policies

## Summary

In this lab, you will practice creating a compliance policy and assign it to a device. You'll also create conditional access rules based on the compliance status of a device. 

## Exercise 1: Configuring compliance policies 

### Scenario

A. Datum would like to ensure that enrolled Windows 10 devices meet a minimum configuration specification.  The following are required:

* Minimum OS version: 10.0.17763.615
* Windows Defender Antimalware required
* iOS and MacOS platforms blocked

If the device does not meet these requirement, the device should be marked as non-compliant.

#### Task 1: Create and apply compliance policy and enrollment restrictions

1.  Sign in to **LON-CL1** as **ADATUM\\Administrator** with the password **Pa55w.rd**. 

2.  In Microsoft Edge, type **https://endpoint.microsoft.com** in the  address bar, and then 
    press **Enter**. Sign in as as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

3.  From the navigation pane select **Devices**, then select **Compliance Policies**.

4.  On the **Compliance policies | Policies** blade, in the details pane select **Create Policy**.

5.  On the **Create a policy** blade, provide the following values and select **Create**:

    -  Platform: **Windows 10 and later**

6.  On the Basics tab, provide the following values and select **Next**:

    -  Name: **Compliance1**

7.  On the **Compliance settings** tab, select **Device Health** and
    review the available settings.

8.  On the **Compliance settings** tab, expand **Device Properties**. In the **Minimum OS version**
    field, type **10.0.16299.15**.

9.  On the **Compliance settings** tab, expand **System Security**. Set the 
    **Windows Defender Antimalware** setting to **Require**. 

10. Select **Next**. On the **Actions for noncompliance** tab, note the action to Mark device
    noncompliant default setting is immediately. Review how you can configure the number of days after which the device is marked as noncompliant, and configuration additional actions. 

11. Select **Next**. On the **Assignments** tab, choose **Select groups to include**.  Select 
    **Windows Devices**, choose **Select**, and then select **Next**.

12. Select **Create**.

13. Select **Devices**, then select **Enroll devices**.

14. On the **Enrollment devices | Windows enrollment** blade, select **Enrollment restrictions**.

15. On the details pane, in the **Device Type Restrictions** section, on the **Default** line, select
    **All Users**.
    
16. On the **All Users** blade, select **Properties**. In the **Platform settings** section, select **Edit**.

17. On the **Platforms settings** blade, in the **Platform** column, on the rows with **iOS/iPadOS** and **macOS**, select **Block**. Select **Review + save** and then select **Save**.

18. Scroll left to the **Device Enrollment | Enrollment restrictions** blade. 
    In the **Device Limit Restrictions** section, select **All Users** and then select **Properties**.

19. In the **Device limit** section, select **Edit**, then change the value to **3**.  

20. Select **Review + Save**, and then select **Save**.


## Exercise 2: Creating a conditional access policy

### Scenario 

When devices are non-compliant, they should not be able to access their e-mail. You've been asked to configure a conditional access policy that enforces this rule, and verify it functions as expected.

#### Task 1: Create a conditional access policy

1.  On **LON-CL1**, in the **Microsoft Endpoint Manager admin center** select **Devices**, 
    then select **Conditional Access**.

2.  In the **Details** pane, select **New policy**.

3.  On the **New** blade, in the **Name** text box, type **Conditional1** and
    then select **Users and groups**.

4.  On the **Users and groups** blade, select the **All users** radio button.

5.  On the **New** blade, select **Cloud apps or actions**, select the **Select apps** radio
    button, select **Select**, select **Office 365 Exchange Online**, and then select
    **Select**

6.  On the **New** blade, select **Conditions**, select **Device platforms**, in
    the **Configure** section select **Yes**, select the **Select device
    platforms** radio button, select the **Windows** check box, and then select
    **Done**.

7.  On the **New** blade under **Access controls**, select **Grant**, select the
    **Require device to be marked as compliant** check box, and then select
    **Select**.

8.  On the **New** blade, select **On** for the **Enable policy** option and
    then select **Create**.

#### Task 4: Verify that the conditional access policy is working

1.  On **LON-CL1**, open a new Microsoft Edge tab, then and open <https://portal.office.com>.

2.  Select the **Outlook** icon. 

3.  Verify that you receive the message **"You can't get there from here"**.

4.  Select **More details**. You should see more information about why you are
    blocked. 
    
    _Note: This is because LON-CL1 is not joined to Azure AD and not managed
    by Intune, so not marked as compliant._

5.  **Close** the browser window.

6.  Switch to **LON-CL3**, and sign in as **admin\@yourtenant.onmicrosoft.com**. 

7.  Open **Microsoft Edge**, then and open **https://portal.office.com**.
    On the Office 365 portal, select the **Outlook** icon. 

8. Ensure that you can access your mailbox. 

    _Note: This is because LON-CL3 is a managed device and marked as compliant. You might get a message that device is being checked for compliance. If that happens, wait for a few minutes and
    then try again._

**END OF LAB**