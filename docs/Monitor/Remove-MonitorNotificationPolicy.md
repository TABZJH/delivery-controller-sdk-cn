# Remove-MonitorNotificationPolicy

Removes persisted policy from the database by marking them as deleted

## 语法

    Remove-MonitorNotificationPolicy [-InputObject <MonitorNotificationPolicy[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-MonitorNotificationPolicy [-Uid <Int64[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes the policy object from database by marking them as deleted and disable all the condtions associated with that

## 相关命令

- [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy.html)
- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationRulePolicy](Set-MonitorNotificationRulePolicy.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Removes all of the instances with the id matching in the specified policy objects                                                                                      | false | true (ByValue) |                                       |
| UID          | Removes all of the instances with the specified ids. If any of the ids are invalid, an exception is thrown.                                                            | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Return success if all operations are succeeded

Return success if all operations are succeeded. An exception is thrown otherwise

## 示例

### 示例 1

    Remove-MonitorNotificationPolicy -Id 1
    

Description  
\---\---\-----  
Removes the policy with id 1

### 示例 2

    Remove-MonitorNotificationPolicy -InputObject $policy
    

Description  
\---\---\-----  
Removes the policy with id matching the policy object specified