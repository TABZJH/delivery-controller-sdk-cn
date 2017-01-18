# Remove-MonitorNotificationPolicyConditions

Remove conditions from the existing policy specified and returns the updated policy.

## 语法

    Remove-MonitorNotificationPolicyConditions -InputObject <MonitorNotificationPolicy> -Conditions <ConditionType[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-MonitorNotificationPolicyConditions -Uid <Int64> -Conditions <ConditionType[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove conditions from the existing policy specified and returns the updated policy.

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Specifies the policy object from which the conditions to be removed.                                                                                                   | true  | true (ByValue) |                                       |
| 条件           | Collection of condition types to be removed                                                                                                                            | true  | false          |                                       |
| UID          | Specifies the unique identifier of the policy from which the conditions to be removed.                                                                                 | true  | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the updated policy object

## 示例

### 示例 1

    Remove-MonitorNotificationPolicyConditions -Uid 100 -Conditions SessionsPeakconnectedCount
    

Description  
\---\---\-----  
Removes the condition SessionPeakconnectedCount from policy matching id 100