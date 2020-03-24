# Practice Lab - Creating device inventory reports

## Summary

In this lab, you will practice viewing inventory within Intune, Excel, and using PowerBI.

## Exercise 1 

### Scenario

You've been asked to review the inventory for LON-CL4.  Use Intune to review the devices hardware and app inventory.

### Task 1: Examining device inventory

1.  Switch to **LON-CL3** and sign in as **Admin** with the password **Pa55w.rd**.

2.  In Microsoft Edge, type **https://portal.azure.com** in the address bar, and
    then press **Enter**.

3.  Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant
    Admin password. Under Azure Services, select **Intune**. 

4.  Select **Devices**, then select **All devices** and in the details pane, select the
    **MARKETING-###** entry. On the **Overview** blade, examine the various
    information displayed about the device.

    _Note: This device is the LON-CL4 VM._

5.  Select **Properties** and note that you can change the **Management name**,
    **Device category** and **Device ownership**.

6.  In the Management name field, replace the existing text with **LON-CL4** and select **Save**.

7.  Under **Monitor**, select **Hardware** and examine the hardware from
    **MARKETING-###**. You need to scroll down to see it all.

8.  Under **Monitor**, select **Discovered apps** and examine the app inventory
    from MARKETING-###. You need scroll down to see it all.


### Exercise 2 Scenario

Management is requesting a report of all devices. They do not have access to the Intune dashboards, and have requested the information be sent in an Excel file.

### Task 1: Export Intune Data

1.  On **LON-CL3**, in the Azure portal, in the navigation pane, select **Home** in the
    breadcrumb navigation, then select **Intune**.

2.  On the **Intune** blade, select **Devices** and then select **All devices**.

3.  On the All devices blade, in the details pane, select **Export**.

4.  When prompted, select **Yes**, and wait for the export to be prepared.

5.  When prompted by **What do you want to do with…**, select up-arrow next to
    **Save** and select **Save as**.

6.  In the **Save As** dialog box, select **Save** and note that the CSV file is
    saved in the **Downloads** folder.

7.  Close the **finished downloading** notification.

### Task 2: Import Intune data into Microsoft Excel

1.  On **LON-CL3**, select **Start** and then select **Excel**.

2.  In Excel, select **Browse**. Select the **Downloads** folder and in the **All
    Excel Files** drop-down box, select **All Files**.

3.  In the **Open** dialog box, select the **Intune_Devices_\<Date-Time\>**
    file. Then select **Open**.

4.  In the **Text Import Wizard – Step 1 of 3** dialog box, select **Delimited**
    and then select **Next**.

5.  In the **Text Import Wizard – Step 2 of 3** dialog box, remove the check
    mark next to **Tab** and select the check box next to **Comma**. Then select
    **Next**.

6.  In the **Text Import Wizard – Step 3 of 3** dialog box, select **Finish**.

7.  Review the report content. When finished, close Excel and select **No** when asked about saving the report.


### Exercise 3 Scenario

Your organization uses Power BI for reporting.  You've been asked to setup Power BI for Brenda Mueller on LON-CL3 and connect to the Intune Data Warehouse using an OData feed and generate a PDF report.

### Task 1: Create an Intune report using Power BI and Intune Data Warehouse

1.  On **LON-CL3**, on the Task bar, select the **File Explorer** icon and browse
    to **C:\\Software**.

2.  In **File Explorer**, double-click **PBIDesktop_x64.msi**.

3.  On the **Welcome to the Microsoft Power BI Desktop (x64) Setup Wizard**
    page, select **Next**.

4.  On the **Microsoft Software License Terms** page, select **I accept the terms
    in the License Agreement** and select **Next**.

5.  On the **Destination Folder** page, select **Next**.

6.  On the **Ready to install Microsoft Power BI Desktop (x64)** page, select
    **Install**. When prompted, select **Yes**. Wait for the installation to
    complete.

7.  On the **Completed the Microsoft Power BI Desktop (x64) Setup Wizard** page,
    select **Launch Microsoft Power BI Desktop** to remove the check mark. Then
    select **Finish**.

8.  On **LON-CL3**, in the Azure portal, in the navigation pane, select
    **Microsoft Intune** in the breadcrumb navigation.

9.  Scroll to the right and under **Other tasks**, select the **Set up Intune
    Data Warehouse** link. Leave this page open.

10. Select **Start** and under **Recently added**, select **Power BI Desktop**.

11. After PowerBI loads, close the **Sign in to collaborate and share content** page by selecting the
    **X** in the upper right corner.

13.  With the **Home** tab selected in the ribbon, select **Get Data**. In the dialog, select **Other** on the left side, and then select **OData feed** and then select **Connect**.

14.  Switch to the browser with the Intune Data Warehouse screen. Copy the custom
    feed URL into the clipboard.

15.  Switch back to **PowerBI Desktop** and paste the **OData URL** into the
    **URL** box and select **OK**.

16.  Close the **OData feed** pop-up by selecting **Cancel** or the **X** in the
    upper right corner.

17.  On the **Home** tab, select **Refresh**. This will load the actual data from
    Intune.

18.  In the **OData feed** dialog box, select the **Organizational account** tab
    and on then select **Sign in**.

19.  On the **Sign in** page, type **admin\@yourtenant.onmicrosoft.com**. Then
    select **Next**.

20.  On the **Enter password** page, enter the tenant Admin
    password, and select **Sign in**.

21. Back on the **OData feed** dialog box, select **Connect**. Wait for the
    connection and load of data. It will take approximately 1 minute.

22. Select **Apply changes**, next to **There are pending changes in your queries
    that haven´t been applied**. Wait for the task to complete.

23. Select **File** and then select **Export to PDF**. Wait for the PDF to be
    created.

24. When prompted, select **OK** to open the PDF file in Microsoft Edge.

25. Examine the report. You will see six different reports in the PDF file:

-   Device Summary

-   Enrollment trend

-   App protection policy

-   Compliance policy

-   Device configuration policy

-   Device inventory logs

The **Device Summary** report will display the three devices you've enrolled
in the previous labs. Not all reports will have data in them. You can
customize the reports using Power BI Desktop or create your own reports
using the data from the Intune Data Warehouse.


**END OF LAB**