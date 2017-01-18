# Add-MonitorNotificationPolicyCondition

Add conditions to the existing policy specified and returns the updated policy.

## 语法

    Add-MonitorNotificationPolicyCondition -InputObject <MonitorNotificationPolicy> [-AlertThreshold <Int32>] [-AlarmThreshold <Int32>] [-AlertRenotification <TimeSpan>] [-AlarmRenotification <TimeSpan>] [-SearchWindow <TimeSpan>] [-AlertConditionPersistenceInterval <TimeSpan>] [-AlarmConditionPersistenceInterval <TimeSpan>] [-Granularity <TimeSpan>] [-AlertSampleCount <Int32>] [-AlarmSampleCount <Int32>] [-AlertSamplePercent <Int32>] [-AlarmSamplePercent <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-MonitorNotificationPolicyCondition -Uid <Int64> -ConditionType <ConditionType> [-AlertThreshold <Int32>] [-AlarmThreshold <Int32>] [-AlertRenotification <TimeSpan>] [-AlarmRenotification <TimeSpan>] [-SearchWindow <TimeSpan>] [-AlertConditionPersistenceInterval <TimeSpan>] [-AlarmConditionPersistenceInterval <TimeSpan>] [-Granularity <TimeSpan>] [-AlertSampleCount <Int32>] [-AlarmSampleCount <Int32>] [-AlertSamplePercent <Int32>] [-AlarmSamplePercent <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Add conditions to the existing policy specified and returns the updated policy.

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称                                | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 是否必需？ | 管道输入           | 默认值                                   |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject                       | Specifies the policy object to which the conditions to be added                                                                                                                                                                                                                                                                                                                                                                                           | true  | true (ByValue) |                                       |
| UID                               | Specifies the unique identifier of the policy to which the conditions to be added                                                                                                                                                                                                                                                                                                                                                                         | true  | false          |                                       |
| ConditionType                     | Type of the condition using a text string converted to an enum value Possible values are SessionsConcurrentCount SessionsPeakconnectedCount SessionsPeakDisconnectedCount AverageLogonDuration RDSLoadEvaluator ConnectionFailuresRate ConnectionFailuresCount FailedServerMachineCount FailedDesktopMachineCount LogonDuration IcaRoundtripTime IcaRoundtripTimeAverage IcaRoundtripTimeSessionCount IcaRoundtripTimeSessionPercent MemoryUsage CpuUsage | true  | false          |                                       |
| AlertThreshold                    | Threshold value at which the warning notification will be triggered                                                                                                                                                                                                                                                                                                                                                                                       | false | false          |                                       |
| AlarmThreshold                    | Threshold value at which the critical notification will be triggered                                                                                                                                                                                                                                                                                                                                                                                      | false | false          |                                       |
| AlertRenotification               | Duration after which the warning notification will be re-triggered                                                                                                                                                                                                                                                                                                                                                                                        | false | false          |                                       |
| AlarmRenotification               | Duration after which the critical notification will be re-triggered                                                                                                                                                                                                                                                                                                                                                                                       | false | false          |                                       |
| SearchWindow                      | The amount of time the condition query will look back for the matching record when it examines the data.                                                                                                                                                                                                                                                                                                                                                  | false | false          |                                       |
| AlertConditionPersistenceInterval | The amount of time the condition query will look back to check if the alert condition was persisted.                                                                                                                                                                                                                                                                                                                                                      | false | false          |                                       |
| AlarmConditionPersistenceInterval | The amount of time the condition query will look back to check if the alarm condition was persisted.                                                                                                                                                                                                                                                                                                                                                      | false | false          |                                       |
| Granularity                       | Defines the granularity of the rate in seconds. This value is applicable for ‘ConnectionFailuresRate’ condition.                                                                                                                                                                                                                                                                                                                                          | false | false          |                                       |
| AlertSampleCount                  | Defines the count of instances to measure before raising the warning notification. This value is applicable for ICA RTT (Session Count) condition.                                                                                                                                                                                                                                                                                                        | false | false          |                                       |
| AlarmSampleCount                  | Defines the count of instances to measure before raising the critical notification. This value is applicable for ICA RTT (Session Count) condition.                                                                                                                                                                                                                                                                                                       | false | false          |                                       |
| AlertSamplePercent                | Defines the percentage of instances to measure before raising the warning notification. This value is applicable for ICA RTT (Session Percent) condition.                                                                                                                                                                                                                                                                                                 | false | false          |                                       |
| AlarmSamplePercent                | Defines the percentage of instances to measure before raising the critical notification. This value is applicable for ICA RTT (Session Percent) condition.                                                                                                                                                                                                                                                                                                | false | false          |                                       |
| LoggingId                         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                    | false | false          |                                       |
| AdminAddress                      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                                | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the updated policy object

## 示例

### 示例 1

    $timeSpan = New-TimeSpan -Seconds 30
              $alertThreshold = 10
              $alarmThreshold = 20
    
              Add-MonitorNotificationPolicyCondition -Uid 100 -ConditionType SessionsConcurrentCount -AlertThreshold $alertThreshold -AlarmThreshold $alarmThreshold  -AlertRenotification $timeSpan -AlarmRenotification $timeSpan
    

Description  
\---\---\-----  
Add SessionsConcurrentCount condition to the policy matching the id 100