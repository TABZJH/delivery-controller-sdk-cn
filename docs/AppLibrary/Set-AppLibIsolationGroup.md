# Set-AppLibIsolationGroup

Updates an isolation group in the library

## 语法

    Set-AppLibIsolationGroup [-IsolationGroupUid] <Int32> [-Name <String>] [-Description <String>] [-Version <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The isolation group will be updated with the new properties

## 相关命令

- [New-AppLibIsolationGroup](New-AppLibIsolationGroup.html)
- [Remove-AppLibIsolationGroup](Remove-AppLibIsolationGroup.html)
- [Set-AppLibIsolationGroupPackage](Set-AppLibIsolationGroupPackage.html)

## 参数

| 名称                | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group.                                                                                                    | true  | true (ByPropertyName) |                                       |
| 名称                | The name of the isolation group.                                                                                                                                       | false | true (ByPropertyName) |                                       |
| 说明                | The description of the isolation group.                                                                                                                                | false | true (ByPropertyName) |                                       |
| 版本                | The version of the isolation group.                                                                                                                                    | false | true (ByPropertyName) |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    Set-AppLibIsolationGroup -IsolationGroupUid 58  -Name "MyIsolationGroup" -Description "Some description here" -Version "1.0.0.1"
    

Description  
\---\---\-----  
Updates the specified isolation group with the new properties.