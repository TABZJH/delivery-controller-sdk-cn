# Get-BrokerRebootScheduleV2

Gets one or more reboot schedules.

## 语法

    Get-BrokerRebootScheduleV2 [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerRebootScheduleV2 [[-Name] <String>] [-Active <Boolean>] [-Day <RebootScheduleDays>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-MetadataKey <String>] [-Metadata <String>] [-RebootDuration <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-WarningRepeatInterval <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerRebootScheduleV2 cmdlet is used to enumerate desktop group reboot schedules that match all of the supplied criteria.

A reboot schedule can be configured to cause all of the machines in a desktop group to be rebooted at a particular time each day or each week, with the reboot of the individual machines spread out over the duration of the whole reboot cycle. A specific warning message can be configured to be displayed to users who are running sessions on the machines being rebooted.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerRebootScheduleV2 Object The reboot schedule object returned represents a regularly scheduled reboot of machines in a desktop group.

    -- Active (System.Boolean)
       True if there is an active reboot cycle for this schedule, false otherwise.
    
    -- Day (Citrix.Broker.Admin.SDK.RebootScheduleDays)
       When the frequency is weekly, day of the week on which the schedule reboot starts.
    
    -- Description (System.String)
       An optional description for the reboot schedule.
    
    -- DesktopGroupName (System.String)
       Name of the desktop group rebooted by this schedule.
    
    -- DesktopGroupUid (System.Int32)
       Uid of the desktop group rebooted by this schedule.
    
    -- Enabled (System.Boolean)
       True if this schedule is currently enabled, false otherwise.
    
    -- Frequency (Citrix.Broker.Admin.SDK.RebootScheduleFrequency)
       Whether the schedule runs daily or weekly.
    
    -- MetadataKeys (System.String[])
       All key names of metadata items associated with this application.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this application.
    
    -- Name (System.String)
       Name of the reboot schedule.
    
    -- RebootDuration (System.Int32)
       Approximate maximum number of minutes over which the scheduled reboot cycle runs.
    
    -- RestrictToTag (System.String)
       If set the reboot schedule only applies to machines in the desktop group with the specified tag.
    
    -- StartTime (System.TimeSpan)
       Time of day at which the scheduled reboot cycle starts.
    
    -- Uid (System.Int32)
       Uid of the reboot schedule.
    
    -- WarningDuration (System.Int32)
       Number of minutes to display the warning message for.
    
    -- WarningMessage (System.String)
       Warning message to display to users in active sessions prior to rebooting the machine.
    
    -- WarningRepeatInterval (System.Int32)
       Number of minutes to wait before displaying the warning message again.
    
    -- WarningTitle (System.String)
       Title of the warning message dialog.
    

## 相关命令

- [Set-BrokerRebootScheduleV2](Set-BrokerRebootScheduleV2.html)
- [New-BrokerRebootScheduleV2](New-BrokerRebootScheduleV2.html)
- [Remove-BrokerRebootScheduleV2](Remove-BrokerRebootScheduleV2.html)
- [Rename-BrokerRebootScheduleV2](Rename-BrokerRebootScheduleV2.html)
- [Get-BrokerRebootCycle](Get-BrokerRebootCycle.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                         | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets the reboot schedule with the specified Uid.                                                                                                                                                           | true  | false |                                                                                        |
| 名称                     | Gets the reboot schedule with the specified name.                                                                                                                                                          | false | false |                                                                                        |
| 活动                     | Gets desktop group reboot schedules according to whether they are currently active or not. A schedule is active if there is a reboot cycle currently running that was started as a result of the schedule. | false | false |                                                                                        |
| 天                      | Gets the reboot schedules set to run on the specified day (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday).                                                                         | false | false |                                                                                        |
| DesktopGroupName       | Gets the reboot schedules for the desktop group having this name.                                                                                                                                          | false | false |                                                                                        |
| DesktopGroupUid        | Gets the reboot schedules for the desktop group having this Uid.                                                                                                                                           | false | false |                                                                                        |
| 已启用                    | Gets the reboot schedules with the specified Enabled value.                                                                                                                                                | false | false |                                                                                        |
| 频率                     | Gets the reboot schedules with the specified frequency (either Weekly or Daily).                                                                                                                           | false | false |                                                                                        |
| MetadataKey            | All key names of metadata items associated with this application.                                                                                                                                          | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                  | false | false |                                                                                        |
| RebootDuration         | Gets the reboot schedules with the specified duration.                                                                                                                                                     | false | false |                                                                                        |
| RestrictToTag          | Gets the reboot schedules with the specified tag.                                                                                                                                                          | false | false |                                                                                        |
| StartTime              | Gets the reboot schedules with the specified start time (HH:MM).                                                                                                                                           | false | false |                                                                                        |
| WarningRepeatInterval  | Gets the reboot schedules with the specified warning repeat interval.                                                                                                                                      | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                           | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                               | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                      | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                   | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                    | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                     | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                         | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.RebootScheduleV2

Returns matching reboot schedules.

## 示例

### 示例 1

    C:\PS> Get-BrokerRebootScheduleV2
    

Description  
\---\---\-----  
Enumerates all of the reboot schedules.

### 示例 2

    C:\PS> Get-BrokerRebootScheduleV2 -Enabled $false -Frequency Daily
    

Description  
\---\---\-----  
Enumerates all disabled reboot schedules that are scheduled to run daily.

### 示例 3

    C:\PS> Get-BrokerRebootScheduleV2 -DesktopGroupUid 11
    

Description  
\---\---\-----  
Returns the reboot schedules for the desktop group having the Uid 11.