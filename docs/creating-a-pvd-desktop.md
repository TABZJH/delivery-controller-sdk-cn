## 创建 PvD 桌面

本文档提供了用于创建包含 Personal vDisk (PvD) 桌面的交付组的脚本示例。

开始之前，请务必按照[入门指南](./getting-started.md)中详细介绍的步骤进行操作，该文档说明了如何使用 Studio 执行要编写脚本的操作以及收集 Studio 为执行任务所做的 SDK 操作的日志。 之后，可以自定义此输出，以生成自动完成任务的脚本。

!!! tip "注意" 为确保始终获得最新的增强功能和修复程序，Citrix 建议您按照本文档中所述的过程进行操作，而不是复制并粘贴示例脚本。

**了解脚本**

以下部分介绍由 Studio 生成的脚本各部分的作用。 这将有助于您自定义自己的脚本。 为了增强可读性，在脚本中添加了行号和换行符。

```poweshell
1. Start-LogHighLevelOperation -AdminAddress 'test-ddc.mydomain.com:80'
-Source 'Studio' -StartTime 31/07/2013 10:08:58 -Text 'Create Delivery Group `'Win7 PvD
Desktops`''
```

开始执行记录操作并返回日志 ID，用于将后续操作与大型任务相关联。

```poweshell
2. New-BrokerDesktopGroup -AdminAddress 'test-ddc.mydomain.com:80' -ColorDepth 'TwentyFourBit' -DeliveryType 'DesktopsOnly' -DesktopKind 'Private' -InMaintenanceMode
$False -IsRemotePC $False -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -MinimumFunctionalLevel 'L7' -Name 'Win7 PvD Desktops' -OffPeakBufferSizePercent 10 -PeakBufferSizePercent 10 -PublishedName 'Win7 PvD Desktops' -Scope @() -SecureIcaRequired \$False -SessionSupport 'SingleSession -ShutdownDesktopsAfterUse \$False -TimeZone 'GMT Standard Time'
```

通过 Studio 向导收集的选项创建一个新交付组。

```poweshell
3. Add-BrokerMachinesToDesktopGroup -AdminAddress 'test-ddc.mydomain.com:80' -Catalog 'win7-pvd' -Count 2 -DesktopGroup 'Win7 PvD Desktops' -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99
```

将从指定目录请求的计算机数添加到新交付组。

```poweshell
4. Set-Variable -Name 'brokerUsers' -Value @('S-1-5-21-3291547628-200264090-930806513-1104','S-1-5-21-3291547628-200264090-930806513-1105') Get-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Filter {(SID -in $brokerUsers)} -MaxRecordCount 2147483647 Remove-Variable -Name 'brokerUsers' New-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Name
'MYDOMAIN\user1' New-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Name
'MYDOMAIN\user2'
```

不需要执行上述命令，Studio 正在验证用户。

```poweshell
5. Test-BrokerAssignmentPolicyRuleNameAvailable -AdminAddress 'test-ddc.mydomain.com:80' -Name @('Win7 PvD Desktops')
```

Studio 检查策略分配名称是否可用。

```poweshell
6. New-BrokerAssignmentPolicyRule -AdminAddress 'test-ddc.mydomain.com:80' -DesktopGroupUid 41 -Enabled $True -IncludedUserFilterEnabled $False -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -MaxDesktops 1 -Name 'Win7 PvD Desktops'
```

为交付组创建新策略分配规则。未在此处指定任何用户，因此，所有控制操作都通过访问策略规则实现。

```poweshell
7. Set-Variable -Name 'brokerUsers' -Value @('S-1-5-21-3291547628-200264090-930806513-1104','S-1-5-21-3291547628-200264090-930806513-1105')
Get-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Filter {(SID -in \$brokerUsers)} -MaxRecordCount 2147483647

Remove-Variable -Name 'brokerUsers'

New-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Name 'MYDOMAIN\\user1'

New-BrokerUser -AdminAddress 'test-ddc.mydomain.com:80' -Name 'MYDOMAIN\\user2'
```

不需要执行上述命令，Studio 正在执行进一步的检查。

```poweshell
8. Test-BrokerAccessPolicyRuleNameAvailable -AdminAddress 'test-ddc.mydomain.com:80' -Name @('Win7 PvD Desktops\_Direct')
```

Studio 测试访问策略规则是否可用。

```poweshell
9. New-BrokerAccessPolicyRule -AdminAddress 'test-ddc.mydomain.com:80' -AllowedConnections 'NotViaAG' -AllowedProtocols @('HDX','RDP') -AllowRestart $True -DesktopGroupUid
41 -Enabled \$True -IncludedSmartAccessFilterEnabled $True -IncludedUserFilterEnabled $True -IncludedUsers @('MYDOMAIN\user1','MYDOMAIN\user2') -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -Name 'Win7 PvD Desktops_Direct'
```

为新桌面创建访问策略规则以实现非 NetScaler Gateway 连接。

```poweshell
10. Test-BrokerAccessPolicyRuleNameAvailable -AdminAddress 'test-ddc.mydomain.com:80' -Name @('Win7 PvD Desktops_AG') New-BrokerAccessPolicyRule -AdminAddress 'test-ddc.mydomain.com:80' -AllowedConnections 'ViaAG' -AllowedProtocols @('HDX','RDP') -AllowRestart $True -DesktopGroupUid 41 -Enabled $True -IncludedSmartAccessFilterEnabled $True -IncludedSmartAccessTags @() -IncludedUserFilterEnabled $True -IncludedUsers
@('MYDOMAIN\user1','MYDOMAIN\user2') -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -Name 'Win7 PvDDesktops_AG'
```

Studio 重复此过程以实现 NetScaler Gateway 连接。

```poweshell
11. Test-BrokerPowerTimeSchemeNameAvailable -AdminAddress 'test-ddc.mydomain.com:80' -Name @('Win7 PvD Desktops_Weekdays') New-BrokerPowerTimeScheme -AdminAddress 'test-ddc.mydomain.com:80' -DaysOfWeek 'Weekdays' -DesktopGroupUid 41 -DisplayName 'Weekdays' -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -Name 'Win7 PvD Desktops_Weekdays' -PeakHours @($False,$False,$False,$False,$False,$False,$False,$True,$True,$True,$True,$True,$True,$True,$True, $True,$True,$True,$True,$False,$False,$False,$False,$False) -PoolSize @(0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0) Test-BrokerPowerTimeSchemeNameAvailable -AdminAddress 'test-ddc.mydomain.com:80' -Name @('Win7 PvD Desktops_Weekend') New-BrokerPowerTimeScheme -AdminAddress 'test-ddc.mydomain.com:80' -DaysOfWeek 'Weekend' -DesktopGroupUid 41 -DisplayName 'Weekend' -LoggingId 846f2d42-a994-4bce-ab58-be05c8d73b99 -Name 'Win7 PvD Desktops_Weekend' -PeakHours @($False,$False,$False,$False,$False,$False,$False,$True,$True,$True,$True,$True,$True,$True,$True,$True,$True,$True,$True,$False,$False,$False,$False,$False) -PoolSize @(0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0)
```

Studio 检查（可选）工作日和周末电源方案的名称是否可用，然后添加这些名称。

```poweshell
12. Stop-LogHighLevelOperation -AdminAddress 'test-ddc.mydomain.com:80' -EndTime 31/07/2013 10:09:05 -HighLevelOperationId '846f2d42-a994-4bce-ab58-be05c8d73b99' -IsSuccessful $True
```

停止第 1 步中开始的记录操作，并指示操作成功。

**自定义脚本**

本部分介绍如何将 Studio 输出转换并修改成更适用的脚本。

此脚本将创建一个包含 PvD 桌面的交付组。 在参数中指定的目录必须已存在且能适当地填充（填充静态分配类型和 PvD 磁盘）。 此脚本设计为由以 Citrix 管理员身份登录的用户从 PowerShell 命令行运行。 不针对权限执行任何检查；如果用户没有相应的权限，此脚本将失败。

```poweshell
&lt;\#

Sample usage:

.\CreatePvDGroup.ps1 `

-GroupName "Win7 PvD Desktops" `

-SrcCatalog "win7-pvd" `

-NumDesktops 2 `

-Users @('mydomain\user1','mydomain\user2') `

\#&gt;

Param(

[Parameter(Mandatory=\$true)\] \[string\] \$GroupName,

\[Parameter(Mandatory=\$true)\] \[string\] \$SrcCatalog,

\[Parameter(Mandatory=\$true)\] \[int\] \$NumDesktops,

\[Parameter(Mandatory=\$true)\] \[array\] \$Users

\[string\] \$AdminAddress

)
```

下表说明了此脚本中使用的参数。

| 参数          |                                             说明                                              |
| ----------- |:-------------------------------------------------------------------------------------------:|
| SrcCatalog  |                     用于创建 PvD 桌面的目录的名称。通过指定静态分配类型来创建目录。计算机还必须具有 PvD 磁盘。                      |
| GroupName   |                     用于创建 PvD 桌面的目录的名称。通过指定静态分配类型来创建目录。计算机还必须具有 PvD 磁盘。                      |
| NumDesktops |                          添加到 PvD 桌面组的计算机数。如果可用计算机数不足，则将添加尽可能多的计算机。                          |
| 用户          | 哪些用户可以访问组。这是用户或组的列表，例如 @('mydomain\Domain Users') 或 @('mydomain\user1','mydomain\user2') |

```powershell
Set-HypAdminConnection -AdminAddress $adminAddress
```

指定要使用的虚拟机管理程序的管理连接。对某些命令而言，不再需要使用 -AdminAddress。

```powershell
$peakPoolSize = 2

$weekendPoolSizeByHour = new-object int[] 24

$weekdayPoolSizeByHour = new-object int[] 24

9..17 | %{ $weekdayPoolSizeByHour[$_] = $peakPoolSize }

$peakHours = (0..23 | %{ $_ -ge 9 -and $_ -le 17 })
```

这将创建 24 元素阵列，其中每个条目中包含一个 1 或 0。 使用这些阵列可为交付组指定电源计划的高峰时段。 工作日的元素 9 到 17（从 09:00 到 17:00 的时段）设置为 1，其他则保留为 0。 如果可用，则会在高峰时间启动两个未分配的计算机。

```powershell
$logId = Start-LogHighLevelOperation` -Text "Create PvD desktop group" `
-Source "Create PvD Desktop Group Script"
```

开始执行新的记录操作。此操作将返回一个日志 ID，该 ID 将传递到后续操作，以将其与创建组任务相关联。

```powershell
$grp = New-BrokerDesktopGroup `

-DesktopKind 'Private' `

-DeliveryType 'DesktopsOnly' `

-LoggingId $logId.Id `

-Name $GroupName `

-PublishedName $GroupName `

-SessionSupport 'SingleSession' `

-ShutdownDesktopsAfterUse $False

$count = Add-BrokerMachinesToDesktopGroup `

-Catalog $SrcCatalog `

-Count $NumDesktops `

-DesktopGroup \$GroupName `

-LoggingId $logId.Id

"$count machines added to the PvD desktop group"
```

创建新交付组，用于交付专用桌面。 使用的目录必须已填充适合的计算机（永久性具有 PvD 磁盘）。 PublishedName 是向最终用户显示的名称；以下各项使用的名称与组名称相同。

```powershell
New-BrokerAssignmentPolicyRule \`

-DesktopGroupUid \$grp.Uid \`

-IncludedUserFilterEnabled \$False \`

-LoggingId \$logId.Id \`

-MaxDesktops 1 \`

-Name (\$GroupName + '\_AssignRule') \`

| Out-Null
```

已分配的桌面需要具有分配策略。禁用用户过滤器以便完全通过访问策略规则对访问进行控制。

```powershell
New-BrokerAccessPolicyRule `

-AllowedConnections 'NotViaAG' `

-AllowedProtocols @('HDX','RDP') `

-AllowRestart $True `

-DesktopGroupUid $grp.Uid `

-IncludedSmartAccessFilterEnabled $True `

-IncludedUserFilterEnabled $True `

-IncludedUsers $Users `

-LoggingId $logId.Id `

-Name ($GroupName + '_Direct') `

| Out-Null

New-BrokerAccessPolicyRule `

-AllowedConnections 'ViaAG' `

-AllowedProtocols @('HDX','RDP') `

-AllowRestart $True `

-DesktopGroupUid $grp.Uid `

-IncludedSmartAccessFilterEnabled $True `

-IncludedSmartAccessTags @() `

-IncludedUserFilterEnabled $True `

-IncludedUsers $Users `

-LoggingId $logId.Id `

-Name ($GroupName + '_AG') `

| Out-Null
```

指定任何访问限制：允许使用 NetScaler Gateway 以及 HDX 和 RDP 协议进行直接访问。如有必要，用户可以请求重新启动桌面。

```poweshell
New-BrokerPowerTimeScheme `

-DaysOfWeek 'Weekdays' `

-DesktopGroupUid $grp.Uid `

-DisplayName 'Weekdays' `

-LoggingId $logId.Id `

-Name ($GroupName + '_Weekdays') `

-PeakHours $peakHours `

-PoolSize $weekdayPoolSizeByHour `

| Out-Null

New-BrokerPowerTimeScheme `

-DaysOfWeek 'Weekend' `

-DesktopGroupUid $grp.Uid `

-DisplayName 'Weekend' `

-LoggingId $logId.Id `

-Name ($GroupName + '_Weekend') `

-PeakHours $peakHours `

-PoolSize $weekendPoolSizeByHour `

| Out-Null
```

可选：指定电源计划。

```powershell
Stop-LogHighLevelOperation -HighLevelOperationId
$logId.Id -IsSuccessful $True
```

停止配置日志记录并指示是否成功。