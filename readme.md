Get-ADUser -Filter * -Properties PasswordNeverExpires | ? {$_.PasswordNeverExpires -eq "true"} | Select-Object Name,DistinguishedName
Get-ADUser -Filter * -Properties PasswordNeverExpires | ? {$_.PasswordNeverExpires -eq "true"} | % {Set-ADUser -Identity $_.SamAccountName -PasswordNeverExpires $false -Confirm:false}

