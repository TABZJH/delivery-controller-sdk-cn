# New-BrokerAdminFolder

Creates a new admin folder.

## 语法

    New-BrokerAdminFolder [-FolderName] <String> [-ParentFolder <AdminFolder>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerAdminFolder cmdlet creates a new folder for organising objects for administration purposes (for example, Applications).

New-BrokerAdminFolder creates the folder object and optionally places it within an existing admin folder if required.

The following special characters are not allowed in the FolderName: \ / ; : # . * ? = < > | \[ \] ( ) " ' `

## 相关命令

- [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
- [Remove-BrokerAdminFolder](Remove-BrokerAdminFolder.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| FolderName   | The simple name of the new folder within its parent (if any)                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| ParentFolder | The name or UID of the parent folder (if any)                                                                                                                                   | false | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Depends on parameter

Parameters can be piped by property name.

## 返回值

### Citrix.Broker.Admin.SDK.AdminFolder

The new admin folder.

## 示例

### 示例 1

    New-BrokerAdminFolder F1
    

Description  
\---\---\-----  
Creates an admin folder called F1 under the root folder (i.e. F1\)

### 示例 2

    New-BrokerAdminFolder F2 -AdminFolder F1\
    

Description  
\---\---\-----  
Creates an admin folder called F2 under the folder F1\ (i.e. F1\F2\)