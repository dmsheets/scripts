# Add a VM to a Cohesity Protection Job using PowerShell

Warning: this code is provided on a best effort basis and is not in any way officially supported or sanctioned by Cohesity. The code is intentionally kept simple to retain value as example code. The code in this repository is provided as-is and the author accepts no liability for damages resulting from its use.

This powershell script adds a VM to an existing protection job.

## Download the script

Run these commands from PowerShell to download the script(s) into your current directory

```powershell
# Download Commands
$scriptName = 'addVMtoProtectionJob'
$repoURL = 'https://raw.githubusercontent.com/bseltz-cohesity/scripts/master/powershell'
(Invoke-WebRequest -Uri "$repoUrl/$scriptName/$scriptName.ps1").content | Out-File "$scriptName.ps1"; (Get-Content "$scriptName.ps1") | Set-Content "$scriptName.ps1"
(Invoke-WebRequest -Uri "$repoUrl/cohesity-api/cohesity-api.ps1").content | Out-File cohesity-api.ps1; (Get-Content cohesity-api.ps1) | Set-Content cohesity-api.ps1
# End Download Commands
```

## Components

* addVMtoProtectionJob.ps1: the main powershell script
* cohesity-api.ps1: the Cohesity REST API helper module

Place both files in a folder together and run the main script like so:

```powershell
# example
./addVMtoProtectionJob.ps1 -vip mycluster -username admin -jobName 'vm backup' -vmNames mongodb, webserver1
# end example
```

or if you want to input a list of VMs from a text file, you can do this:

```powershell
# example
./addVMtoProtectionJob.ps1 -vip mycluster -username admin -jobName 'vm backup' -vmNames (Get-Content ./vms.txt)
# end example
```

## Parameters

* -vip: DNS or IP of the Cohesity Cluster
* -username: Cohesity User Name
* -domain: (optional) - defaults to 'local'
* -jobName: name of protection job to add VMs to
* -vmNames: names of one or more VMs (comma separated) to add to the protection job
