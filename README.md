Remove a Virtual Machine (VM) on Azure
======================================

            

This Azure Automation runbook removes a Virtual Machine (VM) on Azure using Stop-AzureVM, Remove-AzureVM activities that are available in Azure module. Given a certificate which is used to connect to your subscription, Subscription Id and VM name, the runbook
 uses Remove-AzureVM activity to remove the VM on Azure. The attached VHD(s) to the VM are deleted too. Runbook waits untill VM is removed.


**Requirements**
Before importing and using this runbook the following items must be made available:
1 Connect-Azure' runbook must be imported and published. 2 Certificate file (.pfx or .cer file) associated with the subscription used
** **


**Example**


1) Create Certificate Asset 'myCert':
     Use the certificate file (.pfx or .cer file) to create a Certificate asset for ex. 'myCred' in 
     Azure -> Automation -> select automation account 'MyAutomationAccount' -> Assets -> Add Setting -> Add Credential -> 
     Certificate -> Provide name 'myCred' and upload the certificate file (.pfx or .cer)

     The same certificate must be associated with the subscription, You can verify the same for your subscription 
     at Azure -> Settings -> Management Certificates
 2) Create Azure Connection Asset 'AzureConnection'
     Azure -> Automation -> select automation account 'MyAutomationAccount' -> Assets -> Add Setting 
     -> Add Connection -> Select 'Azure' from dropdown -> Provide name ex. 'AzureConnection'  ->
     Provide AutomationCertificateName 'myCert' you created in step 1 and subscription Id

 3) To run runbook: Test or Start the runbook from Author tab

   to call from another runbook, ex:
Remove-AzureVMSample -AzureConnectionName 'AzureConnection' -ServiceName 'myService' -VMName 'myVM'
**Runbook Content:**


** **


 

 

        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
