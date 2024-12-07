# MSSQL
Fix for SQL server 2019 / 2022 in windows 11
Troubleshoot:
This article provides solutions for troubleshooting errors during installation or starting an instance of SQL Server on Windows 11 and Windows Server 2022. This article is valid for all released versions of SQL Server.
The errors discussed in this article are related to system disk sector size greater than 4 KB.
# Applies to:   SQL Server all versions.
# Notes : You might encounter the failures mentioned in the previous scenarios for a SQL Server instance you installed manually or on a LocalDB instance installed by applications.
# Steps :
   1.First To Open the **Registry**.<br/>
   2.Navigate to Path : Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device .<br/>
   3.On the Edit menu, point to New, and then select Multi-String value. Name it **ForcedPhysicalSectorSizeInBytes** .<br/>
   4.Modify the new value, type in * 4095. Select OK and close the Registry editor.<br/>

# OR
# Command Prompt as Administrator.
  1. Add the key REG ADD "HKLM\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" /v "ForcedPhysicalSectorSizeInBytes" /t   REG_MULTI_SZ /d "* 4095" /f .<br/>
  2.Validate if the key was added successfully. REG QUERY "HKLM\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" /v "ForcedPhysicalSectorSizeInBytes" . <br/>


