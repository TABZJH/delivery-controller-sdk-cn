# Remove-BrokerDesktopGroup

Remove desktop groups from the system or remove them from a Remote PC catalog.

## 语法

    Remove-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-Force] [-RemotePCCatalog <Catalog>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerDesktopGroup [-Name] <String> [-Force] [-RemotePCCatalog <Catalog>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet has 2 functions:

o Remove desktop groups from the system. o Break Remote PC associations between desktop groups and a catalog.

The Remote PC relationships are used by Remote PC automation to determine which desktop groups a machine in a particular Remote PC catalog can be published to. The assignment policy rules belonging to those desktop groups also determines the set of users that are allowed to be assigned to machines from the catalog.

## 相关命令

- [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)
- [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
- [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup.html)
- [Add-BrokerDesktopGroup](Add-BrokerDesktopGroup.html)
- [Rename-BrokerDesktopGroup](Rename-BrokerDesktopGroup.html)
- [New-BrokerCatalog](New-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)

## 参数

| 名称              | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject     | Specifies the desktop groups to remove.                                                                                                                                         | true  | true (ByValue)        | 空值                                                                                     |
| 名称              | Specifies the name of the desktop group to remove.                                                                                                                              | true  | true (ByPropertyName) | 空值                                                                                     |
| Force           | Remove desktop groups even if there are active sessions.                                                                                                                        | false | false                 | false                                                                                  |
| RemotePCCatalog | When this parameter is specified, Remote PC desktop groups are removed from the specified Remote PC catalog.                                                                    | false | true (ByValue)        | 空值                                                                                     |
| LoggingId       | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

You can pipe desktop groups to Remove-BrokerDesktopGroup.

## 返回值

### 无

## Notes If a desktop group contains desktops when it is removed, these desktops are also removed (but the underlying broker machine remains).  
A desktop group that still has active sessions cannot be removed unless the -Force switch is used.

## 示例

### 示例 1

    C:\PS> Remove-BrokerDesktopGroup EMEA*
    

Description  
\---\---\-----  
Remove all desktop groups with names starting with "EMEA".

### 示例 2

    C:\PS> Get-BrokerDesktopGroup -Enabled $false | Remove-BrokerDesktopGroup -Force
    

Description  
\---\---\-----  
Remove all desktops that are currently disabled even if there are active sessions.

### 示例 3

    C:\PS> Get-BrokerDesktopGroup -RemotePCCatalogUid 42 | Remove-BrokerDesktopGroup -RemotePCCatalog 42
    

Description  
\---\---\-----  
Remove all the Remote PC desktop groups that are associated with catalog 42. Note that this only breaks the Remote PC relationships and does not delete the desktop groups.