# Practice Lab - Connecting AD DS and Azure AD

## Summary

In this lab, you will practice configuring synchronization between Active Directory Domain Services and Azure Active Directory.

### Scenario

A. Datum Corporation is currently managing provisioning users in both AD DS and Azure AD as separate processes.  This is time consuming and has led to inconsistent information. You have been tasked with addressing this issue by synchronizing the two directories.

#### Task 1: Verifying licenses and creating a sync account

1.  On **LON-CL1**, sign in as **Adatum\\Administrator**, and then open the
    Microsoft Edge browser.

2.  In the **Microsoft Edge** window, go to **https://portal.azure.com**. If
    prompted, sign in with your MOD admin credentials available in hosted lab
    environment. If the **Stay signed in?** prompt appears, click **No**.

3.  On the **Microsoft Azure** page, click **Azure Active Directory** in the
    left navigation pane. This will open the adatum Azure Active Directory page.

4.  In the middle navigation pane, click **Licenses**, and then click **All
    products**.

5.  Ensure that you see licenses for **Enterprise Mobility + Security E5, Office
    365 Enterprise E5 and Windows 10 Enterprise E3**. This confirms that your
    tenant has all necessary licenses for Microsoft 365 deployment.

6.  On the Azure portal, click **Users** in the middle pane, click **All
    users**, and then click **New user**.

7.  In the **User** dialog box, enter the following:

    1.  Name: **Sync User**

    2.  User Name: **sync\@yourtenant.onmicrosoft.com**

    3.  Click **Directory role**, select **Global administrator**, and then
        click **OK**.

8.  Click **Show Password**, note and write down the value for **Password**, and
    then click **Create**.

9.  At the upper right of the page, click your account name, and then click
    **Sign out**.

10. Close the Microsoft Edge browser, reopen it, and then browse to
    **https://portal.azure.com**.

11. On the **Microsoft Azure** page, click **Use another account** if needed,
    type **sync\@ yourtenant.onmicrosoft.com** for the user name, type the
    temporary password that you noted above, and then click **Sign in**.

12. On the **Update your password** page, in the **Current password** text box,
    type the temporary password, in the **New password** and **Confirm
    password** text boxes, type *MDA101!!* and then click **Sign in**.

13. If the **Welcome to Microsoft** Azure window appears, click **Maybe later**.
    Click your **Sync user** account in the upper right of the page, and then
    select **Sign out**. Leave browser window open.

#### Task 2: Configuring directory synchronization with Azure AD Connect

1.  On **LON-SVR1**, if necessary, sign in as **Adatum\\Administrator**, with
    the password **Pa55w.rd**. If the **Network** pane appears, click **Yes**.

2.  Open Internet Explorer, and then go to
    **http://www.microsoft.com/en-us/download/details.aspx?id=47594**.

3.  On the **Microsoft Azure Active Directory Connect** page, click
    **Download**, and then click **Run**. Note: If you experience any problems
    with launching the download, add the https://download.microsoft.com website
    to your Trusted sites.

4.  In the **Microsoft Azure Active Directory Connect Wizard**, on the **Welcome
    to Azure AD Connect** page, select the **I agree to the license terms and
    privacy notice** check box, and then click **Continue**.

5.  On the **Express Settings** page, click **Customize**.

6.  On the **Install required components** page, click **Install**.

7.  On the **User sign-in** page, ensure that **Password Hash Synchronization**
    is selected, and then click **Next**.

8.  On the **Connect to Azure AD** page, in the **USERNAME** and **PASSWORD**
    boxes, enter the SYNC account user name (it will be in the following format:
    sync\@ **yourtenant.onmicrosoft.com**) and **MDA101!!** for a password, and
    then click **Next**.

9.  On the **Connect your directories** page, ensure that Adatum.com is listed
    under **FOREST**, and then click **Add Directory**.

10. In the **AD forest account** window, select the **Use Existing Account**
    option, and in the **ENTERPRISE ADMIN USERNAME** field, type
    **ADATUM\\Administrator**, and then type **Pa55w.rd** in the **PASSWORD**
    field. Click **OK**, and then click **Next**.

11. On the **Azure AD sign-in configuration** page, ensure that in the **USER
    PRINCIPAL NAME** drop-down list, the **userPrincipalName** value is
    selected. Select **Continue without matching all UPN suffixes to verified
    domains** and then click **Next**.

12. On the **Domain and OU filtering** page, click **Sync selected domains and
    OUs**.

13. Expand **Adatum.com**, clear the checkbox on Adatum.com and ensure that the
    only following check boxes are selected: **Computers**, **IT**,
    **Managers**, **Marketing**, **Research**, and **Sales**. Clear the other
    check boxes, and then click **Next**.

14. On the **Uniquely identifying your users** page, click **Next**.

15. On the **Filter users and devices** page, click **Next**.

16. On the **Optional features** page, review available options, but do not make
    any changes. Ensure that **Password hash synchronization** is selected, and
    then click **Next**.

17. On the **Ready to configure** page, ensure that **Start the synchronization
    process when configuration completes** is selected, and then click
    **Install**.

18. When configuration is complete, click **Exit**.  
    At this time, synchronization of objects from your local Active Directory
    Domain Services (AD DS) and Azure AD begins. You should wait approximately
    3-4 minutes for this process to complete.

19. In the Internet Explorer window on LON-SVR1, browse to
    <http://www.microsoft.com/en-us/download/details.aspx?id=41950>.

20. On the **Microsoft Online Services Sign-In Assistant for IT Professionals
    RTW** page, click **Download**. On the Choose the download you want page,
    select **en\\msoidcli_64.msi** and click **Next**. Click **Run**. Disable
    pop-up blocker if needed.

21. Click **I accept the terms in the License Agreement** and click **Install**.
    When installation is done click **Finish**.

22. On LON-SVR1, run Windows PowerShell as Administrator. In the Windows
    PowerShell window, type: **Install-Module MSOnline** and press Enter. If
    prompted for NuGet provider, click **Y** and press Enter. Also accept
    installation from untrusted repository, if needed. Wait until Windows
    PowerShell Module for Azure AD is installed.

23. Leave the Windows PowerShell window open.

#### Task 3: Verify synchronization in Azure AD

1.  In the Azure portal on LON-CL1, click **Azure Active Directory**.

2.  Click **Users,** and then click **All Users**. Click **Refresh**.

3.  Verify that you see users from your local AD DS. Ensure that these users
    have the value **Windows Server AD** in the **SOURCE** column. Close Users
    window.

4.  Click **Groups**. Verify that you see groups from your local AD DS.

5.  Click the **Managers** group.

6.  On the **Managers** group page, ensure that you see users when you click
    **Members**. Also, verify that you cannot make any changes to this group, as
    it is sourced from the local Active Directory. Close the Managers window and
    close the Groups window.

7.  Leave the Azure portal open on LON-CL1 for the next task.

**END OF LAB**