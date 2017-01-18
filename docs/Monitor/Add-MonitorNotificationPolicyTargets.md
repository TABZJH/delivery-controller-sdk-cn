# Add-MonitorNotificationPolicyTargets

Add targets to the existing policy specified and returns the updated policy

## 语法

    Add-MonitorNotificationPolicyTargets -InputObject <MonitorNotificationPolicy> -TargetIds <String[]> [-Scope <String>] [-TargetKind <TargetKind>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-MonitorNotificationPolicyTargets -Uid <Int64> -TargetIds <String[]> [-Scope <String>] [-TargetKind <TargetKind>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Add targets to the existing policy specified and returns the updated policy

## 相关命令

- [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
- [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
- [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)

## 参数

| 名称           | 说明                                                                                                                                                                           | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Specifies the policy object to which the targets to be added                                                                                                                 | true  | true (ByValue) |                                       |
| TargetIds    | Object reference to the array of target ids. Site GUID - for target type Site, DesktopGroup UUID - for DesktopGroup, RdsWorker target types, User SID - for User target type | true  | false          |                                       |
| UID          | Specifies the unique identifier of the policy to which the targets to be added                                                                                               | true  | false          |                                       |
| 作用域          | Description of the collection of target ids                                                                                                                                  | false | false          |                                       |
| TargetKind   | String representation of the target type enum. Possible values are Site DesktopGroup RdsWorker User                                                                          | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。       | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                   | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### MonitorNotificationPolicy

Returns the policy object

## 示例

### 示例 1

    $targetIds = @()
              $targetIds += "766cde70-3c69-4481-a658-4e11247ac70c"
    
              Add-MonitorNotificationPolicyTargets -Uid 100 -Scope "My Test Targets" -TargetKind Site -TargetIds $targetIds
    

Description  
\---\---\-----  
Add targets to the policy matching the id 100