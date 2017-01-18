# Move-BrokerApplication

Move a published application from one admin folder to another

## 语法

    Move-BrokerApplication [-InputObject] <Application[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Move-BrokerApplication [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Move-BrokerApplication cmdlet moves a published application from one place to another in the tree of admin folders, optionally renaming it in the process (if you only want to change the name of the application for administrative purposes and not its location in the tree, use the Rename-BrokerApplication cmdlet).

The location and name of a published application in this sense is only of interest to the administrator, changes do not affect the end-user experience.

## 相关命令

- [New-BrokerApplication](New-BrokerApplication.html)
- [Add-BrokerApplication](Add-BrokerApplication.html)
- [Get-BrokerApplication](Get-BrokerApplication.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)
- [Rename-BrokerApplication](Rename-BrokerApplication.html)
- [Set-BrokerApplication](Set-BrokerApplication.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The application(s) to be moved                                                                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 名称           | The application(s) to be moved                                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| 目标           | The destination location within the admin folder hierarchy                                                                                                                      | true  | false                 |                                                                                        |
| NewName      | The new name of the application in its new destination                                                                                                                          | false | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Application

You can pipe applications to Move-BrokerApplication.

## 返回值

### None or Citrix.Broker.Admin.SDK.Application

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Application object.

## 示例

### 示例 1

    C:\PS> Move-BrokerApplication -Name 'App1' -Destination 'F1\'
    

Description  
\---\---\-----  
Moves the application in the root folder called "App1" to the folder "F1\".

### 示例 2

    C:\PS> Move-BrokerApplication 'F1\App1' 'F2\' -NewName 'Application1'
    

Description  
\---\---\-----  
Moves the application in folder "F1" called "App1" to the folder "F2\", renaming it to "Application1" in the process.