# MSSQL
Fix for SQL server 2019 / 2022 in windows 11
# Applies to:   SQL Server all versions.
# Steps :
   1.First To Open the **Registry**.<br/>
   2.Navigate to Path : Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device .<br/>
   3.On the Edit menu, point to New, and then select Multi-String value. Name it **ForcedPhysicalSectorSizeInBytes** .<br/>
   4.Modify the new value, type in * 4095. Select OK and close the Registry editor.<br/>
   
# Command Prompt as Administrator.
1. Add the key REG ADD "HKLM\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" /v "ForcedPhysicalSectorSizeInBytes" /t   REG_MULTI_SZ /d "* 4095" /f <br/>2.Validate if the key was added successfully. REG QUERY "HKLM\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" /v "ForcedPhysicalSectorSizeInBytes"  <br/>

# PowerShell as Administrator.
1.Add the key New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" -Name   "ForcedPhysicalSectorSizeInBytes" -PropertyType MultiString        -Force -Value "* 4095" </br>
2.Validate if the key was added successfully. Get-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" -Name   "ForcedPhysicalSectorSizeInBytes"





