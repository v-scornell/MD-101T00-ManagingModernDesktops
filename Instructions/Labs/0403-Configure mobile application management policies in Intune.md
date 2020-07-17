# Practice Lab - Configure mobile application management (MAM) policies in Intune

## Summary

In this lab, you will practice configuring and applying App protection policies.

### Scenario

All the developers in A. Datum have iPhones running the latest version of iOS. The security department in A. Datum is concerned with data leaks and wants to prevent data from the corporate e-mail to be copied out to other programs. You must provide a solution that addresses the concerns from the security department. The head of the developer department, Brenda Mueller, has volunteered to help you test and evaluate the solution and provide feedback.

#### Task 1: Create app protection policy in Intune

1.  On **LON-CL3** sign in as **admin\@yourtenant.onmicrosoft.com** with the 
    default tenant password.

2.   Open **Microsoft Edge**, navigate to **https://endpoint.microsoft.com** and select **Apps**.

3.  On the **Apps | Overview** blade, select **App protection policies** under
    **Policy**. In the details pane, select **Create Policy** and then
    select **iOS/iPadOS**.

4.  On the **Basics** tab, configure the following options and select **Next**:

    -   Name: **Outlook – Developers**

    -   Description: **MAM policy that prevent cut and paste from Outlook**

5.  On the Apps tab, select **Select public apps**

6.  On the **Select apps to target** blade, in the text box, type **Outlook**. Select
    **Microsoft Outlook** and then select **Select**, and then select **Next**.

7.  On the **Data protection** tab, configure the following options and select
    **Next**:

    -   Backup Org data to ITunes and iCloud backups: **Allow**

    -   Send Org data to other apps: **None**

    -   Receive data from other apps: **Policy managed apps**

    -   Restrict cut, copy, and paste with other apps: **Any app**

    -   Leave all other settings at default

8.  On the **Access requirements** tab, configure the following options and
    select **Next**:

    -   PIN for access: **Not required**

9.  On the **Conditional launch** tab, review the settings. Select **Next**.

     _Note: Here you can set the sign-in security requirements for your access
     protection policy. You can select a setting and enter the value that users
     must meet to sign in to your company app. Make note of the various settings
     but do not change anything._

10. On the Assignments tab, select **Select groups to include**. 

11. Select the **A. Datum developer devices** group, then choose **Select**. 

12. Select **Next**.  On the **Review + create** tab, review the settings and select **Create**. 

13. On the **Apps | App protection policies** blade, in the details pane,
    verify that **Outlook - Developers** is listed.

**END OF LAB**