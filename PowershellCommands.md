# 🖥️ Active Directory PowerShell Cheat Sheet – Master Table

> All essential AD PowerShell commands organized with examples for quick reference.

| Category | Task | Command | Example |
|----------|------|---------|---------|
| **Module Setup** | Import AD module | `Import-Module ActiveDirectory` | `Import-Module ActiveDirectory` |
|  | Check module loaded | `Get-Module -ListAvailable` | `Get-Module -ListAvailable` |
| **User Management** | Create user | `New-ADUser` | `New-ADUser -Name "John Doe" -SamAccountName jdoe -UserPrincipalName jdoe@company.com -Path "OU=Sales,DC=company,DC=com" -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -Enabled $true` |
|  | Get user | `Get-ADUser` | `Get-ADUser -Identity jdoe -Properties *` |
|  | Set user property | `Set-ADUser` | `Set-ADUser -Identity jdoe -Title "Sales Manager"` |
|  | Enable account | `Enable-ADAccount` | `Enable-ADAccount -Identity jdoe` |
|  | Disable account | `Disable-ADAccount` | `Disable-ADAccount -Identity jdoe` |
|  | Remove user | `Remove-ADUser` | `Remove-ADUser -Identity jdoe -Confirm:$false` |
| **Group Management** | Create group | `New-ADGroup` | `New-ADGroup -Name "SalesTeam" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=company,DC=com"` |
|  | Get group info | `Get-ADGroup` | `Get-ADGroup -Identity SalesTeam -Properties *` |
|  | Add member | `Add-ADGroupMember` | `Add-ADGroupMember -Identity SalesTeam -Members jdoe` |
|  | Remove member | `Remove-ADGroupMember` | `Remove-ADGroupMember -Identity SalesTeam -Members jdoe -Confirm:$false` |
|  | Remove group | `Remove-ADGroup` | `Remove-ADGroup -Identity SalesTeam -Confirm:$false` |
| **OU Management** | Create OU | `New-ADOrganizationalUnit` | `New-ADOrganizationalUnit -Name "Sales" -Path "DC=company,DC=com"` |
|  | Get OU | `Get-ADOrganizationalUnit` | `Get-ADOrganizationalUnit -Filter *` |
|  | Move object | `Move-ADObject` | `Move-ADObject -Identity "CN=John Doe,OU=Users,DC=company,DC=com" -TargetPath "OU=Sales,DC=company,DC=com"` |
|  | Remove OU | `Remove-ADOrganizationalUnit` | `Remove-ADOrganizationalUnit -Identity "OU=Sales,DC=company,DC=com" -Recursive` |
| **Computer Management** | Create computer | `New-ADComputer` | `New-ADComputer -Name "PC01" -Path "OU=Computers,DC=company,DC=com"` |
|  | Get computer | `Get-ADComputer` | `Get-ADComputer -Identity PC01 -Properties *` |
|  | Disable/Enable | `Disable-ADAccount / Enable-ADAccount` | `Disable-ADAccount -Identity PC01` |
|  | Remove computer | `Remove-ADComputer` | `Remove-ADComputer -Identity PC01 -Confirm:$false` |
| **Domain & Forest Info** | Domain info | `Get-ADDomain` | `Get-ADDomain` |
|  | Domain controllers | `Get-ADDomainController` | `Get-ADDomainController -Filter *` |
|  | Forest info | `Get-ADForest` | `Get-ADForest` |
|  | FSMO roles | `Get-ADDomain` | `Get-ADDomain | select PDCEmulator,RIDMaster,InfrastructureMaster` |
|  | Transfer FSMO | `Move-ADDirectoryServerOperationMasterRole` | `Move-ADDirectoryServerOperationMasterRole -Identity DC01 -OperationMasterRole PDCEmulator` |
| **Group Policy** | Create GPO | `New-GPO` | `New-GPO -Name "Disable_USB"` |
|  | Link GPO | `New-GPLink` | `New-GPLink -Name "Disable_USB" -Target "OU=Sales,DC=company,DC=com"` |
|  | Set registry policy | `Set-GPRegistryValue` | `Set-GPRegistryValue -Name "Disable_USB" -Key "HKLM\Software\Policies\Microsoft\Windows\RemovableStorageDevices" -ValueName "Deny_All" -Type DWord -Value 1` |
|  | Get applied GPOs | `Get-GPResultantSetOfPolicy` | `Get-GPResultantSetOfPolicy -ReportType Html -Path C:\GPOReport.html` |
| **Searching & Filtering** | Find users | `Get-ADUser -Filter` | `Get-ADUser -Filter 'Name -like "*John*"'` |
|  | Locked accounts | `Search-ADAccount -LockedOut` | `Search-ADAccount -LockedOut` |
|  | Inactive users | `Search-ADAccount -AccountInactive -TimeSpan 90` | `Search-ADAccount -AccountInactive -TimeSpan 90` |
|  | Disabled accounts | `Search-ADAccount -AccountDisabled` | `Search-ADAccount -AccountDisabled` |
| **Password & Account Management** | Set password | `Set-ADAccountPassword` | `Set-ADAccountPassword -Identity jdoe -NewPassword (ConvertTo-SecureString "P@ssw0rd1" -AsPlainText -Force)` |
|  | Unlock account | `Unlock-ADAccount` | `Unlock-ADAccount -Identity jdoe` |
|  | Force change at next logon | `Set-ADUser -ChangePasswordAtLogon $true` | `Set-ADUser -Identity jdoe -ChangePasswordAtLogon $true` |
| **Reporting & Export** | List all users in OU | `Get-ADUser -SearchBase` | `Get-ADUser -SearchBase "OU=Sales,DC=company,DC=com" -Filter *` |
|  | List groups of a user | `Get-ADPrincipalGroupMembership` | `Get-ADPrincipalGroupMembership -Identity jdoe` |
|  | Export users to CSV | `Get-ADUser -Filter * | Export-Csv` | `Get-ADUser -Filter * | Export-Csv "C:\ADUsers.csv" -NoTypeInformation` |
| **Miscellaneous** | Refresh AD replication | `repadmin /syncall` | `repadmin /syncall /AdeP` |
|  | Test AD connectivity | `Test-ComputerSecureChannel` | `Test-ComputerSecureChannel -Verbose` |
|  | Check module loaded | `Get-Module -ListAvailable` | `Get-Module -ListAvailable` |
|  | Import module | `Import-Module ActiveDirectory` | `Import-Module ActiveDirectory` |

---

💡 **Tips for Mastery**:  
- Practice **CRUD operations** on users, groups, OUs, and computers.  
- Use `-Properties *` to see all attributes.  
- Export results to CSV for documentation.  
- Test PowerShell commands in **lab AD environment** before production.  
- Combine commands in **scripts** for bulk operations.  
