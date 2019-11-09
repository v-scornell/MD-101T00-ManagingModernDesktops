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

1.  In **LON-DC1**, in the Azure portal, click **Home** in the breadcrumb navigation, 
    then select **Intune**.

2.  On the **Microsoft Intune** blade, click **Device compliance**.

3.  On the **Device compliance** blade, click **Policies** and then in the
    details pane click **+Create Policy**.

4.  On the **Create Policy** blade, provide the following values:

    -  Name: **Compliance1**

    -  Platform: **Windows 10 and later**

5.  On the **Windows 10 compliance policy** blade, click **Device Health** and
    review the available settings.

6.  On the **Windows 10 compliance policy** blade, click **Device Properties**.

7.  On the **Device Properties** blade, in the **Minimum OS version** row, type
    **10.0.16299.15** and then click **OK**.

8.  On the **Windows 10 compliance policy** blade, click **System Security**.

9.  On the System Security blade, in the Defender section, click **Require for
    Windows Defender Antimalware** and click **OK**.

10. On the **Windows 10 compliance policy** blade review the other available
    options and then click **OK**.

11. On the **Create Policy** blade, click **Actions for noncompliance** and then
    on the details pane, click **+Add**.

12. On the **Action parameters,** review the available options and then close
    the blade.

13. In the Actions blade click **Mark device noncompliant**. Review how you can
    configure the number of days after which the device is marked as
    noncompliant, click **OK** twice and then click **Create**.

14. On the **Compliance1** blade, click **Assignments**, click **Select groups
    to include**, click **Windows Devices**, click **Select,** and then click
    **Save**.

15. Scroll the page to the left and then on the **Microsoft Intune** blade, 
    click **Device enrollment**.

16. Review the available options on the **Device enrollment** blade.

17. On the **Device enrollment** blade, click **Enrollment restrictions**.

18. On the details pane, in the **Device Type Restrictions** section, click
    **Default,** click **Properties,** and then click **Edit**.

19. On the **Select platforms** blade, in the **iOS** and **macOS** rows click
    **Block**, then click **Review + save**, then click **Save**.

20. Scroll left to the **Device Enrollment - Enrollment restrictions** blade. 
    In the **Device Limit Restrictions** section, click **Default** and then
    click **Properties**.

21. Select **Edit**, then change the value to 3.  Select **Review + Save**.

#### Task 2: Create a device configuration profile

1.  In **LON-DC1**, in the Azure portal, scroll the page to the left and then on
    the **Microsoft Intune** blade click **Device configuration**.

2.  On the **Device configuration** blade, click **Profiles** and then click
    **+Create profile**.

3.  Enter the name **Adatum VPN** and the description **Corporate VPN for
    Adatum**.

4.  Under **Platform**, select **Windows 10 and later**.

5.  Under **Profile type**, select **VPN**.

6.  On the **VPN** blade, select **Base VPN**.

7.  For the Connection name, enter **Adatum VPN**.

8.  Under **Servers**, enter the following information, and then select **Add**:

    -  Description: **Adatum VPN Server**

    -  IP Address or FQDN: **vpn.adatum.com**

    -  Default server: **True**

9.  Next to **Connection type**, select **F5 Access**.

10. For the authentication model, select **Username and password**.

11. In the **Custom XML** box, enter the following code:

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```
1.  Select **OK** twice, and then select **Create**.

2.  On the **Adatum VPN device configuration profile** blade, select
    **Assignments**.

3.  Verify that **Include** is selected.

4.  Select **Select groups to include**.

5.  Select **Windows Devices**, and then select **Select**.

6.  Select **Save**.


## Exercise 2: Creating a conditional access policy

### Scenario 

When devices are non-compliant, they should not be able to access their e-mail. You've been asked to configure a conditional access policy that enforces this rule, and verify it functions as expected.

#### Task 1: Create a conditional access policy

1.  On **LON-DC1**, in the Azure portal, on the **Microsoft Intune** blade, click **Conditional
    access**.

2.  In the **Details** pane, click **+New policy**.

3.  On the **New** blade, in the **Name** text box, type **Conditional1** and
    then click **Users and groups**.

4.  On the **Users and groups** blade, select the **All users** radio button and
    then click **Done**.

5.  On the **New** blade, click **Cloud apps**, select the **Select apps** radio
    button, click **Select**, click **Office 365 Exchange Online**, click
    **Select,** and then click **Done**.

6.  On the **New** blade, click **Conditions**, click **Device platforms**, in
    the **Configure** section click **Yes**, select the **Select device
    platforms** radio button, select the **Windows** check box, and then click
    **Done** twice.

7.  On the **New** blade under access controls, click **Grant**, select the
    **Require device to be marked as compliant** check box, and then click
    **Select**.

8.  On the **New** blade, select **On** for the **Enable policy** option and
    then click **Create**.

#### Task 4: Verify that the conditional access policy is working

1.  On **LON-CL1**, sign in as **adatum/administrator** with the password **Pa55w.rd**. 
    Open a new Microsoft Edge tab, then and open <https://portal.office.com>.

2.  Sign in as **admin\@yourtenant.onmicrosoft.com**. On the Office 365 portal, 
    click the **Outlook** icon. 

3.  Verify that you receive the message **"You can't get there from here"**.

4.  Select **More details**. You should see more information about why you are
    blocked. This is because LON-CL1 is not joined to Azure AD and not managed
    by Intune, so not marked as compliant.

5.  **Close** the browser window.

6.  Switch to **LON-CL3**,

7.  Sign in as **admin\@yourtenant.onmicrosoft.com**. 

8.  Open a new Microsoft Edge tab, then and open **https://portal.office.com**.
    On the Office 365 portal, select the **Outlook** icon. 

9.  Verify that you receive the message **"Oops - You can’t get to this yet"**.
    Note that this message indicates the device is registered that a policy
    is being applied to bring the device to a compliant state. 

10. Switch to **LON-CL4**.  Repeat steps 7 & 8.

11. Ensure that you can access your mailbox. This is because LON-CL4 is a
    managed device and marked as compliant. You might get a message that device
    is being checked for compliance. If that happens, wait for a few minutes and
    then try again.

**END OF LAB**