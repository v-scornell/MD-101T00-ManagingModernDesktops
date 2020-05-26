# Practice Lab - Configure Hybrid Azure AD join

## Summary

In this lab, you will practice configuring hybrid Azure Active Directory join for your devices.

### Scenario

A. Some Windows devices from Datum Corporation are currently joined to the local Active Directory. To enable those devices to seamlessly access cloud services you plan to enable hybrid Azure AD join.

#### Task 1: Configure hybrid Azure AD join in Azure Active Directory Connect

1.  On **LON-CL1**, sign in as **Adatum\\Administrator** with the password of **Pa55w.rd**. 

2.  Switch to **LON-SRV1** and sign in as **Adatum\\Administrator** with the password of **Pa55w.rd**,
    and on the Desktop double-click **Azure AD Connect**.

3.  In the **Microsoft Azure Active Director Connect** window select **Configure**.

4.  On the **Additional tasks** page, select **Configure device options** and select **Next**.

5.  On the **Overview** page select **Next*.

6.  On the **Connect to Azure AD** page enter **Pa55w.rd12345** as password into the **PASSWORD* box, then select **Next**.

7.  On the **Device options** page select **Configure Hybrid Azure AD join**, and then select **Next*.

8.  On the **Device operating systems** page select **Windows 10 or later domain-joined devices**, and then select **Next*.

9.  On the **SCP configuration** page select the **Forest Adatum.com**. Select **Azure Active Directory** from the **Authentication Service** dropdown
    and select **Add**. In the **Enterprise Admin Credentials** window enter **Adatum\\Administrator** as **User name** and **Pa55w.rd** as **Password*.
    Select **OK** and select **Next**.

10. In the **Ready to configure** window select **Configure** to run the configuration.

11. When configuration is complete, select **Exit**.

#### Task 2: verify the registration

1.  Switch to **LON-CL1**.

2.  On the taskbar, right-click **Start**, select **Shut down or sign out** and then select **Restart**.
    _Note: The reboot will trigger the hybrid Azure AD join on LON-CL1._
   
3.  When **LON-CL1** has restarted sign in as **Adatum\\Administrator**. 
    
4.  On the taskbar, right-click **Start** and select **Windows Powershell (Admin)**

5.  In the **Windows PowerShell** window, type the following command, and then press
    **Enter**:

```
dsregcmd /status

```

6.  In the output under **Device State**, verify that **AzureAdJoined : YES** and **DomainJoined : YES** are displayed.
    _Note: If the device is not yet joined to AzureAD wait for the Azure AD Connect sync to complete and try to reboot LON-CL1 again._

7.  On the taskbar select **Microsoft Edge**, type **https://aad.portal.azure.com** in the address bar, and then press **Enter**.

8.  Sign in as user Admin@yourtenant.onmicrosoft.com, and use the tenant Admin password. If the **Stay signed in?** prompt appears, select **No**. 
    If the Welcome to Microsoft Azure window appears, select Maybe later.

9.  Select  **Azure Active Directory**, then select **Devices**. Select **Refresh**.

10. Verify that **LON-CL1** has **Hybrid Azure AD joined** as value for the row **Join Type** and that **Registered** contains a time stamp.

11. CLose all windows and sign out.

**END OF LAB**
