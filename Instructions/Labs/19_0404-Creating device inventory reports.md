# Practice Lab - Creating device inventory reports

## Summary

In this lab, you will practice viewing inventory within Intune, Excel, and using PowerBI.

## Exercise 1 

### Scenario

You've been asked to review the inventory for LON-CL3.  Use Intune to review the devices hardware and app inventory.

#### Task 1: Examining device inventory

1.  Sign in to **LON-CL3** as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and
    then press **Enter**.

3.  Select **Devices**, then select **All devices** and in the details pane, select the
    **LON-CL3** entry. Examine the various information displayed about the device.

4.  Select **Properties** and note that you can change the **Management name**,
    **Device category** and **Device ownership**.

5.  In the **Management name** field, replace the existing text with **LON-CL3** and select **Save**.

7.  Under **Monitor**, select **Hardware** and examine the hardware from
    **LON-CL3**. You need to scroll down to see it all.

8.  Under **Monitor**, select **Discovered apps** and examine the app inventory
    from **LON-CL3**. You may need to scroll down to see it all.


### Exercise 2 Scenario

Management is requesting a report of all devices. They do not have access to the Intune dashboards, and have requested the information be sent in an Excel file.

#### Task 1: Export Intune Data

1.  On **LON-CL3**, in the Endpoint Manager portal, select **Devices** and then select **All devices**.

2.  On the **Devices | All devices** blade, in the details pane, select **Export**.

3.  When prompted, select **Yes**, and wait for the export to be prepared.

4.  When prompted by **What do you want to do with…**, select **Save**.

5.  In the **finished downloading** notification, select **Open folder**. Note the file downloaded is a zip file. 

6. In the Downloads folder, right-click the downloaded zip file and select **Extract all**. Browse to the **Downloads** folder and select **Extract**.


#### Task 2: Import Intune data into Microsoft Excel

1.  On **LON-CL3**, select **Start** and then select **Excel**.

2.  In Excel, select **Browse**. Select the **Downloads** folder and in the **All
    Excel Files** drop-down box, select **All Files**.

3.  In the **Open** dialog box, select the file you just extracted. Then select **Open**.

4.  In the **Text Import Wizard – Step 1 of 3** dialog box, select **Delimited**
    and then select **Next**.

5.  In the **Text Import Wizard – Step 2 of 3** dialog box, remove the check
    mark next to **Tab** and select the check box next to **Comma**. Then select
    **Next**.

6.  In the **Text Import Wizard – Step 3 of 3** dialog box, select **Finish**.

7.  Review the report content. When finished, close Excel and select **No** when asked about saving the report.


### Exercise 3 Scenario

Your organization uses Power BI for reporting.  You've been asked to setup Power BI for Brenda Mueller on LON-CL3 and connect to the Intune Data Warehouse. Brenda needs to see a report that shows the primary user of each device. 

#### Task 1: Install and connect Power BI to the Intune Data Warehouse

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

8.  Select **Start** and select **Power BI Desktop**.

9.  In the **Welcome to Power BI Desktop**, fill out the form as follows and
    then select **Done**:

-   First Name: **Brenda**

-   Last Name: **Mueller**

-   Email Address: **bredam\@adatum.com**

-   Enter your phone number: **12121212**

-   Country/region: **United States**

-   Company name: **A. Datum Inc.**

-   Company size: **50-249**

-   Job Title: **IT Professional**

10. After PowerBI loads, close the **Sign in to collaborate and share content** page by selecting the
    **X** in the upper right corner.

11.  With the **Home** tab selected in the ribbon, select **Get Data**. In the dialog, select **Other** on the left side, and then select **OData feed** and then select **Connect**.

12.  Switch to the browser and navigate back to the Home page in the Endpoint Manager portal. 

13.  Select **Reports** and then select **Data warehouse**.

14.  In the **OData feed for reporting service** field, copy the Odata URL into the clipboard.

15.  Switch back to **PowerBI Desktop** and paste the **OData URL** into the
    **URL** box and select **OK**.

16.  In the **OData feed** dialog box, select the **Organizational account** tab
    and on then select **Sign in**.

17.  On the **Sign in** page, type **admin\@yourtenant.onmicrosoft.com**. Then
    select **Next**.

18.  On the **Enter password** page, enter the tenant Admin
    password, and select **Sign in**.

19. Back on the **OData feed** dialog box, select **Connect**. Wait for the
    connection and load of data. 
    
20. In the **Navigator** window, select all tables. You can select the first table, and then shift-select the last table to select all tables. With all tables selected, select **Load**.

#### Task 2: Create a custom report using Power BI and Intune Data Warehouse

1.  In the **Visualizations** pane, select the **Treemap** option (the icon appears to have several rectangles of various sizes). The Treemap chart will be added to the report canvas.

2.  In the Fields pane, find the **devices** table and expand it. 

3.  Select the **deviceName** data field and drag it onto the Treemap chart in the report canvas.

4.  Drag the **deviceKey** data field from the devices table to the **Visualizations** pane and drop it on under the **Values** section in the box labeled **Add data fields here**.

5.  In the Fields pane, scroll down and find the **users** table and expand it. 

6.  Drag the **displayName** data field from the users table to the **Visualizations** pane and drop it on under the **Details** section.

_Note: You should now see device names in each report object, with a user name listed under each device. This should match the users and devices you have used in previous lab steps up until this point._

_Note: Depending on how recent the Autopilot lab was performed, LON-CL5 may show in the report as the temporary name first assigned to the VM when the lab was provisioned. This will eventually resolve with the correct device name as the Intune Data Warehouse refreshes._ 

7.  Select the **Treemap** you added to the report canvas. In the **Visualizations** pane, select the **table** report option (the icon appears as a spreadsheet) to switch the report canvas to a table view.

8.  Select **File**, then select **Export to PDF**.  The browser should launch and display the report in a PDF format. 

9.  Close all open windows.


**END OF LAB**