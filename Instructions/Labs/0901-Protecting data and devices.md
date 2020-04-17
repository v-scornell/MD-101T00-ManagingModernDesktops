# Practice Lab - Protecting data and devices

## Summary

In this lab, you will practice configuring encryption using EFS and Bitlocker.

## Exercise 1: Configuring Encrypting File System (EFS)

### Scenario

Abbi and Bill share LON-CL1. Abbi is working with files containing sensitive information that requires it be encrypted. Help Abbi setup a folder to store encrypted information in on LON-CL1 and verify Bill cannot access the information. 

#### Task 1: Create a data folder and configure folder view options

1.  Sign in to **LON-CL1** as **Adatum\\Abbi** with the password **MDA101!!**.

2.  On the taskbar, select the **File Explorer** icon, select **This
    PC**, and then double-click **Local Disk (C:)**.

3.  On the ribbon, select the **Home** tab and then select 'he **New
    Folder** icon. Name the new folder **SecretAbbi**.

4.  On the ribbon, select the **View** tab and then select
    **Options**. Select **Change folder and search options**.
    
5.  In the **Folder Options** window, select **View**.

6.  In the **Advanced settings** list, select the **Show encrypted or compressed
    NTFS files in color** check box.

7.  Select **OK**.

#### Task 2: Encrypt the folder by using EFS and backup a certificate

1.  Right-click the **SecretAbbi** folder, and then select **Properties**.

2.  Select **Advanced**.

3.  On the **Advanced Attributes** dialog box, select the **Encrypt contents to
    secure data** check box. Select **OK** twice.

4.  Verify that the **SecretAbbi** folder appears in green. This confirms that
    folder is encrypted.

5.  Open the **SecretAbbi** folder.

6.  In the blank area, right-click and select **New**, and then
    select **Text Document**.'

7.  Name the new file **Secrets**, and then double-click the file to open it in
    Notepad.

8.  Enter the following text: **This is a secret file**.

9.  Close Notepad, and then when prompted, select **Save**.

10. In the **Type here to search** text box on the taskbar, type
    **certificates** and then select **Manage file encryption
    certificates**.

11. In the Encrypting File System wizard, select **Next**.

12. On the **Select or create a file encryption certificate** page ensure that
    the certificate for Abbi Skinner is issued by AdatumCA. Select **View
    certificate** to see the details and select **Ok'*. Select **Next**.

13. On the **Back up your certificate or key** page, select to backup a
    certificate and save it to the **C:\\backup\\** folder (create the backup
    folder before saving). Give it the name **certbackup**. Provide **Pa55w.rd**
    for password and select **Next** two times and then select
    **Close**.

14. Sign out from **LON-CL1**.

#### Task 3: Test access to the folder

1.  Sign in to **LON-CL1** as **ADATUM\\Bill** with the password **Pa55w.rd**.

2.  On the taskbar, select the **File Explorer** icon.

3.  Select **This PC**, and then double-clickselect **Local Disk (C:)**.

4.  Open the **SecretAbbi** folder.

5.  Double-click **Secrets**.

6.  Verify that **Access** is denied, and then select **OK**. Close Notepad.

7.  Sign out from **LON-CL1** and sign back in as **Adatum\\Abbi** with the password **MDA101!!**.


### Scenario 2 Exercise

It's been determined that all the information on LON-CL1 should be encrypted. You've been asked to configure full disk encryption on LON-CL1 and require additional authentication at startup be enabled.

#### Task 1: Configure Group Policy Object (GPO) settings

1.  In the **Type here to search** textbox on the taskbar, type **gpedit.msc**,
    and then right-click the **gpedit.msc** item and select **Run as
    administrator**. Provide administrative credentials for
    **Adatum\\Administrator**.

2.  In the Local Group Policy Editor, under the **Computer Configuration** node,
    expand **Administrative Templates**, expand **Windows Components**, and then
    expand **BitLocker Drive Encryption**.

3.  Select **Operating System Drives**, and then double-click **Require
    additional authentication at startup**.

4.  In the **Require additional authentication at startup** dialog box, select
    **Enabled**, and then select **OK**.

5.  Close all open windows.

#### Task 2: Enable BitLocker

1.  On **LON-CL1**, in the taskbar, select **File Explorer and then select This
    PC**.

2.  In the navigation pane, right-click **Local Disk (C:)**, and then select
    **Turn on BitLocker**. Provide administrative credentials, when prompted.

3.  In the **BitLocker Drive Encryption (C:)** dialog box, select **Next** three
    times and then select **Enter a password**.

4.  In the **Enter your password** and **Reenter your password** boxes, type
    **Pa55w.rd**, and then select **Next**.

5.  On the **How do you want to back up your recovery key?** page, select
    **Print the recovery key**. Select the **Microsoft Print to PDF** printer,
    and save the file as PDF. Select **Next**.

6.  On the **Choose how much of your drive to encrypt** page, select **Encrypt
    used disk space only** and select **Next**.

7.  On the **Choose which encryption mode to use** page, ensure that **New
    encryption mode (best for fixed drives on this device)** is selected, and
    then select **Next**.

8.  On the **Are you ready to encrypt this drive** page, select **Run BitLocker
    system check** and select **Continue**.

9.  Select **Restart now** and restart **LON-CL1**.

10. When LON-CL1 restarts, type **Pa55w.rd** and press Enter to unlock the
    drive.

#### Task 3: Verify BitLocker protection

1.  Sign in to **LON-CL1** as **Adatum\\Administrator** with the password
    **Pa55w.rd**.

2.  On the taskbar, select **File Explorer and then select This PC**.

3.  In the navigation pane, right-click **Local Disk (C:) and then select Manage
    BitLocker**.

4.  In the BitLocker Drive Encryption window, ensure that you see **C: BitLocker
    Encrypting** status. This means that drive is being encrypted. This takes
    some time, so you can proceed to the next task.

5.  Close all open windows.

**END OF LAB**