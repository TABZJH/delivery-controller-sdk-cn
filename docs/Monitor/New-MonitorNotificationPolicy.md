# New-MonitorNotificationPolicy

Returns a new MonitorNotificationPolicy object

## 语法

    New-MonitorNotificationPolicy -Name <String> [-Description <String>] [-Webhook <String>] [-IsSnmpEnabled <Boolean>] [-Enabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a new policy instance using the specified parameters

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称            | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 名称            | Name of policy to create                                                                                                                                               | true  | false |                                       |
| 说明            | Description of policy to create                                                                                                                                        | false | false |                                       |
| Webhook       | Webhook URL of policy to create                                                                                                                                        | false | false |                                       |
| IsSnmpEnabled | boolean value representing if SNMP is enabled for new Policy                                                                                                           | false | false |                                       |
| 已启用           | Boolean paramter indicating the enabled state of the policy. true – Enabled, false – Disabled                                                                          | false | false |                                       |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the collection of policy objects created

## 示例

### 示例 1

    New-MonitorNotificationPolicy -Name "Policy1" -Description "Policy Description" -Enabled $true
    

Description  
\---\---\-----  
Creates session policy and persist the data into database