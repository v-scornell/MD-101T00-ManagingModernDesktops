### Managing Modern Desktops 

**(Updated/Resolved) 04-17-20**


An issue has been identified regarding the _Creating device inventory reports_ lab in Module 4. In the last task, _Creating an Intune report using Power BI and Intune Data Warehouse_, on Step 21, instead of connecting to the Data Warehouse, the student will see an error that suggest credentials may not have sufficient rights.  This is not the intended behavior._

_Resolved: This issue was due to pre-defined reports that were based on the pre-release of the Intune Datawarehouse. This has been updated with new lab steps to create reports using PowerBI._


**04-17-20**

We have received several reports of errors related to MD-101 that we have not been able to reproduce. Through further investigation, we've identified that this may be caused by an older version of the MD-100/101 VMs being provisioned. If you see what appear to be steps that do not align to the VM configuration, please verify that with your Lab Hoster that the VMs are for MD-101**T00-A** (and **not** MD-101**T01-A**). If you are unable to verify this, perform the following steps in your environment:

1.  Sign in to **LON-DC1**
2.  Verify the path **E:\Labfiles\Install\USMT** exists

If you do not see the path in step 2, and instead see a path such as E:\Labfiles\USMT, your environment does not have the correct VMs. Verify the correct lab code (MD-101**T00-A**) has been selected or contact your lab provider to resolve this.

If you believe you have the correct VMs, please notify either your ALH or WWL support. You may also submit an issue on GitHub. Please see the updated Instructor Prep Guide on the Learning Download Center for more information. 


