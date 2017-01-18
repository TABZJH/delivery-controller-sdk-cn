## 创建目录

以下示例显示了如何为一组 Machine Creation Services (MCS) 计算机创建目录。

开始之前，请务必按照 [SDK 入门](./getting-started.md)中详细介绍的步骤进行操作。

本文档介绍了如何使用 Studio 执行要编写脚本的操作（在本例中，是为一组 Machine Creation Services 计算机创建目录），以及如何收集 Studio 为执行任务所做的 SDK 操作的日志。 之后，可以自定义此输出，以生成自动完成目录创建的脚本。

!!! tip "注意" 为确保始终获得最新的增强功能和修复程序，Citrix 建议您按照本文档中所述的过程进行操作，而不是复制并粘贴示例脚本。 为了增强可读性，在脚本中添加了行号和换行符。

**了解脚本**

以下部分介绍由 Studio 生成的脚本各部分的作用。这将有助于您自定义自己的脚本。为了增强可读性，添加了行号。

```PowerShell
1. Start-LogHighLevelOperation -AdminAddress
'ddc.dumdev.internal.citrix.com:80' -Source 'Studio' -StartTime 29/05/2013 14:43:08 -Text 'Create Machine Catalog `'ExampleMachines`''
```

开始执行记录操作，并返回日志 ID，该 ID 将提供给后续操作，以将其与大型任务相关联。

```PowerShell
2. New-BrokerCatalog
-AdminAddress 'ddc.dumdev.internal.citrix.com:80' -AllocationType 'Permanent' -Description 'Example Machines' -IsRemotePC $False -LoggingId
f39a2792-064a-43eb-97c7-397cc1238e46 -MinimumFunctionalLevel 'L7' -Name 'ExampleMachines' -PersistUserChanges 'OnPvd' -ProvisioningType 'MCS' -Scope @()
-SessionSupport 'SingleSession'
```

创建 Broker 目录。此目录由即将创建的计算机进行填充。

```PowerShell
3. New-AcctIdentityPool -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -AllowUnicode -Domain 'dumdev.internal.citrix.com'
   -IdentityPoolName 'ExampleMachines' -LoggingId f39a2792-064a-43eb-97c7-397cc1238e46 -NamingScheme 'Example-####' -NamingSchemeType 'Numeric'
   -OU 'OU=DUMVMs,DC=dumdev,DC=internal,DC=citrix,DC=com' -Scope @()
```

创建标识池。这定义用于创建 AD 计算机帐户的机制。标识池将用作为即将创建的计算机而创建的 AD 帐户的容器。

```PowerShell
4. Set-BrokerCatalogMetadata -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -CatalogId 1 -LoggingId f39a2792-064a-43eb-97c7-397cc1238e46 -Name
'Citrix_DesktopStudio_IdentityPoolUid' -Value 'b99aee6d-8772-4dbc-978b-8eb9a26e2407'
```

在 Broker 目录中，利用标识池的详细信息设置元数据。这不是必需的。

```PowerShell
5. Test-ProvSchemeNameAvailable -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -ProvisioningSchemeName @('ExampleMachines')
```

检查请求的名称是否可用。这不是必需的。

```PowerShell
6. New-ProvScheme -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -CleanOnBoot -HostingUnitName 'SharedNFS' -IdentityPoolName 'ExampleMachines' -LoggingId
f39a2792-064a-43eb-97c7-397cc1238e46 -MasterImageVM 'XDHyp:\hostingunits\SharedNFS\BaseVM.vm\Base OS,
domain joined and activated.snapshot \Pre-reqs installed.snapshot\\Updates Applied.snapshot\VDA75-no agent.snapshot\Updated Agent.snapshot'
-NetworkMapping @{0='xdhyp:\hostingunits\SharedNFS\Network0.network'} -PersonalVDiskDriveLetter P -PersonalVDiskDriveSize 10 -ProvisioningSchemeName 'ExampleMachines'
-RunAsynchronously -Scope @() -UsePersonalVDiskStorage -VMCpuCount 1 -VMMemoryMB 1024
```

创建置备方案对象。 这是要创建的计算机的模板。 其中指定了虚拟机管理程序、网络、存储、内存和要使用的 CPU 数等。 它采用已设置的系统中的参数，例如，托管单元名称和要用于即将创建的计算机的 VM 快照的路径。 此命令“完整”复制要使用的 VM 快照，因此，此过程可能需要一段时间才能完成。

在此示例中，Studio 脚本指定了此命令中的 -RunAsyncronous 标志。 这意味着，此命令会在运行结束之前将控制权返回给管理员。因此，必须等命令运行结束再执行任何需要此命令完成才能执行的操作。 如果未指定此标志，此命令将以内联方式同步运行，并且直到命令运行完成（成功或失败）后，才会返回控制权。 可以使用 Get-ProvTask cmdlet 查看异步任务的状态。 提供启动任务的操作时返回的任务 ID。在本例中为 New-ProvScheme cmdlet。

```PowerShell
7. Set-BrokerCatalog -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -LoggingId f39a2792-064a-43eb-97c7-397cc1238e46 -Name 'ExampleMachines'
   -ProvisioningSchemeId 76125e3a-9001-4993-86b6-eefc85c87880
```

执行上述步骤中创建的置备方案的唯一 ID 更新 BrokerCatalog。

```PowerShell
8. Add-ProvSchemeControllerAddress -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -ControllerAddress @('DDC.dumdev.internal.citrix.com')
-LoggingId f39a2792-064a-43eb-97c7-397cc1238e46 -ProvisioningSchemeName 'ExampleMachines'
```

在置备方案对象中，添加一组控制器地址。 这是一组地址列表，在部署时，创建的计算机可以使用这些地址在控制器 (Broker) 中注册。 可以通过多种方式提供计算机的注册地址。但是，如果管理员要使用 VDA 安装程序中的“允许 Machine Creation Service 提供此信息”，则必须提供此信息。 对此列表所做的变更仅影响更改后创建的计算机，不会影响现有计算机。

```PowerShell
9. Get-AcctADAccount -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -IdentityPoolUid b99aee6d-8772-4dbc-978b-8eb9a26e2407 -Lock $False -MaxRecordCount 2147483647 -State 'Available'
```

Studio 可以从标识池获取可用计算机标识的列表。这样一来，如果存在过去已创建但尚未使用的现有帐户，可以使用这些帐户而不必创建新帐户。 请注意，在脚本中这不是必需的，因为只要脚本运行时所在的上下文具有创建新帐户的权限，即可采用创建新帐户的方式。 但是，如果脚本无权创建新帐户，请将脚本改为使用可用帐户（运行脚本前，需要执行单独的过程，以便为标识池提供一组帐户）。

```PowerShell
10. New-AcctADAccount -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -Count 2 -IdentityPoolUid b99aee6d-8772-4dbc-978b-8eb9a26e2407 -LoggingId
f39a2792-064a-43eb-97c7-397cc1238e46
```

在 Active Directory 中，创建所需的 AD 计算机帐户。 此脚本将创建一个帐户，但如果需要，可以使用命令中的“Count”参数创建更多帐户。 创建的帐户将存储在通过上述步骤创建的置备方案中定义的 OU 中。

```PowerShell
11. New-ProvVM -ADAccountName @('DUMDEV\Example-0001\$','DUMDEV\Example-0002\$') -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -LoggingId
f39a2792-064a-43eb-97c7-397cc1238e46 -ProvisioningSchemeName 'ExampleMachines' -RunAsynchronously
```

根据上面创建的置备方案中的模板定义，创建虚拟机。此过程可能需要一段时间才能完成。

```PowerShell
12. Lock-ProvVM -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -LoggingId f39a2792-064a-43eb-97c7-397cc1238e46
    -ProvisioningSchemeName 'ExampleMachines' -Tag 'Brokered' -VMID @('0710bb77-d01f-d006-4d67-5472e5cd349f')
```

锁定已置备的虚拟机，并防止意外修改虚拟机。 SDK 用户可以以此来指示虚拟机正在使用以及锁定原因。 此脚本通过“已设置代理”标志锁定 VM。该标志指示虚拟机已创建并添加到 Broker 目录，必须先将其从目录中移除，才能进行删除。 可以根据需要设置标记名称。

```PowerShell
13. New-BrokerMachine -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -CatalogUid 1 -HostedMachineId '0710bb77-d01f-d006-4d67-5472e5cd349f' -HypervisorConnectionUid 1
-LoggingId f39a2792-064a-43eb-97c7-397cc1238e46 -MachineName 'S-1-5-21-3918710733-2340574387-1999698698-109114'
```

创建 Broker 计算机对象。这些对象存储在目录中，并将随目录一起加入已置备的计算机。

```PowerShell
14. Start-BrokerMachinePvdImagePrepare -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -InputObject @(2) -LoggingId f39a2792-064a-43eb-97c7-397cc1238e46
```

请求 Broker Service 启动 Personal vDisk 的准备操作。这是计算机初始化 Personal vDisk 存储所必需的操作。

```PowerShell
15. Stop-LogHighLevelOperation -AdminAddress 'ddc.dumdev.internal.citrix.com:80' -HighLevelOperationId f39a2792-064a-43eb-97c7-397cc1238e46 -IsSuccessful $true
```

停止第一步中开始的记录操作，并指示操作成功。

**自定义脚本**

以下部分介绍如何将 Studio 输出转换并修改成更适用的脚本。 除使用变量和删除不需要的命令外，还介绍了如何通过计算机创建循环过程来控制所创建计算机的数量。 为了增强可读性，添加了行号。

```PowerShell
1[CmdletBinding()]

param

(

[Parameter(Mandatory=$true)] [string] $hostingUnitPath,

[Parameter(Mandatory=$true)] [string] $catalogName,

[string] $catalogDescription,

[Parameter(Mandatory=$true)] [int] $numVmsToCreate,

[string] $adminAddress,

[Parameter(Mandatory=$true)] [string] $namingScheme,

[string] $OU,

[Parameter(Mandatory=$true)] [string] $domain,

[Parameter(Mandatory=$true)] [string] $masterImagePath

)

2. Set-HypAdminConnection -AdminAddress $adminAddress

3. $hostingUnit = get-item $hostingUnitPath

4. $hostConnection = $hostingUnit.hypervisorConnection

5. $brokerHypConnection = Get-BrokerHypervisorConnection -HypHypervisorConnectionUid $hostConnection.HypervisorConnectionUid

6. # Start logged operation

7. $loggingOp = Start-LogHighLevelOperation -AdminAddress $adminAddress -Source 'Scripted' -Text "Create Machine Catalog `'$catalogName`'"

8. $loggingId = $loggingOp.Id

9. # Create the broker catalog and the AD Identity account pool

10. $catalog = New-BrokerCatalog -AllocationType 'Permanent' -Description $catalogDescription -IsRemotePC $False

-MinimumFunctionalLevel 'L7' -Name $catalogName -PersistUserChanges
'OnPvd' -ProvisioningType 'MCS' -Scope @() -SessionSupport 'SingleSession' -LoggingId $loggingId -AdminAddress
$adminAddress

11. $adPool = New-AcctIdentityPool -IdentityPoolName $catalogName
-NamingScheme $namingScheme

-NamingSchemeType 'Numeric' -OU $OU -Domain $domain -AllowUnicode
-LoggingId $loggingId -AdminAddress $adminAddress

12. Set-BrokerCatalogMetadata -CatalogId $catalog.Uid -Name
'Citrix_DesktopStudio_IdentityPoolUid' -Value $adPool.IdentityPoolUid -LoggingId $loggingId -AdminAddress
$adminAddress

13. ###################################################################

14. #create the ProvisioningScheme and wait for it to complete (reporting progress)

15. $provSchemeTaskID = New-ProvScheme -ProvisioningSchemeName
$catalogName -HostingUnitUID $hostingUnit.HostingUnitUID

-IdentityPoolUID $adpool.IdentityPoolUid -CleanOnBoot -MasterImageVM
$masterImagePath -UsePersonalVDiskStorage

-PersonalVDiskDriveLetter P -PersonalVDiskDriveSize 10 -RunAsynchronously
-LoggingId $loggingId -AdminAddress $adminAddress

16. $ProvTask = get-provTask -TaskID $provSchemeTaskID -AdminAddress $adminAddress

17. $taskProgress = 0

18. write-host "Creating New ProvScheme"

19. while ($provTask.Active -eq $true)

20. {

21. # catch an uninitialized task progress, this occurs until the product initialized the value

22. try {$totalPercent = if ($provTask.TaskProgress){$provTask.TaskProgress} else {0}} catch {}

23. Write-Progress -activity "Creating Provisioning Scheme:" -status "$totalPercent% Complete:" -percentcomplete $totalPercent

24. sleep 30

25. $ProvTask = get-provTask -TaskID $provSchemeTaskID -AdminAddress $adminAddress

26. }

27. write-host "New ProvScheme Creation Finished"

28. $provScheme = get-provScheme -ProvisioningSchemeUID $provTask.ProvisioningSchemeUid

29. $controllers = Get-BrokerController | select DNSName

30. Add-ProvSchemeControllerAddress -ProvisioningSchemeUID $provScheme.ProvisioningSchemeUID -ControllerAddress $controllers -LoggingId $loggingId -AdminAddress $adminAddress

31. ###################################################################

32. # Set the provisioning scheme id for the broker catalog

33. Set-BrokerCatalog -InputObject $catalog -ProvisioningSchemeId $provTask.ProvisioningSchemeUid -LoggingId $loggingId -AdminAddress $adminAddress

34. ###################################################################

35. # create the AD accounts required and then create the Virtual machines (reporting progress)

36. $accts = New-AcctADAccount -IdentityPoolUid $adPool.IdentityPoolUid -Count $numVMsToCreate -LoggingId $loggingId -AdminAddress $adminAddress

37. $provVMTaskID = New-ProvVM -ProvisioningSchemeUID $provScheme.ProvisioningSchemeUID

-ADAccountName $accts.SuccessfulAccounts -RunAsynchronously -LoggingId $loggingId -AdminAddress $adminAddress

38. # wait for the VMS to finish Provisioning

39. $ProvTask = get-provTask -TaskID $provVMTaskID -AdminAddress $adminAddress

40. while ($provTask.Active -eq $true)

41. {

42. # catch an uninitialized task progress, this occurs until the product initialized the value

43. try {$totalPercent = if ($provTask.TaskProgress){$provTask.TaskProgress} else {0}} catch {}

44. Write-Progress -activity "Creating Machines:" -status "$totalPercent% Complete:" -percentcomplete $totalPercent

45. sleep 5

46. $ProvTask = get-provTask -TaskID $provVMTaskID -AdminAddress $adminAddress

47. }

48. write-host "VM Creation Finished"

49. # Lock the VMs and add them to the broker Catalog

50. $provisionedVMs = get-ProvVM -ProvisioningSchemeUID
$provScheme.ProvisioningSchemeUID -AdminAddress $adminAddress

51. $provisionedVMs | Lock-ProvVM -ProvisioningSchemeUID $provScheme.ProvisioningSchemeUID
-Tag 'Brokered' -LoggingId $loggingId -AdminAddress $adminAddress

52. $provisionedVMs | ForEach-Object {New-BrokerMachine -CatalogUid $catalog.UID -HostedMachineId $_.VMId

-HypervisorConnectionUid $brokerHypConnection.UID -MachineName $_.ADAccountSid -LoggingId $loggingId -AdminAddress $adminAddress}

53. Stop-LogHighLevelOperation -IsSuccessful $true -HighLevelOperationId $loggingId -AdminAddress $adminAddress
```