# Get-BrokerRebootCycle

Gets one or more reboot cycles.

## 语法

    Get-BrokerRebootCycle -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerRebootCycle [-CatalogName <String>] [-CatalogUid <Int32>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-EndTime <DateTime>] [-MachinesCompleted <Int32>] [-MachinesFailed <Int32>] [-MachinesInProgress <Int32>] [-MachinesPending <Int32>] [-MachinesSkipped <Int32>] [-Metadata <String>] [-RebootDuration <Int32>] [-RebootScheduleName <String>] [-RebootScheduleUid <Int32>] [-RestrictToTag <String>] [-StartTime <DateTime>] [-State <RebootCycleState>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerRebootCycle cmdlet is used to enumerate reboot cycles that match all of the supplied criteria.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerRebootCycle Object The reboot cycle object returned represents a single occurrence of the process of rebooting a portion (or all) of the machines in a desktop group.

    -- CatalogName (System.String)
       Name of the catalog whose machines are rebooted by this cycle if the cycle is associated with a catalog.
    
    -- CatalogUid (System.Int32?)
       Uid of the catalog whose machines are rebooted by this cycle if the cycle is associated with a catalog.
    
    -- DesktopGroupName (System.String)
       Name of the desktop group whose machines are rebooted by this cycle.
    
    -- DesktopGroupUid (System.Int32)
       Uid of the desktop group whose machines are rebooted by this cycle.
    
    -- EndTime (System.DateTime?)
       Time at which this cycle was completed, canceled or abandoned.
    
    -- MachinesCompleted (System.Int32)
       Number of machines successfully rebooted by this cycle.
    
    -- MachinesFailed (System.Int32)
       Number of machines issued with reboot requests where either the request failed or the operation did not complete within the allowed time.
    
    -- MachinesInProgress (System.Int32)
       Number of machines issued with reboot requests but which have not yet completed the operation.
    
    -- MachinesPending (System.Int32)
       Number of outstanding machines to be rebooted during the cycle but on which processing has not yet started.
    
    -- MachinesSkipped (System.Int32)
       Number of machines scheduled for reboot during the cycle but which were not processed either because the cycle was canceled or abandoned or because the machine was unavailable for reboot processing throughout the cycle.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Map of metadata associated with this cycle.
    
    -- RebootDuration (System.Int32)
       Approximate maximum number of minutes over which the reboot cycle runs.
    
    -- RebootScheduleName (System.String)
       Name of the Reboot Schedule which triggered this cycle if the cycle is associated with a reboot schedule.
    
    -- RebootScheduleUid (System.Int32?)
       Uid of the Reboot Schedule which triggered this cycle if the cycle is associated with a reboot schedule.
    
    -- RestrictToTag (System.String)
       An optional Tag which limits the reboot cycle to machines within the desktop group with the specified tag.
    
    -- StartTime (System.DateTime)
       Time of day at which this reboot cycle was started.
    
    -- State (Citrix.Broker.Admin.SDK.RebootCycleState)
       The execution state of this cycle.
    
    -- Uid (System.Int64)
       Unique ID of this reboot cycle.
    
    -- WarningDuration (System.Int32)
       Number of minutes to display the warning message for.
    
    -- WarningMessage (System.String)
       Warning message to display to users in active sessions prior to rebooting the machine.
    
    -- WarningRepeatInterval (System.Int32)
       Number of minutes to wait before showing the reboot warning message again.
    
    -- WarningTitle (System.String)
       Title of the warning message dialog.
    

## 相关命令

- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
- [Start-DesktopGroupRebootCycle](Start-DesktopGroupRebootCycle.html)
- [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets reboot cycles that have the specified Uid.                                                                                                                                                                                                                       | true  | false |                                                                                        |
| CatalogName            | Gets reboot cycles that relate to the named catalog.                                                                                                                                                                                                                  | false | false |                                                                                        |
| CatalogUid             | Gets reboot cycles that relate to the catalog with a particular Uid.                                                                                                                                                                                                  | false | false |                                                                                        |
| DesktopGroupName       | Gets reboot cycles that relate to the named desktop group.                                                                                                                                                                                                            | false | false |                                                                                        |
| DesktopGroupUid        | Gets reboot cycles that relate to the desktop group with a particular Uid.                                                                                                                                                                                            | false | false |                                                                                        |
| EndTime                | Gets reboot cycles that have the specified time at which the reboot cycle was completed, canceled or abandoned.                                                                                                                                                       | false | false |                                                                                        |
| MachinesCompleted      | Gets reboot cycles that have the specified count of machines successfully rebooted during the cycle.                                                                                                                                                                  | false | false |                                                                                        |
| MachinesFailed         | Gets reboot cycles that have the specified count of machines issued with reboot requests where either the request failed or the operation did not complete within the allowed time.                                                                                   | false | false |                                                                                        |
| MachinesInProgress     | Gets reboot cycles that have the specified count of machines issued with reboot requests but which have not yet completed the operation.                                                                                                                              | false | false |                                                                                        |
| MachinesPending        | Gets reboot cycles that have the specified count of outstanding machines to be rebooted during the cycle but on which processing has not yet started.                                                                                                                 | false | false |                                                                                        |
| MachinesSkipped        | Gets reboot cycles that have the specified count of machines scheduled for reboot during the cycle but which were not processed either because the cycle was canceled or abandoned or because the machine was unavailable for reboot processing throughout the cycle. | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                                                             | false | false |                                                                                        |
| RebootDuration         | Gets reboot cycles that have the specified approximate maximum duration in minutes over which the reboot cycle runs.                                                                                                                                                  | false | false |                                                                                        |
| RebootScheduleName     | Gets reboot cycles which were triggered by the named reboot schedule.                                                                                                                                                                                                 | false | false |                                                                                        |
| RebootScheduleUid      | Gets reboot cycles which were triggered by the reboot schedule with aparticular Uid.                                                                                                                                                                                  | false | false |                                                                                        |
| RestrictToTag          | An optional Tag which limits the reboot cycle to machines within the desktop group with the specified tag.                                                                                                                                                            | false | false |                                                                                        |
| StartTime              | Gets reboot cycles that have the specified time at which the reboot cycle started.                                                                                                                                                                                    | false | false |                                                                                        |
| 状态                     | Gets reboot cycles that have the specified overall state of the reboot cycle. Valid values are Initializing, Active, Completed, Canceled, and Abandoned.                                                                                                              | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                      | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                                                                                          | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                 | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                              | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                               | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                    | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.RebootCycle

Returns matching reboot cycles.

## 示例

### 示例 1

    C:\PS> Get-BrokerRebootCycle
    

Description  
\---\---\-----  
Enumerate all reboot cycles.

### 示例 2

    C:\PS> Get-BrokerRebootCycle -State Completed
    

Description  
\---\---\-----  
Enumerates all reboot cycles that have successfully completed.

### 示例 3

    C:\PS> Get-BrokerRebootCycle -DesktopGroupName CallCenter
    

Description  
\---\---\-----  
Enumerates all reboot cycles related to the desktop group named CallCenter.