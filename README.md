# Active Directory User Automation Lab

## Overview
This repository contains a PowerShell script that automates the creation of 1,000 Active Directory user accounts inside a Windows Server 2019 virtualized environment.

## Setup Instructions
1. Install Windows Server 2019 in VirtualBox.
2. Configure Active Directory and promote the server as a Domain Controller.
3. Run the PowerShell script to bulk create user accounts.

## PowerShell Script
```powershell
# Import Active Directory Module
Import-Module ActiveDirectory

# Create 1000 users
For ($i=1; $i -le 1000; $i++) {
    $username = "User$i"
    $password = ConvertTo-SecureString "P@ssword123" -AsPlainText -Force
    New-ADUser -Name $username -GivenName "User" -Surname "$i" -SamAccountName $username -UserPrincipalName "$username@LabDomain.local" -Path "OU=Users,DC=LabDomain,DC=local" -AccountPassword $password -Enabled $true
}
