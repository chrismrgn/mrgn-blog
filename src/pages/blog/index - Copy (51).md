---
title: "Azure Quickstart"
date: 2013-10-01T22:00:24.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

Here is a quick code sample to create a virtual machine from PowerShell on Windows Azure.

I use a variation of this script to quickly pop up VM's to host SDL Tridion in the Cloud

#Import-AzurePublishSettingsFile
Set-AzureSubscription -SubscriptionId "SUBSCRIPTION\_ID" -SubscriptionName "SUBSCRIPTION\_NAME" -CurrentStorageAccount "STORAGE\_NAME"

#Windows Server 2012 with SQL Server 2012 SP1
$image = "fb83b3509582419d99629ce476bcb5c8\_\_Microsoft-SQL-Server-2012SP1-Standard-CY13SU04-SQL2012-SP1-11.0.3350.0-Win2012"
$adminPassword = "PASSWORD"

#Get Location - Optional override to 'West US'
$locations = Get-AzureLocation
$myLoc = $locations\[0\].name

#Create VM
$vm = New-AzureVMConfig –ImageName $image –Name "ScriptedTdnVM" –InstanceSize "ExtraSmall" –HostCaching "ReadWrite" \`
 | Add-AzureProvisioningConfig -Windows -AdminUsername "TridionAdmin" -Password $adminPassword \`
 | Add-AzureDataDisk -CreateNew -DiskSizeInGB 50 -DiskLabel 'scriptedtdndisk' -LUN 0 \`
 | New-AzureVM –ServiceName "ScriptedTridionEnvironment" -location $myLoc
