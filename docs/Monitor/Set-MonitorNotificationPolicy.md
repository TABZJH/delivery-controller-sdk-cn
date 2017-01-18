# Set-MonitorNotificationPolicy

Set/Modify MonitorNotificationPolicy object

## 语法

    Set-MonitorNotificationPolicy -InputObject <MonitorNotificationPolicy> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-MonitorNotificationPolicy -Uid <Int64> [-Name <String>] [-Description <String>] [-Webhook <String>] [-IsSnmpEnabled <Boolean>] [-Enabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a new policy instance using the specified parameters

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称            | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| InputObject   | Specifies the new policy object to adjust.                                                                                                                             | true  | false |                                       |
| UID           | Unique identifier for policy to bet set.                                                                                                                               | true  | false |                                       |
| 名称            | New Name of the policy.                                                                                                                                                | false | false |                                       |
| 说明            | String value representing the new Policy description                                                                                                                   | false | false |                                       |
| Webhook       | String value representing the new Policy webhook                                                                                                                       | false | false |                                       |
| IsSnmpEnabled | boolean value representing if SNMP is enabled for new Policy                                                                                                           | false | false |                                       |
| 已启用           | Boolean paramter indicating the enabled state of the policy. true – Enabled, false – Disabled                                                                          | false | false |                                       |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the modified policy

## 示例

### 示例 1

    Set-MonitorNotificationPolicy -Id 1 -Enable
    

Description  
\---\---\-----  
Enable the policy with the id 1

### 示例 2

    $policy = Get-MonitorNotificationPolicy -Uid 1
    
              $policy.EmailAddresses += "newemail@abc.com"
    
              Set-MonitorNotificationPolicy -InputObject $policy
    

Description  
\---\---\-----  
Update the policy with the id 1 to add new email address

### 示例 3

    $policy = Get-MonitorNotificationPolicy -Uid 1
              $policy.TargetIds += "766cde70-3c69-4481-a658-4e11247ac70c"
    
              $Policy = Set-MonitorNotificationPolicy -Id 1 -InputObject $policy
    

Description  
\---\---\-----  
Update the policy with the id 1 to add new target value