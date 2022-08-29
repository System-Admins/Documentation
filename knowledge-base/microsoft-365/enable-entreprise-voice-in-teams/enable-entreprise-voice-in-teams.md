# Enable Enterprise Voice In Microsoft Teams

Use the following guide to enable Enterprise Voice in Microsoft Teams on a single user.

Please make sure that:

- You are "**Teams administrator**" or "**Global admin**" in Microsoft 365 and have the credentials ready for your admin account.
- The machine you use for this tutorial has a good internet connection.
- The "**Audio Conference**" and "**Phone System**" is assigned to the user as licenses in Microsoft 365
- Allowed to execute PowerShell on the device you are using for this tutorial



1. Open a PowerShell terminal (C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe).

2. Edit the variable on line 2 to match the user who needs the Enterprise Voice feature enabled and then copy and execute in the PowerShell terminal.

   ```powershell
   # User e-mail (UPN).
   $Identity = "joe@contoso.com";
   
   # Bypass execution policy.
   Set-ExecutionPolicy -ExecutionPolicy Bypass -Force -Scope CurrentUser;
   
   # Install module.
   Install-Module -Name MicrosoftTeams -Force -Scope CurrentUser -SkipPublisherCheck -AllowClobber -Confirm:$false;
   
   # Import module.
   Import-Module -Name MicrosoftTeams -Force;
   
   # Connect to Microsoft Teams.
   Connect-MicrosoftTeams;
   
   # Enable entrprise voice.
   Set-CsPhoneNumberAsssignment -Identity $Identity -EnterpriseVoiceEnabled $true;
   ```

   

   The above will install the Microsoft Teams PowerShell module, prompt for credentials to your administrator account in Microsoft 365, and enables the Enterprise Voice feature on the user-specified on line 2.
