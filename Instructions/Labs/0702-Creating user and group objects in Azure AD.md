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

1.  On **LON-DC1**, sign in as **Adatum\\Administrator**, and login to the
    Azure portal as **admin\@yourtenant.onmicrosoft.com** if you are not already there.
    
2.  Navigate to Azure Active Directory.  On the **Azure AD - Overview** page, select 
    **Users** and then select **New user**.

3.  In the **New User** dialog box, enter the following:

    -  Name: **Edmund Reeve**

    -  User Name: **ereeve\@yourtenant.onmicrosoft.com**

4.  Select **Let me create the password.**

5.  Enter **Pa55w.rd12345** the select **Create**.

6.  Scroll left to the **Azure AD** blade. Select **Custom domain names** and select 
    the **yourtenant.onmicrosoft.com** listing.

7.  On the **In-use** row, select the **### resources referencing this domain name**. 

8.  On the **Domain name resources** blade, type **Alex** in the search box and 
    press **Enter**. Select **Alex Wilber**.

9.  Select **Assigned roles** and select +Add assignment. Select **Global administrator**.

10. Scroll left to the **Azure AD - Custom domain names** blade and select **Users**. 
    Select **Edmund Reeve**.

11. In the **Edmund Reeve - Profile** blade, in the right pane under the**Settings** 
    section, select **Edit**, select your country/region in the **Usage location** drop-down box. 
    
    _Note: If your country/region is not listed, select **United States**.
    
12. Select **Save**. Close the **Edmund Reeve – Profile** page.

13. Close the **Users – All users** window, and then select **Licenses**.

14. Select **All products**, and then select **Enterprise Mobility + Security
    E5** and **Office 365 Enterprise E5**. Select **Assign**.

15. Select **Users and groups**, select **Edmund Reeve** from the list, and
    then select **Select**.

16. Select **Assign**.

17. At the upper right of the page, select your account name, and then select
    **Sign in with a different account**.

18. On the **Microsoft Azure** page, select **Use another account if needed**,
    type **ereeve\@ yourtenant.onmicrosoft.com** for the user name, type the
    temporary password that you noted above, and then select **Sign in**.

19. On the **Update your password** page, in the **Current password** text box,
    type **Pa55w.rd12345**, in the **New password** and **Confirm
    password** text boxes, type **MDA101!!**, and then select **Sign in**. If the
    **Stay signed in** prompt appears, select **No**.

20. Select Edmund’s user account in the upper right of the page, and then select
    **Sign in with a different account**

21. On the **Microsoft Azure** page, use the MOD Administrator account to sign
    in.

22. In the Microsoft Azure portal, select the **Azure Active Directory**
    directory item, and then select **Groups.**

23. On the **Groups – All groups** page, select **All groups**, and then select
    **New Group**.

24. In the **Group** window, select **Security** for Group type, type
    **AdatumGroup1** in the **Group Name** text box, select **Assigned** for
    **Membership type**, and then select **Members**.

25. In the **Members** window, select **Edmund Reeve**, and then select
    **Select**.

26. Select **Create**. Close the **Group** page.

27. Minimize the browser window on **LON-DC1**.

#### Task 2: Creating users by using PowerShell

1.  On the **LON-SVR1**, restore the Windows PowerShell window.

2.  In the Windows PowerShell window, type the following command, and then press
    Enter:

```
Connect-MsolService

```
3.  In the **Enter Credentials** dialog box, sign in as
    **admin\@yourtenant.onmicrosoft.com** with the tenant password, and then
    select **OK**.

4.  In the Windows PowerShell window, type the following code to create a new user, and then press
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

7.  In the Windows PowerShell window, type the following code to create a new group, and then press
    Enter:

```
New-MsolGroup -DisplayName “Azure team” -Description “Adatum Azure team users”

```
8.  In the Windows PowerShell window, type the following command, and then press
    Enter:

```
Get-MsolGroup

```
9.  Verify that you get the list of groups in your tenant, including the Azure team group you just created.

10.  In the Windows PowerShell window, type the following code to define a variable as the Azure team group, and then press
    Enter:

```
$group = Get-MsolGroup | Where-Object {$_.DisplayName -eq "Azure team"}

```
11.  In the Windows PowerShell window, type the following code to define another variable as the user, and then press
    Enter:

```
$user = Get-MsolUser | Where-Object {$_.DisplayName -eq “Cody Godinez”}

```
12.  In the Windows PowerShell window, type the following code to add Cody to the Azure team using set variables, and then press
    Enter:

```
Add-MsolGroupMember -GroupObjectId $group.ObjectId -GroupMemberType "User"
-GroupMemberObjectId $user.ObjectId

```
13.  In the Windows PowerShell window, type the following code, and then press
    Enter:

```
Get-MsolGroupMember -GroupObjectId $group.ObjectId

```
14.  Verify that you get **Cody Godinez** as a result. Minimize the Windows PowerShell window.

**END OF LAB**