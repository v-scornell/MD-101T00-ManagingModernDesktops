# Practice Lab - Configuring a WIP policy in Intune

## Summary

In this lab, you will practice creating and configuring Windows Information Protection policies in Intune.

#### Task 1: Create a WIP policy in Intune

1.  On **LON-CL3**, sign in as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Open an InPrivate window in Microsoft Edge, and then navigate to <https://portal.azure.com>. 
    Sign in using your MOD administrator credentials if prompted. Ensure that the Azure portal opens.

3.  In the navigation pane, select **Intune** and then select **Client apps**.

4.  Select **App protection policies**, and then select **+Create policy** and select **Windows 10**.

5.  In the Name text box, type **Windows 10 WIP test policy**.

6.  In the Enrollment state list, select **With enrollment**.

9.  Select **Protected apps**, then select **Add apps**.

3.  Select **Microsoft Edge** and **Notepad**. Select **OK** twice.

5.  Select **Required settings**, and then select **Allow overrides**.

7.  In the **Corporate identity** text box, type **yourtenant.onmicrosoft.com**
    if needed, and then select **OK**.

8.  Leave the console open.

#### Task 2: Define corporate boundaries

1.  Select **Configure Advanced settings**.

2.  Select **Add network boundary**.

3.  In the **Boundary type** list, select **Network domains**.

4.  In the **Name** text box, type **Domain name**.

5.  In the **Value** text box, type **Adatum.com**, and then select **OK**.

6.  Select **Add network boundary**.

7.  In the **Boundary type** list, select **Network domains**.

8.  In the **Name** text box, type **Cloud Domain name**.

9.  In the **Value** text box, type **yourtenant.onmicrosoft.com**, and then
    select **OK**.

10. Repeat steps 2−5 for the following boundary:

    -   Boundary type: **IPv4 ranges**

    -   Name: **IPv4 Range**

    -   Value: **172.16.0.1-172.16.0.190**

1.  Leave the Azure portal with the Intune console open.

#### Task 4: Create and upload a Data Recovery Agent (DRA) certificate

1.  On **LON-CL3**, right-click the **Start** menu, select **Windows
    PowerShell**.

2.  In the **Windows PowerShell** console, type the following command, and then
    press Enter:

```
    Cipher /r:ADATUMDRA

```
3.  When prompted, type **Pa55w.rd**, and then confirm the password.

4.  Switch to Microsoft Edge, and under **Data protection**, select the
    **Browse** icon.

5.  Browse to the **C:\\Users\Mod Administrator\\** folder, select the
    **ADATUMDRA.cer** file, and then select **Open**.

6.  Under **Show the enterprise data protection icon**, select **On**.

7.  Select **OK**, and then select **Create.**

#### Task 5: Assign and test the WIP policy

1.  On **LON-CL3**, in Microsoft Edge, select the policy **Windows 10 WIP test
    policy**.

2.  Select **Assignments**, then select **Select groups to include**.

3.  In the **Select** search box enter **Windows devices**.

4.  Select **Windows devices** and select **Select**, and then select **Save**.

5.  On the Start menu on LON-CL3, select **Settings**.

6.  Select **Accounts** and then select **Access work or school**.

7.  Under work or school account select **Connected to Adatum Azure AD** and
    select **Info**.

8.  Select **Sync**.

    **Note**: Wait for the settings to sync.

9.  Sign out and sign back in as **diegos\@@yourtenant.onmicrosoft.com** 
    with the default tenant password.

10. In Microsoft Edge, navigate to **https://yourtenant.sharepoint.com**.

11. Start Internet Explorer and navigate to **https://yourtenant.sharepoint.com.**

    **Note**: You should not be able to successfully navigate to the Microsoft
    SharePoint Online site in Internet Explorer because it’s not an allowed app.


**END OF LAB**