# New-AppLibIsolationGroup

Adds a new isolation group into the library

## 语法

    New-AppLibIsolationGroup [-LibraryUid] <Int32> [-Name] <String> [-Description <String>] [-Version <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The isolation group will be added to the library

## 相关命令

- [Remove-AppLibIsolationGroup](Remove-AppLibIsolationGroup.html)
- [Set-AppLibIsolationGroup](Set-AppLibIsolationGroup.html)
- [Set-AppLibIsolationGroupPackage](Set-AppLibIsolationGroupPackage.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| LibraryUid   | The unique identifier of the library to which the isolation group will be added                                                                                        | true  | true (ByPropertyName) |                                       |
| 名称           | The name of the isolation group.                                                                                                                                       | true  | false                 |                                       |
| 说明           | The description of the isolation group.                                                                                                                                | false | false                 |                                       |
| 版本           | The version of the isolation group.                                                                                                                                    | false | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.IsolationGroup

An object representing the details of the new isolation group.

## 示例

### 示例 1

    Add-AppLibIsolationGroup -LibraryUid 1 -Name "MyIsolationGroup" -Description "Some description here" -Version "1.0.0.1"
    

Description  
\---\---\-----  
Adds the isolation group to the specified library