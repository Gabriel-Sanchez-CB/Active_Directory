
Import-Module ActiveDirectory

$UserList = Get-Content ".\users.txt"
$Domain = "corp.local"
$OUPath = "OU=Employees,DC=corp,DC=local"
$DefaultPassword = ConvertTo-SecureString "P@ssw0rd123!" -AsPlainText -Force

foreach ($User in $UserList) {

    $FirstName = $User.Split(" ")[0]
    $LastName  = $User.Split(" ")[1]

    $Username = ($FirstName.Substring(0,1) + $LastName).ToLower()

    New-ADUser `
        -Name "$FirstName $LastName" `
        -GivenName $FirstName `
        -Surname $LastName `
        -SamAccountName $Username `
        -UserPrincipalName "$Username@$Domain" `
        -Path $OUPath `
        -AccountPassword $DefaultPassword `
        -Enabled $true `
        -ChangePasswordAtLogon $true

    Write-Host "User created: $Username"
}

Write-Host "Bulk user creation completed successfully."
