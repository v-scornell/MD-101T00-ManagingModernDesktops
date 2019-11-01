# Practice Lab - Creating user and group objects in Azure AD

## Summary

In this lab, you will practice creating users in Azure AD in the browser UI and in PowerShell.

### Scenario

You've been asked to add user accounts from a list of new employees.  They should the following users in the Azure portal:

| **Name**           | **User Name**                           | **Role**                 | **License**                 | **Password**      | **Security Group** |
|--------------------|-----------------------------------------|--------------------------|-----------------------------|-------------------|--------------------|
| **Edmund Reeve**   | **ereeve\@yourtenant.onmicrosoft.com**  |                          | **EMS E5 and O365 Ent E5**  | **Pa55w.rd12345** | **AdatumGroup1**   |
| **Alex Wilber**    | **alexw\@yourtenant.onmicrosoft.com**   | **Global Administrator** |                             | **(temporary)**   |                    |
| **Miranda Snider** | **msnider\@yourtenant.onmicrosoft.com** |                          | **EMS E5 and O365 Ent E5**  | **(temporary)**   |                    |

Once created, users with temporary passwords should each sign in to the Azure portal and reset their passwords. The AdatumGroup1 group will also need to be created.

You've also been told several more employees will be hired over the next few days.  You've decided that scripting would be a far more efficient method of adding users. You've decided to create the follow user and group using Powershell to test your script commands, including commands to check the results. 

| **Name**           | **User Name**                           | **Role**                 | **License**                 | **Password**      | **Security Group** |
|--------------------|-----------------------------------------|--------------------------|-----------------------------|-------------------|--------------------|
| **Cody Godinez**   | **cgodinez@yourtenant.onmicrosoft.com**  |                          |   | **Pa55w.rd12345** | **Adatum Azure team users**   |

Note: For location use either your local region or United States. 

#### Task 1: Creating users by using the Azure portal

1.  On the **adatum** page, click **Users** in the middle pane, click **All
    users**, and then click **New user**.

2.  In the **User** dialog box, enter the following:

    -  Name: **Edmund Reeve**

    -  User Name: **ereeve\@yourtenant.onmicrosoft.com**

3.  Click **Let me create the password.**

4.  Enter **Pa55w.rd12345** the select create.

5.  On the **Contoso –overview located in the Azure Active directory select –
    Custom domain names** page, click **the domain under name – then select the
    highlighted In use text referencing the number of resources that reference
    the domain.**,

6.  In the **User** dialog box, enter the following:

    -  Name: **Alex Wilber**

    -  User Name: **alexw\@yourtenant.onmicrosoft.com**

    -  Click **Assigned role**, select **Global administrator**, and then click
        **Add**.

7.  **in the Profiles section select reset password**, note and write down the
    value for **Password**, and then click **Create**.

8.  In the **Users– All users** window, click **Edmund Reeve**.

9.  In the **Edmund Reeve** window, click **Profile**, and then in the right
    pane, in the **Settings** section, click **Edit**, select your
    country/region in the **Usage location** drop-down box. If your
    country/region is not listed, select **United States**, and then click
    **Save**. Close the **Edmund Reeve – Profile** page.

10. Repeat steps 7 and 8 for the user account **Miranda Snider**.

11. Close the **Users – All users** window, and then click **Licenses** in the
    middle pane.

12. Click **All products**, and then select **Enterprise Mobility + Security
    E5** and **Office 365 Enterprise E5**. Click **Assign**.

13. Click **Users and groups**, select Edmund and Miranda from the list, and
    then click **Select**.

14. Click **Assign**.

15. At the upper right of the page, click your account name, and then click
    **Sign out**.

16. Close the Microsoft Edge browser, reopen it, and then browse to
    **https://portal.azure.com**.

17. On the **Microsoft Azure** page, click **Use another account if needed**,
    type **ereeve\@ yourtenant.onmicrosoft.com** for the user name, type the
    temporary password that you noted above, and then click **Sign in**.

18. On the **Update your password** page, in the **Current password** text box,
    type the temporary password, in the **New password** and **Confirm
    password** text boxes, type **MDA101!!**, and then click **Sign in**. If the
    **Stay signed in** prompt appears, click **No**.

19. Click Edmund’s user account in the upper right of the page, and then select
    **Sign out**. Leave Microsoft Edge open. Click **Use another account**.

20. On the **Microsoft Azure** page, click **Use another account if needed**,
    type **msnider\@ yourtenant.onmicrosoft.com** for the user name, type the
    temporary password that you noted above, and then click **Sign in**.

21. On the **Update your password** page, in the **Current password** text box,
    type the temporary password, in the **New password** and **Confirm
    password** text boxes, type **MDA101!!** and then click **Sign in**. If the
    **Stay signed in** prompt appears, click **No**.

22. Click Miranda’s user account in the upper right of the page, and then select
    **Sign out**. Leave Microsoft Edge open. Click **Use another account**.

23. On the **Microsoft Azure** page, use the MOD Administrator account to sign
    in.

24. In the Microsoft Azure portal, click the **Azure Active Directory**
    directory item, and then click **Groups.**

25. On the **Groups – All groups** page, click **All groups**, and then click
    **New Group**.

26. In the **Group** window, select **Security** for Group type, type
    **AdatumGroup1** in the **Group Name** text box, select **Assigned** for
    **Membership type**, and then click **Members**.

27. In the **Members** window, select **Edmund Reeve**, and then click
    **Select**.

28. Click **Create**. Close the **Group** page.

29. Minimize the browser window on **LON-CL1**.

#### Task 2: Creating users by using PowerShell

1.  On the **LON-SVR1**, restore the Windows PowerShell window.

2.  In the Windows PowerShell window, type the following command, and then press
    Enter:

```
Connect-MsolService

```
3.  In the **Enter Credentials** dialog box, sign in as
    **admin\@yourtenant.onmicrosoft.com** with the tenant password*,* and then
    click **OK**.

4.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
New-MsolUser –UserPrincipalName cgodinez@yourtenant.onmicrosoft.com
-DisplayName “Cody Godinez” -FirstName “Cody” -LastName “Godinez” -Password
‘Pa55w.rd12345’ -ForceChangePassword $false -UsageLocation “US”

```
5.  In the Windows PowerShell window, type the following command, and then press
    Enter:

```
Get-MsolUser

```
6.  Verify that you get the list of users in your tenant.

7.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
New-MsolGroup -DisplayName “Azure team” -Description “Adatum Azure team users”

```
8.  In the Windows PowerShell window, type the following command, and then press
    Enter:

```
Get-MsolGroup

```
9.  Verify that you get the list of groups in your tenant.

10.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
$group = Get-MsolGroup | Where-Object {$_.DisplayName -eq "Azure team"}

```
11.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
$user = Get-MsolUser | Where-Object {$_.DisplayName -eq “Cody Godinez”}

```
12.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
Add-MsolGroupMember -GroupObjectId $group.ObjectId -GroupMemberType "User"
-GroupMemberObjectId $user.ObjectId

```
13.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
Get-MsolGroupMember -GroupObjectId \$group.ObjectId

```
14.  Verify that you get **Cody Godinez** as a result. Minimize the Windows PowerShell window.

** END OF LAB **