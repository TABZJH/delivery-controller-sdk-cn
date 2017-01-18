# Set-MonitorConfiguration

设置监控服务使用的配置设置。

## 语法

    Set-MonitorConfiguration [-GroomSessionsRetentionDays <Int32>] [-GroomFailuresRetentionDays <Int32>] [-GroomLoadIndexesRetentionDays <Int32>] [-GroomDeletedRetentionDays <Int32>] [-GroomSummariesRetentionDays <Int32>] [-GroomMachineHotfixLogRetentionDays <Int32>] [-GroomMinuteRetentionDays <Int32>] [-GroomHourlyRetentionDays <Int32>] [-DataCollectionEnabled <Boolean>] [-FullPollStartHour <Int32>] [-ResolutionPollTimeHours <Int32>] [-SyncPollTimeHours <Int32>] [-DetailedSqlOutputEnabled <Boolean>] [-MonitorQueryTimeoutSeconds <Int32>] [-CollectHotfixDataEnabled <Boolean>] [-GroomApplicationInstanceRetentionDays <Int32>] [-GroomNotificationLogRetentionDays <Int32>] [-GroomResourceUsageRawDataRetentionDays <Int32>] [-GroomResourceUsageMinuteDataRetentionDays <Int32>] [-GroomResourceUsageHourDataRetentionDays <Int32>] [-GroomResourceUsageDayDataRetentionDays <Int32>] [-GroomProcessUsageRawDataRetentionDays <Int32>] [-GroomProcessUsageMinuteDataRetentionDays <Int32>] [-GroomProcessUsageHourDataRetentionDays <Int32>] [-GroomProcessUsageDayDataRetentionDays <Int32>] [-GroomSessionMetricsDataRetentionDays <Int32>] [-EnableDayLevelGranularityProcessUtilization <Boolean>] [-EnableHourLevelGranularityProcessUtilization <Boolean>] [-EnableMinLevelGranularityProcessUtilization <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the configuration settings used by the Monitor Service. Use these settings to modify the behavior of the service.

使用此命令无需配置数据库连接。

## 相关命令

- [Get-MonitorConfiguration](Get-MonitorConfiguration.html)

## 参数

| 名称                                           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                     |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | --------------------------------------- |
| GroomSessionsRetentionDays                   | 确定会话终止后保留会话和连接记录的天数。                                                                                                                                                   | false | false | 对于非 Platinum 版本为 7；对于 Platinum 为 90。    |
| GroomFailuresRetentionDays                   | 确定创建 MachineFailureLog 和 ConnectionFailureLog 记录后保留这些记录的天数。                                                                                                            | false | false | 对于非 Platinum 版本为 7；对于 Platinum 为 90。    |
| GroomLoadIndexesRetentionDays                | 确定创建 LoadIndex 记录后保留这些记录的天数.                                                                                                                                           | false | false | 对于非 Platinum 版本为 7；对于 Platinum 为 90。    |
| GroomDeletedRetentionDays                    | 确定 LifecycleState 为“Deleted”的 Machine、Catalog、DesktopGroup 和 Hypervisor 条目的保留天数。 此操作还会删除任何相关的 Session、Connection、Summary、Failure 或 LoadIndex 记录。                       | false | false | 对于非 Platinum 版本为 7；对于 Platinum 为 90。    |
| GroomSummariesRetentionDays                  | 确定保留 DesktopGroupSummary、FailureLogSummary 和 LoadIndexSummary 记录的天数，以天为粒度。                                                                                             | false | false | 对于非 Platinum 版本为 7；对于 Platinum 为 90。    |
| GroomMachineHotfixLogRetentionDays           | 确定保留 Machine-Hotfix 历史记录的天数，以天为粒度。                                                                                                                                     | false | false | 90                                      |
| GroomMinuteRetentionDays                     | 确定保留详细数据的天数。                                                                                                                                                           | false | false | 3                                       |
| GroomHourlyRetentionDays                     | Determines how many days to keep hourly data.                                                                                                                          | false | false | 7 for non-platinum, 32 for platinum.    |
| DataCollectionEnabled                        | Starts / stops data collection. Stopping data collection turns off polling, and does not persist operational event data to the database.                               | false | false | True                                    |
| FullPollStartHour                            | 一天中全面轮询应开始的时间（小时）。                                                                                                                                                     | false | false |                                         |
| ResolutionPollTimeHours                      | 解析轮询工作线程的开始时间。                                                                                                                                                         | false | false |                                         |
| SyncPollTimeHours                            | 同步轮询工作线程的开始时间。                                                                                                                                                         | false | false |                                         |
| DetailedSqlOutputEnabled                     | 确定是否应启用 SqlLog 以便向 CDF 跟踪发送 SQL 语句                                                                                                                                     | false | false | False                                   |
| MonitorQueryTimeoutSeconds                   | Determines the maximum time Monitoring Service will wait for the database query execution                                                                              | false | false | 300                                     |
| CollectHotfixDataEnabled                     | 此设置确定是将修补程序清单数据收集起来并存储在数据库中还是将其丢弃。                                                                                                                                     | false | false |                                         |
| GroomApplicationInstanceRetentionDays        | Determines how many days to keep the history of application instances.                                                                                                 | false | false | 0 for non-platinum, 90 for platinum.    |
| GroomNotificationLogRetentionDays            | FIXME                                                                                                                                                                  | false | false |                                         |
| GroomResourceUsageRawDataRetentionDays       | Determines how many days to keep Resource Utilization data.                                                                                                            | false | false | 1 for non-platinum and platinum.        |
| GroomResourceUsageMinuteDataRetentionDays    | Determines how many days to keep Resource Utilization summary minute data.                                                                                             | false | false | 7 for non-platinum and platinum.        |
| GroomResourceUsageHourDataRetentionDays      | Determines how many days to keep Resource Utilization summary hour data.                                                                                               | false | false | 7 for non-platinum and 30 for platinum. |
| GroomResourceUsageDayDataRetentionDays       | Determines how many days to keep Resource Utilization summary day data.                                                                                                | false | false | 7 for non-platinum and 90 for platinum. |
| GroomProcessUsageRawDataRetentionDays        | Determines how many days to keep Process Utilization data.                                                                                                             | false | false | 1 for non-platinum and platinum.        |
| GroomProcessUsageMinuteDataRetentionDays     | Determines how many days to keep Process Utilization summary minute data.                                                                                              | false | false | 3 for non-platinum and platinum.        |
| GroomProcessUsageHourDataRetentionDays       | Determines how many days to keep Process Utilization summary hour data.                                                                                                | false | false | 7 for non-platinum and platinum.        |
| GroomProcessUsageDayDataRetentionDays        | Determines how many days to keep Process Utilization summary day data.                                                                                                 | false | false | 7 for non-platinum and 30 for platinum. |
| GroomSessionMetricsDataRetentionDays         | Determines how many days to keep SessionMetrics data.                                                                                                                  | false | false | 7 for non-platinum and platinum.        |
| EnableDayLevelGranularityProcessUtilization  | This setting is used to determine to enable or disable Day Level granularity for Process Data.                                                                         | false | false |                                         |
| EnableHourLevelGranularityProcessUtilization | This setting is used to determine to enable or disable Hour Level granularity for Process Data.                                                                        | false | false |                                         |
| EnableMinLevelGranularityProcessUtilization  | This setting is used to determine to enable or disable Minute Level granularity for Process Data.                                                                      | false | false |                                         |
| LoggingId                                    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                         |
| AdminAddress                                 | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。   |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS>Set-MonitorConfiguration -GroomSessionsRetentionDays 5 -GroomFailuresRetentionDays 4 ...
    

Description  
\---\---\-----  
Updates the settings in the site database with the newly specified values.