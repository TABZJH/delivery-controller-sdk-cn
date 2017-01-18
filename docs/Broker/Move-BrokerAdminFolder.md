# Move-BrokerAdminFolder

Moves a folder to another place in the hierarchy, optionally renaming it

## 语法

    Move-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Move-BrokerAdminFolder [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Move-BrokerAdminFolder cmdlet moves a folder for organising objects for administration purposes (for example, Applications) to another position in the hierarchy.

The following special characters are not allowed in the new FolderName: \ / ; : # . * ? = < > | \[ \] ( ) " ' `

## 相关命令

- [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
- [New-BrokerAdminFolder](New-BrokerAdminFolder.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The folder(s) to be moved                                                                                                                                                       | true  | true (ByValue)        |                                                                                        |
| 名称           | A pattern matching the names of folders to be moved                                                                                                                             | true  | true (ByPropertyName) |                                                                                        |
| 目标           | The destination folder the folder being moved should end up in                                                                                                                  | true  | false                 |                                                                                        |
| NewName      | The name the new folder should have in the destination folder                                                                                                                   | false | false                 |                                                                                        |
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

    Move-BrokerAdminFolder F1\XXX\ F2\
    

Description  
\---\---\-----  
Moves the folder called XXX within the folder F1\ to a new home in F2\

### 示例 2

    Move-BrokerAdminFolder F1\XXX\ F2\ -NewName YYY
    

Description  
\---\---\-----  
Moves the folder called XXX within the folder F1\ to a new home in F2\ renaming it to YYY in the process