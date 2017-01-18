# Rename-BrokerAdminFolder

Renames a folder

## 语法

    Rename-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerAdminFolder [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerAdminFolder cmdlet renames a folder for organising objects for administration purposes (for example, Applications).

The following special characters are not allowed in the new FolderName: \ / ; : # . * ? = < > | \[ \] ( ) " ' `

## 相关命令

- [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
- [New-BrokerAdminFolder](New-BrokerAdminFolder.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The folder(s) to be renamed                                                                                                                                                     | true  | true (ByValue)        |                                                                                        |
| 名称           | A pattern matching the names of folders to be renamed                                                                                                                           | true  | true (ByPropertyName) |                                                                                        |
| NewName      | The name the new folder(s) should have.                                                                                                                                         | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Depends on parameter

Parameters can be piped by property name.

## 返回值

### None or Citrix.Broker.Admin.SDK.AdminFolder

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AdminFolder object.

## 示例

### 示例 1

    Rename-BrokerAdminFolder F1\XXX\ YYY
    

Description  
\---\---\-----  
Renames the folder called XXX within the folder F1\ to YYY