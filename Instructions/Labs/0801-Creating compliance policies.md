# Practice Lab - Creating compliance and conditional access policies

## Summary

In this lab, you will practice creating a compliance policy and assign it to a device. You'll also create conditional access rules based on the compliance status of a device. 

## Exercise 1: Configuring compliance policies 

### Scenario

A. Datum would like to ensure that enrolled Windows 10 devices meet a minimum configuration specification.  The following are required:

* Minimum OS version: 10.0.16299.15
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

1.  In **LON-CL1**, in the Azure portal, click **All services**, type
    **intune,** and then click **Intune**.

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
    to include**, click **Enrolled Devices**, click **Select,** and then click
    **Save**.

15. In **LON-CL1**, in the Azure portal, scroll the page to the left and then on
    the **Microsoft Intune** blade, click **Device enrollment**.

16. Review the available options on the **Device enrollment** blade.

17. On the **Device enrollment** blade, click **Enrollment restrictions**.

18. On the details pane, in the **Device Type Restrictions** section, click
    **Default,** click **Properties,** and then click **Select platforms**.

19. On the **Select platforms** blade, in the **iOS** and **macOS** rows click
    **Block**, click **OK,** and then click **Save**.

20. On the left pane, in the **Device Limit Restrictions** section, click
    **Default** and then click **Properties**.

21. In the **Device Limit** dropdown list, select **3** and then click **Save**.

#### Task 2: Create a device configuration profile

1.  In **LON-CL1**, in the Azure portal, scroll the page to the left and then on
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

5.  Select **Enrolled Devices**, and then select **Select**.

6.  Select **Save**.


## Exercise 2: Creating a conditional access policy

### Scenario 

When devices are non-compliant, they should not be able to access their e-mail. You've been asked to configure a conditional access policy that enforces this rule, and verify it functions as expected.

#### Task 1: Enroll a device to Azure AD and Intune

1.  In **LON-CL2**, sign in as Admin with password Pa55w.rd and then on the
    taskbar, click **Start**, type **connect to work** and then click **Acess
    work or school**.

2.  In the **Settings** app, in the **Access work or school** section, click
    **+Connect**.

3.  In the **Microsoft account** window, on the **Set up a work or school
    account** page, click **Join this device to Azure Active Directory**.

4.  On the **Let’s get you signed in** page, in the **Work or school account**
    text box, type **Admin\@yourtenant.onmicrosoft.com** and then click
    **Next**.

5.  On the Enter password page, type **Pa55w.rd** in the text box and then click
    **Sign in**.

6.  Wait a few seconds and then on the **Make sure this is your organization**
    dialog, click **Join**.

7.  On the **You’re all set!** page, click **Done**.

8.  In the **Settings** app, in the **Access work or school** section, verify
    that the device is connected to Azure AD and then close the **Settings**
    app.

9.  Restart LON-CL2 and then sign in as Admin\@**yourtenant.onmicrosoft.com**.
    Create a PIN, if required.

#### Task 2: Verify that the device is enrolled to Azure AD and Intune

1.  In **LON-CL1**, in the Azure portal, scroll the page to the left and then on
    the **Microsoft Intune** blade, click **Devices**.

2.  On the **Devices** blade, click **Azure AD devices** and verify that in the
    Details pane the same device is listed. **Note:** This view lists devices
    that are joined to Azure AD. Remember that you configured integration
    between Azure AD and Intune, and because of that, any device that is joined
    to Azure AD is automatically enrolled to Intune.

3.  On **LON-CL1**, in the Azure portal, select **Microsoft Intune**.

4.  Select **Devices**, and then select **All devices**.

5.  Select **LON-CL2**, and then select **Sync**.

6.  When prompted, click **Yes**. Wait for 3-4 minutes.

7.  Switch to the LON-CL2 machine.

8.  Right-click **Start**, and then select **Network connections**.

9.  Select **VPN**, and then verify that **Adatum VPN** appears in the **VPN**
    list. Note: If Adatum VPN does not appear, repeat steps 7 and 8 and then
    check again. You can also proceed to the next task, and then come back later
    to check this.

#### Task 3: Create a conditional access policy

1.  In the Azure portal, on the **Microsoft Intune** blade, click **Conditional
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

1.  On **LON-CL1**, sign in as **Adatum\\Administrator**, open a new Microsoft
    Edge tab, then and open <https://portal.office.com>.

2.  Sign in with the following account:

    -   Username: **AllanD\@yourtenant.onmicrosoft.com**

    -   Password: **Pa55w.rd**

1.  On the Office 365 portal, click the **Outlook** icon.

2.  Verify that you receive the message **"You can’t get there from here"**.

3.  Select **More details**. You should see more information about why you are
    blocked. This is because LON-CL1 is not joined to Azure AD and not managed
    by Intune, so not marked as compliant.

4.  **Close** the browser window.

5.  Switch to **LON-CL3**.

6.  Repeat steps 1 to 3.

7.  Ensure that you can access your mailbox. This is because LON-CL3 is a
    managed device and marked as compliant. You might get a message that device
    is being checked for compliance. If that happens, wait for a few minutes and
    then try again.




