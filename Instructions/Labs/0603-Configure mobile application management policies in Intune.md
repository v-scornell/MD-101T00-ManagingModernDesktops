# Practice Lab - Configure mobile application management (MAM) policies in Intune

## Summary

In this lab, you will practice configuring and applying App protection policies.

### Scenario

All the developers in A. Datum have iPhones running the latest version of iOS. The security department in A. Datum is concerned with data leaks and wants to prevent data from the corporate e-mail to be copied out to other programs. You must provide a solution that addresses the concerns from the security department. The head of the developer department, Brenda Mueller, has volunteered to help you test and evaluate the solution and provide feedback.

#### Task 1: Create app protection policy in Intune

1.  On **LON-CL3**, in the Azure portal, select **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, select **Client apps**.

2.  On the **Client apps** blade, select **App protection policies** under
    **Manage**. In the details pane, select **+ Create Policy** and then
    **select iOS/iPadOS**.

3.  On the **Basics** tab, configure the following options and select **Next**:

-   Name: **Outlook – Developers**

-   Description: **MAM policy that prevent cut and paste from Outlook**

4.  On the Apps tab, select **+Select public apps**

5.  On the **Apps** tab, in the text box, type **Outlook**. Select
    **Microsoft Outlook** and then select **Select**.

6.  Select **Next**. On the **Data protection** tab, configure the following options and select
    **OK**:

-   Backup Org data to ITunes and iCloud backups: **Allow**

-   Send Org data to other apps: **None**

-   Receive data from other apps: **Policy managed apps**

-   Restrict cut, copy, and paste with other apps: **Any app**

-   Leave all other settings at default

7.  Select **Next**. On the **Access requirements** tab, configure the following options and
    select **OK**:

-   PIN for access: **Not required**

8. Select **Next**. On the **Conditional launch** tab, review the settings. 

     Here you can set the sign-in security requirements for your access
     protection policy. You can select a setting and enter the value that users
     must meet to sign in to your company app. Make note of the various settings
     but do not change anything. Select **OK**.

9.  Select **Next**. On the Assignments tab, select **+Select groups to include**. 

10. Select the **A. Datum developer devices** group, then choose **Select**. 

11. Select **Next**.  On the **Review + create** tab, review the settings and select **Create**. 

12. On the **Client apps - App protection policies** blade, in the details pane,
    verify that **Outlook - Developers** is listed.

**END OF LAB**