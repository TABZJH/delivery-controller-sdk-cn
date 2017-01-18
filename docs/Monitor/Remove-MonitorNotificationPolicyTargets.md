# Remove-MonitorNotificationPolicyTargets

Remove targets from the existing policy specified and returns the updated policy.

## 语法

    Remove-MonitorNotificationPolicyTargets -InputObject <MonitorNotificationPolicy> -TargetIds <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-MonitorNotificationPolicyTargets -Uid <Int64> -TargetIds <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove targets from the existing policy specified and returns the updated policy.

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Specifies the policy object from the targets to be removed                                                                                                             | true  | true (ByValue) |                                       |
| TargetIds    | Object reference to the array of target ids. Site GUID - for target type Site DesktopGroup UUID - for DesktopGroup, RdsWorker target types                             | true  | false          |                                       |
| UID          | Specifies the unique identifier of the policy from the targets to be removed                                                                                           | true  | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the policy object

## 示例

### 示例 1

    $targetIds = @()
              $targetIds += "766cde70-3c69-4481-a658-4e11247ac70d"
    
              Remove-MonitorNotificationPolicyTargets -Uid 100  -TargetIds $targetIds
    

Description  
\---\---\-----  
Removes the targets from policy matching id 100