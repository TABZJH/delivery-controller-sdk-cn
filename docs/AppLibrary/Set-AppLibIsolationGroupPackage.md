# Set-AppLibIsolationGroupPackage

Updates an App-V package's settings in an Isolation Group.

## 语法

    Set-AppLibIsolationGroupPackage [-IsolationGroupUid] <Int32> -AppVPackageUid <Int32> -OrderNumber <Int32> -ExplicitInclusion <Boolean> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Updates an App-V package's settings in the specified Isolation Group.

## 相关命令

- [Remove-AppLibIsolationGroupPackage](Remove-AppLibIsolationGroupPackage.html)

## 参数

| 名称                | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IsolationGroupUid | 要包含包的隔离组的 AppLibrary 内部唯一标识符。                                                                                                                                          | true  | true (ByPropertyName) |                                       |
| AppVPackageUid    | App-V 包的 AppLibrary 内部唯一标识符。                                                                                                                                           | true  | true (ByPropertyName) |                                       |
| OrderNumber       | 隔离组中的排序编号。                                                                                                                                                             | true  | true (ByPropertyName) |                                       |
| ExplicitInclusion | 指示包是否明确包括在交付组中。                                                                                                                                                        | true  | true (ByPropertyName) |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 无

## 示例

### 示例 1

    Set-AppLibIsolationGroupPackage -IsolationGroupUid 4 -AppVPackageUid 15 -OrderNumber 1 -ExplicitInclusion True
    

Description  
\---\---\-----  
Updates the App-V package with the unique identifier in the specified isolation group.