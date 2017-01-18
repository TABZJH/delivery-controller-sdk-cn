# Rename-BrokerDesktopGroup

Renames a desktop group.

## 语法

    Rename-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerDesktopGroup [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerDesktopGroup cmdlet changes the name of a desktop group. A desktop group cannot have the same name as another desktop group.

## 相关命令

- [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)
- [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
- [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup.html)
- [Remove-BrokerDesktopGroup](Remove-BrokerDesktopGroup.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the desktop group to rename.                                                                                                                                          | true  | true (ByValue)        | 空值                                                                                     |
| 名称           | Specifies the name of the desktop group to rename.                                                                                                                              | true  | true (ByPropertyName) | 空值                                                                                     |
| NewName      | Specifies the new name that the desktop group will have.                                                                                                                        | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

You can pipe desktop groups to Rename-BrokerDesktopGroup.

## 返回值

### None or Citrix.Broker.Admin.SDK.DesktopGroup

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.DesktopGroup object.## Notes Renaming a desktop group does not alter its published name. If you need to change the name with which this desktop group appears to end-users, set a new value for the PublishedName property using the Set-BrokerDesktopGroup cmdlet.

## 示例

### 示例 1

    C:\PS> Rename-BrokerDesktopGroup -Name "Old Name" -NewName "New Name"
    

Description  
\---\---\-----  
Renames desktop group with the name "Old Name" to "New Name".

### 示例 2

    C:\PS> Get-BrokerDesktopGroup -Uid 1 | Rename-BrokerDesktopGroup -NewName "New Name" -PassThru
    

Description  
\---\---\-----  
Renames desktop group with the Uid 1 to "New Name", showing the result.