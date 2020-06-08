# Practice Lab - Configuring a WIP policy in Intune

## Summary

In this lab, you will practice creating and configuring Windows Information Protection policies in Intune.

#### Task 1: Create a WIP policy in Intune

1.  On **LON-CL3**, sign in as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Open **Microsoft Edge**, and then navigate to **https://endpoint.microsoft.com**.

3.  In the navigation pane, select **Apps**.

4.  Select **App protection policies**, and then select **Create policy** and select **Windows 10**.

5.  In the **Name** text box, type **Windows 10 WIP test policy**.

6.  In the **Enrollment state** list, select **With enrollment** and select **Next**.

7.  On the **Targeted apps** tab, under **Protected apps**, then select **Add**.

8.  Select **Microsoft Edge** and **Notepad**. Select **OK** and select **Next**.

9.  On the **Required settings** tab, next to the **Windows Information Protection mode** option, select **Allow overrides**.

10.  In the **Corporate identity** text box, type **yourtenant.onmicrosoft.com**
    if needed, and then select **Next**.

11.  On the **Advanced settings** tab, in the **Network perimeter** section, select **Add**.

12.  On the **Add network boundary** dialog, in the **Boundary type** list, select **Network domains**.

13.  In the **Name** text box, type **Domain name**.

14.  In the **Value** text box, type **Adatum.com**, and then select **OK**.

15.  In the **Network perimeter** section, again select **Add**.

16.  On the **Add network boundary** dialog, in the **Boundary type** list, select **Network domains**.

17.  In the **Name** text box, type **Cloud Domain name**.

18.  In the **Value** text box, type **yourtenant.sharepoint.com|yourtenant-my.sharepoint.com|yourtenant-files.sharepoint.com**, and then select **OK**.

19. Repeat steps 16−18 for the following boundary:

    -   Boundary type: **IPv4 ranges**

    -   Name: **IPv4 Range**

    -   Value: **172.16.0.1-172.16.0.190**

20. Select **Next**.

21.  On the **Assignments** tab, in the **Included Groups** section, select **Select groups to include**.

22.  In the **Select** search box enter **Windows devices**.

23.  Select **Windows devices** and select **Select**.

24.  Select **Next** and then select **Create**.

#### Task 2: Create and upload a Data Recovery Agent (DRA) certificate

1.  On **LON-CL3**, right-click the **Start** menu, select **Windows PowerShell**.

2.  Note the current folder location.

3.  In the **Windows PowerShell** console, type the following command, and then
    press **Enter**:

```
Cipher /r:ADATUMDRA

```
4.  When prompted, type **Pa55w.rd**, and then confirm the password.

5.  Switch to **Microsoft Edge** and select the **Windows 10 WIP test policy** you created.

6.  Select **Properties**. In the **Advanced settings** section, select **Edit**.

7.  Under **Data protection**, select the **Browse** icon.

8.  Browse to the folder location as noted in Step 2 and select the
    **ADATUMDRA.cer** file, and then select **Open**.

9.  Under **Show the enterprise data protection icon**, select **On**.

10.  Select **Review + save**, and then select **Save.**

#### Task 3: Sync and test the WIP policy

1.  On the **Start** menu on **LON-CL3**, select **Settings**.

2.  Select **Accounts** and then select **Access work or school**.

3.  Under **Access work or school**, select **Connected to Adatum Azure AD** and
    select **Info**.

4.  Select **Sync**.

    **Important**: Wait for the settings to sync.

5.  Sign out and sign back in as **diegos\@yourtenant.onmicrosoft.com** 
    with the default tenant password.

6.  In **Microsoft Edge**, navigate to **https://yourtenant.sharepoint.com**.

7.  Start **Internet Explorer** and navigate to **https://yourtenant.sharepoint.com**.

    _Note: You should not be able to successfully navigate to the Microsoft
    SharePoint Online site in Internet Explorer because it’s not an allowed app._

    _If you are still able to access the site in Internet Explorer, sign out and sign back in, and repeat step 7._

8.  Right-click the **Windows task bar** and select **Task Manager**.  Select **More details** if needed.

9.  Select the **Details** tab. Right-click on any tab and select **Select columns**. 

10.  Scroll to and check the box next to **Enterprise context** and select **OK**. Note that the Enterprise context for Microsoft Edge shows the domain, while Internet Explorer's context shows as Personal.  


**END OF LAB**