# Get-MonitorNotificationPolicy

Returns a list of MonitorNotificationPolicy objects matching the specified parameters

## 语法

    Get-MonitorNotificationPolicy [-Uid <Int64>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-MonitorNotificationPolicy -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a list of MonitorNotificationPolicy objects matching the specified parameters

## 相关命令

- [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 名称           | Returns all of the policies contains the specified name.                                                                                                               | true  | false |                                       |
| UID          | Returns the policy with the specified id.                                                                                                                              | false | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Collections.Generic.ICollection`1[[Citrix.Monitor.Sdk.PowerShell.MonitorNotificationPolicy, Citrix.Monitor.PowerShellSnapIn, Version=7.7.0.95, Culture=neutral, PublicKeyToken=e6a2b8abcb991548]]

Returns a collection of policies.

## 示例

### 示例 1

    Get-MonitorNotificationPolicy -Id 1
    

Description  
\---\---\-----  
Returns the policy object having the Id equals to 1

### 示例 2

    Get-MonitorNotificationPolicy -Name 'Server OS Policy'
    

Description  
\---\---\-----  
Returns the policy object having the name contains 'Server OS Policy'