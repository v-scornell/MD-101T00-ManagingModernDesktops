# Practice Lab - Creating device inventory reports

## Summary

In this lab, you will practice viewing inventory within Intune, Excel, and using PowerBI.

## Exercise 1 

### Scenario

You've been asked to review the inventory for LON-CL4.  Use Intune to review the devices hardware and app inventory.

### Task 1: Examining device inventory

1.  On **LON-CL3**, click **All devices** and in the details pane, click the
    **LON-CL4** entry. On the **Overview** blade, examine the various
    information displayed about the device.

2.  Click **Properties** and note that you can change the **Management name**,
    **Device category** and **Device ownership**.

3.  Under **Monitor**, click **Hardware** and examine the hardware from
    **LON-CL4**. You need to scroll down to see it all.

4.  Under **Monitor**, click **Discovered apps** and examine the app inventory
    from LON-CL4. You need scroll down to see it all.


### Exercise 2 Scenario

Management is requesting a report of all device. They do not have access to the Intune dashboards, and have requested the information be sent in an Excel file.

### Task 1: Export Intune Data

1.  On **LON-CL3**, in the Azure portal, in the navigation pane, click
    **Intune**.

2.  On the **Intune** blade, click **Devices** and then click **All devices**.

3.  On the All devices blade, in the details pane, click **Export**.

4.  When prompted, click **Yes**, and wait for the export to be prepared.

5.  When prompted by **What do you want to do with…**, click up-arrow next to
    **Save** and select **Save as**.

6.  In the **Save As** dialog box, click **Save** and note that the CSV file is
    saved in the **Downloads** folder.

7.  Close the **finished downloading** notification.

### Task 2: Import Intune data into Microsoft Excel

1.  On **LON-CL3**, click **Start** and then click **Excel 2019**.

2.  In Excel, click **Browse**. Click the **Downloads** folder and in the **All
    Excel Files** drop-down box, select **All Files**.

3.  In the **Open** dialog box, select the **Intune_Devices_\<Date-Time\>**
    file. Then click **Open**.

4.  In the **Text Import Wizard – Step 1 of 3** dialog box, click **Delimited**
    and then click **Next**.

5.  In the **Text Import Wizard – Step 2 of 3** dialog box, remove the check
    mark next to **Tab** and click the check box next to **Comma**. Then click
    **Next**.

6.  In the **Text Import Wizard – Step 3 of 3** dialog box, click **Finish**.

7.  Close Excel and click **No** when asked about saving the report.


### Exercise 3 Scenario

Your organization uses Power BI for reporting.  You've been asked to setup Power BI for Brenda Mueller on LON-CL3 and connect to the Intune Data Warehouse using an OData feed and generate a PDF report.

### Task 1: Create an Intune report using Power BI and Intune Data Warehouse

1.  On **LON-CL3**, on the Task bar, click the **File Explorer** icon and browse
    to **C:\\Software**.

2.  In **File Explorer**, double-click **PBIDesktop_x64.msi**.

3.  On the **Welcome to the Microsoft Power BI Desktop (x64) Setup Wizard**
    page, click **Next**.

4.  On the **Microsoft Software License Terms** page, click **I accept the terms
    in the License Agreement** and click **Next**.

5.  On the **Destination Folder** page, click **Next**.

6.  On the **Ready to install Microsoft Power BI Desktop (x64)** page, click
    **Install**. When prompted, click **Yes**. Wait for the installation to
    complete.

7.  On the **Completed the Microsoft Power BI Desktop (x64) Setup Wizard** page,
    click **Launch Microsoft Power BI Desktop** to remove the check mark. Then
    click **Finish**.

8.  On **LON-CL3**, in the Azure portal, in the navigation pane, click
    **Intune**.

9.  Scroll to the right and under **Other tasks**, click the **Set up Intune
    Data Warehouse** link. Leave this page open.

10. Click **Start** and under **Recently added**, click **Power BI Desktop**.
    Wait for Power BI Desktop to load.

11. In the **Welcome to Power BI Desktop**, fill out the form as follows and
    then click **Done**:

-   First Name: **Brenda**

-   Last Name: **Mueller**

-   Email Address: **bredam\@adatum.com**

-   Enter your phone number: **12121212**

-   Country/region: **United States**

-   Company name: **A. Datum Inc.**

-   Company size: **50-249**

-   Job Title: **IT Professional**

1.  Close the **Sign in to collaborate and share content** page by clicking the
    X in the upper right corner.

2.  Choose **Home**, then **Get Data**. Select **OData feed** and choose
    **Basic**.

3.  Switch to the browser with the Intune Data Warehouse screen. Copy the custom
    feed URL into the clipboard.

4.  Switch back to **PowerBI Desktop** and paste the **OData URL** into the
    **URL** box and select **OK**.

5.  Close the **OData feed** pop-up by clicking **Cancel** or the **X** in the
    upper right corner.

6.  On the **Home** tab, click **Refresh**. This will load the actual data from
    Intune.

7.  In the **OData feed** dialog box, click the **Organizational account** tab
    and on then click **Sign in**.

8.  On the **Sign in** page, type **admin\@yourtenant.onmicrosoft.com**. Then
    click **Next**.

9.  On the **Enter password** page, use **Pa55w.rd** as the tenant Admin
    password, and click **Sign in**.

10. Back on the **OData feed** dialog box, click **Connect**. Wait for the
    connection and load of data. It will take approximately 1 minute.

11. Click **Apply changes**, next to **There are pending changes in your queries
    that haven´t been applied**. Wait for the task to complete.

12. Click **File** and then click **Export to PDF**. Wait for the PDF to be
    created.

13. When prompted, click **OK** to open the PDF file in Microsoft Edge.

14. Examine the report. You will see six different reports in the PDF file:

-   Device Summary

-   Enrollment trend

-   App protection policy

-   Compliance policy

-   Device configuration policy

-   Device inventory logs

The **Device Summary** report will display the three devices you’ve enrolled
in the previous labs. Not all reports will have data in them. You can
customize the reports using Power BI Desktop or create your own reports
using the data from the Intune Data Warehouse.


** END OF LAB **