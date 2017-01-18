# Remove-BrokerAdminFolder

Removes an admin folder.

## 语法

    Remove-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerAdminFolder [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerAdminFolder cmdlet removes an existing admin folder.

Remove-BrokerAdminFolder will not remove a folder if it contains any other objects (e.g. sub-folders or applications).

## 相关命令

- [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
- [New-BrokerAdminFolder](New-BrokerAdminFolder.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Identifies the folder to remove                                                                                                                                                 | true  | true (ByValue)        |                                                                                        |
| 名称           | The name pattern of folder(s) to remove                                                                                                                                         | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.AdminFolder

The admin folder objects can be specified as input.

## 返回值

### 无

This cmdlet does not return any output.

## 示例

### 示例 1

    Remove-BrokerAdminFolder F1\F2\
    

Description  
\---\---\-----  
Removes the folder called F2 within the folder F1\