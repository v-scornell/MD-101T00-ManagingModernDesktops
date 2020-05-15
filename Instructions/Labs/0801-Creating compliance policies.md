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

Enrolled devices should also be assigned a VPN configuration with the following properties:

* Connection Name: **Adatum VPN**
* Description: **Adatum VPN Server**
* Address: **vpn.adatum.com**
* Set as **default server**
* Connection Type: **F5 Access**
* Authentication Model: **Username and password**
* Custom XML: **\<f5-vpn-conf\>\<single-sign-on-credential />\</f5-vpn-conf\>**

#### Task 1: Create and apply compliance policy and enrollment restrictions

1.  In **LON-DC1**, in the Azure portal, select **Home** in the breadcrumb navigation, 
    then select **Intune**.

2.  On the **Microsoft Intune** blade, select **Device compliance**.

3.  On the **Device compliance** blade, select **Policies** and then in the
    details pane select **+Create Policy**.

4.  On the **Create a policy** blade, provide the following values:

    -  Platform: **Windows 10 and later**

5.  Select **Create**. On the Basics tab, provide the following values:

    -  Name: **Compliance1**

6. Select **Next**. On the **Compliance settings** tab, select **Device Health** and
    review the available settings.

7.  On the **Compliance settings** tab, expand **Device Properties**. In the **Minimum OS version** field, type
    **10.0.16299.15**.

8.  On the **Compliance settings** tab, expand **System Security**. Set the **Windows Defender Antimalware** setting to **Require**. 

9.  Select **Next**. On the **Actions for noncompliance** tab, note the action to Mark device noncompliant default setting is immediately. Review how you can
    configure the number of days after which the device is marked as noncompliant, and configuration additional actions. 
    
    select **OK** twice and then select **Create**.

10. Select **Next** twice. On the **Assignments** tab, choose **+ Select groups to include**.  Select **Windows Devices**, choose **Select**, and then select **Next**.

11. Select **Create**.


12. Scroll the page to the left and then on the **Microsoft Intune** blade, 
    select **Device enrollment**.

13. On the **Device enrollment** blade, select **Enrollment restrictions**.

14. On the details pane, in the **Device Type Restrictions** section, on the **Default** line, select
    **All Users**.
    
15. On the **All Users** blade, select **Properties**. In the **Platform settings** section, select **Edit**.

16. On the **Select platforms** blade, in the **Platform** column, on the rows with **iOS** and **macOS**, select **Block**. Select **Review + save** and then select **Save**.

17. Scroll left to the **Device Enrollment - Enrollment restrictions** blade. 
    In the **Device Limit Restrictions** section, select **All Users** and then select **Properties**.

18. In the Device limit section, select **Edit**, then change the value to **3**.  

19. Select **Review + Save**, and then select **Save**.

#### Task 2: Create a device configuration profile

1.  In **LON-DC1**, in the Azure portal, scroll the page to the left and then on
    the **Microsoft Intune** blade select **Device configuration**.

2.  On the **Device configuration** blade, select **Profiles** and then select
    **+Create profile**.

3.  Under **Platform**, select **Windows 10 and later**.

4.  Under **Profile type**, select **VPN**.

5.  On the Basic tab, configure the following values: 

    -  Name: **Adatum VPN**

    -  Description **Corporate VPN for Adatum**.

6.  Select **Next**. On the **VPN** blade, expand **Base VPN** and configure the following values:

    - Connection name: **Adatum VPN**

    - Connection type: **F5 Access**

    - Authentication model: **Username and password**

7.  Under **Servers**, enter the following information:

    -  Description: **Adatum VPN Server**

    -  IP Address or FQDN: **vpn.adatum.com**

    -  Default server: **True**

8. In the **Custom XML** box, enter the following code:

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```
9.  Select **Next** twice. On the **Assignments** tab, choose **+ Select groups to include**.

10.  Select **Windows Devices**, and then choose **Select**.

11.  Select **Next** twice and then select **Create**.


## Exercise 2: Creating a conditional access policy

### Scenario 

When devices are non-compliant, they should not be able to access their e-mail. You've been asked to configure a conditional access policy that enforces this rule, and verify it functions as expected.

#### Task 1: Create a conditional access policy

1.  On **LON-DC1**, in the Azure portal, on the **Microsoft Intune** blade, select **Conditional
    access**.

2.  In the **Details** pane, select **+New policy**.

3.  On the **New** blade, in the **Name** text box, type **Conditional1** and
    then select **Users and groups**.

4.  On the **Users and groups** blade, select the **All users** radio button and
    then select **Done**.

5.  On the **New** blade, select **Cloud apps**, select the **Select apps** radio
    button, select **Select**, select **Office 365 Exchange Online**, select
    **Select,** and then select **Done**.

6.  On the **New** blade, select **Conditions**, select **Device platforms**, in
    the **Configure** section select **Yes**, select the **Select device
    platforms** radio button, select the **Windows** check box, and then select
    **Done** twice.

7.  On the **New** blade under access controls, select **Grant**, select the
    **Require device to be marked as compliant** check box, and then select
    **Select**.

8.  On the **New** blade, select **On** for the **Enable policy** option and
    then select **Create**.

#### Task 4: Verify that the conditional access policy is working

1.  On **LON-CL1**, sign in as **adatum\\administrator** with the password **Pa55w.rd**. 
    Open a new Microsoft Edge tab, then and open <https://portal.office.com>.

2.  Sign in as **admin\@yourtenant.onmicrosoft.com**. On the Office 365 portal, 
    select the **Outlook** icon. 

3.  Verify that you receive the message **"You can't get there from here"**.

4.  Select **More details**. You should see more information about why you are
    blocked. This is because LON-CL1 is not joined to Azure AD and not managed
    by Intune, so not marked as compliant.

5.  **Close** the browser window.

6.  Switch to **LON-CL3**, and sign in as **admin\@yourtenant.onmicrosoft.com**. 

7.  Open a new Microsoft Edge tab, then and open **https://portal.office.com**.
    On the Office 365 portal, select the **Outlook** icon. 

8.  Verify that you receive the message **"Oops - You can’t get to this yet"**.
    Note that this message indicates the device is registered that a policy
    is being applied to bring the device to a compliant state. 

9. Switch to **LON-CL4**.  Repeat steps 7 & 8.

10. Ensure that you can access your mailbox. 

    This is because LON-CL4 is a
    managed device and marked as compliant. You might get a message that device
    is being checked for compliance. If that happens, wait for a few minutes and
    then try again.

**END OF LAB**