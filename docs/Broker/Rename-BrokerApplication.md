# Rename-BrokerApplication

Renames an application.

## 语法

    Rename-BrokerApplication [-InputObject] <Application[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerApplication [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerApplication cmdlet changes the administrative name of an application. An application cannot have the same name as another application.

Renaming an application does not alter its published name. To change the name with which this application appears to end-users, set a new value for the PublishedName property using the Set-BrokerApplication cmdlet.

Renaming an application does not alter its BrowserName. If the BrowserName property also needs to be changed, use the Set-BrokerApplication cmdlet to modify it.

## 相关命令

- [New-BrokerApplication](New-BrokerApplication.html)
- [Set-BrokerApplication](Set-BrokerApplication.html)
- [Get-BrokerApplication](Get-BrokerApplication.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the application to rename.                                                                                                                                            | true  | true (ByValue)        | 空值                                                                                     |
| 名称           | Specifies the name of the application to rename.                                                                                                                                | true  | true (ByPropertyName) | 空值                                                                                     |
| NewName      | Specifies the new name for the application.                                                                                                                                     | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Application

You can pipe applications to Rename-BrokerApplication.

## 返回值

### None or Citrix.Broker.Admin.SDK.Application

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Application object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerApplication -Name "Old Name" -NewName "New Name"
    

Description  
\---\---\-----  
Renames the application with name "Old Name" to "New Name".

### 示例 2

    C:\PS> Get-BrokerApplication -Uid 1 | Rename-BrokerApplication -NewName "New Name" -PassThru
    

Description  
\---\---\-----  
Renames application with the Uid 1 to "New Name", showing the result.