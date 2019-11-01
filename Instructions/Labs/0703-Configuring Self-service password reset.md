# Practice Lab - Configuring Self-service password reset (SSPR) for user accounts in Azure AD

## Summary

In this lab, you will practice configuring and testing SSPR and password writeback to AD DS.

### Scenario

The Help Desk has indicated that a large number of support tickets are related to password resets. You have been asked to setup a way for users to reset their password on their own. The process should reset both their Azure AD and AD DS password. 

#### Task 1: Configure password writeback

1.  On **LON-SVR1**, on the desktop, double-click **Azure AD Connect**.

2.  On the **Welcome to Azure AD Connect** page, click **Configure**.

3.  On the **Additional tasks** page, click **Customize synchronization
    options**, and then click **Next**.

4.  On the **Connect to Azure AD** page, if needed type
    **SYNC\@yourtenant.onmicrosoft.com** in the **USERNAME** text box, type
    **MDA101!!** in the **PASSWORD** text box, and then click **Next**.

5.  On the **Connect to your directories** page, click **Next**.

6.  On the **Domain and OU filtering** page, click **Next**.

7.  On the **Optional features** page, select **Password writeback**, and then
    click **Next**.

8.  On the **Ready to configure** page, click **Configure**.

9.  On the **Configuration complete** page, click **Exit**.

10. On **LON-SVR1**, open Internet Explorer and go to
    **https://portal.azure.com**.

11. Sign in with the MOD administrator account.

12. In the Azure portal, click **Azure Active Directory**.

13. In the left navigation pane, click **Password reset**.

14. In the Password reset – Properties window, click **All** to enable
    self-service password reset to all users. Click **Save**.

15. On the **Password reset – Properties** page, click **Authentication
    methods**.

16. For the methods available to users, ensure that **Mobile Phone** and
    **Email** are selected, and then select **Security Questions**.

17. For the **number of questions required to register**, select **3**.

18. For the **number of questions required to reset**, select **3**.

19. In the **Select security questions** section, click **No security questions
    configured**, then click **Predefined**, select three questions of your
    choice, and then click **OK** twice.

20. Click **Save**.

21. Click on **Registration.** Click **No** for **Require users to register when
    signing in**, and the click **Save**.

22. In the middle pane, click **On-premises integration**.

23. Verify that your on-premises writeback client is running and select **Yes**
    for the **Write back passwords to your on-premises directory** option. Click
    **Save**.

24. Close the Internet Explorer browser window, and then reopen it.

#### Task 2: Configure self-service password reset

1.  In Internet Explorer, browse to **https://myapps.microsoft.com**. If you are
    already signed in, sign out.

2.  Click **Use another account** if needed.

3.  **JoniS\@yourtenant.onmicrosoft.com**, and then, when prompted, sign in as
    **JoniS\@ yourtenant.onmicrosoft.com** with the password **Pa55w.rd**.

4.  On the **Microsoft** page, click on the **JoniS** account in the top right
    corner, and then click **Profile**.

5.  Click **Set up self service password reset**.

6.  On the **don’t lose access to your account** page, click **Set it up now**
    for the **Authentication Phone** option.

7.  Choose your country or region, type your mobile phone number, and then click
    **text me**.

8.  Type the number that you receive in a text message in the text box below,
    and then click **verify**.

9.  Click **Set it up now** for the **Authentication Email** option. Type your
    email address that you easily access. Click **email me**.

10. Sign in to your email account, read the code, type it in the verification
    field, and then click **Verify**. Note: If you don’t find a message with a
    code in your inbox, check the junk folder.

11. On the **don’t lose access to your account!** page, click **Finish**.

12. On the **Microsoft Azure** page, click on the **JoniS** account, and then
    click **Profile**.

13. In the Azure portal, click **Change password**.

14. On the **change password** page, in the **Old password** text box, type
    **Pa55w.rd**, in the **Create new password** and the **Confirm new
    password** text boxes, type **MDA101!!** and then click **submit**.

15. Wait until the Microsoft Azure profile portal appears, and then close the
    Internet Explorer browser window.

#### Task 3: Verify password writeback

1.  Ensure that you are signed in to LON-SVR1.

2.  Restore the Windows PowerShell window from the desktop.

3.  At the Windows PowerShell command prompt, type the following commands, and
    then press Enter after each command:

```
Import-Module ADSync

Start-ADSyncSyncCycle –PolicyType Delta

```
1.  Wait for approximately 3-4 minutes.

2.  Minimize Windows PowerShell, and then switch to LON-CL1. Sign out.

3.  Try to sign in to LON-CL1 as **Adatum\\JoniS** with the password
    **Pa55w.rd**.

4.  Ensure that you get the message that the user name or password is incorrect.

5.  Try to sign in to LON-CL1 as **Adatum\\JoniS** with the password
    **MDA101!!**. You should be able to sign in. This confirms that the password
    you changed in the Azure portal is written back to your local Active
    Directory Domain Services (AD DS).

** END OF LAB ****END OF LAB**