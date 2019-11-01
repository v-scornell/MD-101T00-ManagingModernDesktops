# Practice Lab - Configure mobile application management (MAM) policies in Intune

## Summary

In this lab, you will practice configuring and applying App protection policies.

### Scenario

All the developers in A. Datum have iPhones running the latest version of iOS. The security department in A. Datum is concerned with data leaks and wants to prevent data from the corporate e-mail to be copied out to other programs. You must provide a solution that addresses the concerns from the security department. The head of the developer department, Brenda Mueller, has volunteered to help you test and evaluate the solution and provide feedback.

#### Task 1: Create app protection policy in Intune

1.  On **LON-CL3**, in the Azure portal, click **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, click **Client apps**.

2.  On the **Client apps** blade, click **App protection policies** under
    **Manage**. In the details pane, click **+ Create Policy**.

3.  On the **Add a policy** blade, configure the following options:

-   Name: **Outlook – Developers**

-   Description: **MAM policy that prevent cut and paste from Outlook**

-   Platform: **iOS**

4.  Click **Apps - Select required settings**

5.  On the **Apps** blade, scroll down and select **Outlook**. Then click
    **Select**.

6.  Back on the **Create a policy** blade, click **Settings - Default settings
    configured.** In the **Settings** blade, click **Data protection – Default
    settings configured.**

7.  On the **Data protection** blade, configure the following options and click
    **OK**:

-   Backup Org data to ITunes and iCloud backups: **Yes**

-   Send Org data to other apps: **None**

-   Receive data from other apps: **Policy managed apps**

-   Restrict cut, copy, and paste with other apps: **Any app**

-   Leave all other settings at default

8.  Back on the **Settings** blade, click **Access requirements – Default
    settings configured**.

9.  On the **Access requirements** blade, configure the following options and
    click **OK**:

-   PIN for access: **Not required**

10.  Back on the **Settings** blade, click **Conditional launch - Default
    settings configured**.

     Here you can set the sign-in security requirements for your access
     protection policy. You can select a setting and enter the value that users
     must meet to sign in to your company app. Make note of the various settings
     but do not change anything. Click **OK**.

11.  Back on the **Settings** blade, click **OK** and then click **Create**.

12.  On the **Client apps - App protection policies** blade, in the details pane,
    verify that **Outlook - Developers** is listed.

#### Task 2: Deploy MAM policy to developer users

1.  On **LON-CL3**, in the Azure portal, click **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, click **Client apps**.

2.  On the **Client apps** blade, click **App protection policies** under
    **Manage**.

3.  On the **Client apps - App protection policies** blade, in the details pane,
    click **Outlook - developers**.

4.  On the **Intune App Protection** blade, click **Assignments**.

5.  On the **Intune App Protection - Assignments** blade, click **Select groups
    to include**.

6.  On the **Select groups to include** blade, click **A. Datum Developers** and
    then click **Select** and then click **Save**. Close the blade. The app
    protection policy is now assigned to the **A. Datum Developers** Azure AD
    group.
