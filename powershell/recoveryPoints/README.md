# List Recovery Points Per Protected Object

Warning: this code is provided on a best effort basis and is not in any way officially supported or sanctioned by Cohesity. The code is intentionally kept simple to retain value as example code. The code in this repository is provided as-is and the author accepts no liability for damages resulting from its use.

This PowerShell script lists available recovery points for every protected object in Cohesity.

## Download the script

Run these commands from PowerShell to download the script(s) into your current directory

```powershell
# Download Commands
$scriptName = 'recoveryPoints'
$repoURL = 'https://raw.githubusercontent.com/bseltz-cohesity/scripts/master/powershell'
(Invoke-WebRequest -Uri "$repoUrl/$scriptName/$scriptName.ps1").content | Out-File "$scriptName.ps1"; (Get-Content "$scriptName.ps1") | Set-Content "$scriptName.ps1"
(Invoke-WebRequest -Uri "$repoUrl/cohesity-api/cohesity-api.ps1").content | Out-File cohesity-api.ps1; (Get-Content cohesity-api.ps1) | Set-Content cohesity-api.ps1
# End Download Commands
```

## Components

* recoveryPoints.ps1: the main python script
* cohesity-api.ps1: the Cohesity REST API helper module

Place both files in a folder together and run the main script like so:

```bash
./recoveryPoints.ps1 -vip mycluster -username myusername -domain mydomain.net
```

```text
Connected!
File-Based Backup(Physical) CentOS3.mydomain.net
	2019-02-20 00:40:01	https://mycluster/protection/job/6222/run/29301/1550641201048526/protection
	2019-02-19 00:40:01	https://mycluster/protection/job/6222/run/28777/1550554801520507/protection
	2019-02-18 00:40:00	https://mycluster/protection/job/6222/run/28270/1550468400570536/protection
	2019-02-17 00:40:01	https://mycluster/protection/job/6222/run/27772/1550382001462778/protection
	2019-02-16 00:40:01	https://mycluster/protection/job/6222/run/27103/1550295601670561/protection
	2019-02-15 00:40:00	https://mycluster/protection/job/6222/run/26595/1550209200386442/protection
	2019-02-14 00:40:01	https://mycluster/protection/job/6222/run/26093/1550122801249750/protection
Generic NAS(GenericNas) \\w2012b.mydomain.net\Downloads
	2019-02-20 00:10:01	https://mycluster/protection/job/841/run/29286/1550639401468152/protection
	2019-02-19 00:10:00	https://mycluster/protection/job/841/run/28762/1550553000993546/protection
	2019-02-18 00:10:01	https://mycluster/protection/job/841/run/28255/1550466601093680/protection
	2019-02-17 00:10:00	https://mycluster/protection/job/841/run/27757/1550380200917590/protection
	2019-02-16 00:10:00	https://mycluster/protection/job/841/run/27088/1550293800109272/protection
Infrastructure(VMware) vCenter6
	2019-02-19 23:40:01	https://mycluster/protection/job/12/run/29266/1550637601843279/protection
	2019-02-18 23:40:01	https://mycluster/protection/job/12/run/28742/1550551201378934/protection
	2019-02-17 23:40:01	https://mycluster/protection/job/12/run/28235/1550464801343984/protection
	2019-02-16 23:40:00	https://mycluster/protection/job/12/run/27737/1550378400757396/protection
	2019-02-15 23:40:00	https://mycluster/protection/job/12/run/27068/1550292000305561/protection
	2019-02-14 23:40:01	https://mycluster/protection/job/12/run/26560/1550205601241452/protection
	2019-02-13 23:40:01	https://mycluster/protection/job/12/run/26058/1550119201801767/protection
	2019-02-12 23:40:00	https://mycluster/protection/job/12/run/25536/1550032800512203/protection
	2019-02-11 23:40:00	https://mycluster/protection/job/12/run/25020/1549946400078295/protection
	2019-02-10 23:40:00	https://mycluster/protection/job/12/run/24500/1549860000767626/protection
Infrastructure(VMware) AWSControlVM
	2019-02-19 23:40:01	https://mycluster/protection/job/12/run/29266/1550637601843279/protection
	2019-02-18 23:40:01	https://mycluster/protection/job/12/run/28742/1550551201378934/protection
	2019-02-17 23:40:01	https://mycluster/protection/job/12/run/28235/1550464801343984/protection
	2019-02-16 23:40:00	https://mycluster/protection/job/12/run/27737/1550378400757396/protection
	2019-02-15 23:40:00	https://mycluster/protection/job/12/run/27068/1550292000305561/protection
	2019-02-14 23:40:01	https://mycluster/protection/job/12/run/26560/1550205601241452/protection
	2019-02-13 23:40:01	https://mycluster/protection/job/12/run/26058/1550119201801767/protection
Infrastructure(VMware) CentOS1
	2019-02-19 23:40:01	https://mycluster/protection/job/12/run/29266/1550637601843279/protection
	2019-02-18 23:40:01	https://mycluster/protection/job/12/run/28742/1550551201378934/protection
	2019-02-17 23:40:01	https://mycluster/protection/job/12/run/28235/1550464801343984/protection
	2019-02-16 23:40:00	https://mycluster/protection/job/12/run/27737/1550378400757396/protection
	2019-02-15 23:40:00	https://mycluster/protection/job/12/run/27068/1550292000305561/protection
	2019-02-14 23:40:01	https://mycluster/protection/job/12/run/26560/1550205601241452/protection
	2019-02-13 23:40:01	https://mycluster/protection/job/12/run/26058/1550119201801767/protection
	2019-02-12 23:40:00	https://mycluster/protection/job/12/run/25536/1550032800512203/protection
	2019-02-11 23:40:00	https://mycluster/protection/job/12/run/25020/1549946400078295/protection
	2019-02-10 23:40:00	https://mycluster/protection/job/12/run/24500/1549860000767626/protection
```
