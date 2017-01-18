# Add-BrokerDesktopGroup

Associate Remote PC desktop groups with the specified Remote PC catalog.

## 语法

    Add-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-RemotePCCatalog <Catalog>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerDesktopGroup [-Name] <String> [-RemotePCCatalog <Catalog>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet forms relationships between Remote PC desktop groups and catalogs.

The Remote PC relationships are used by Remote PC automation to determine which desktop groups a machine in a particular Remote PC catalog can be published to. The assignment policy rules belonging to those desktop groups also determines the set of users that are allowed to be assigned to machines from the catalog.

## 相关命令

- [Remove-BrokerDesktopGroup](Remove-BrokerDesktopGroup.html)
- [Add-BrokerCatalog](Add-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)

## 参数

| 名称              | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject     | Specifies one or more Remote PC desktop groups to add to a Remote PC catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | true  | true (ByValue)        |                                                                                        |
| 名称              | Specifies the Remote PC desktop groups to add to a Remote PC catalog based on their name properties.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | true  | true (ByPropertyName) |                                                                                        |
| RemotePCCatalog | The Remote PC catalog which the desktop groups are to be added to. Specified by name, Uid or instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | false | true (ByValue)        |                                                                                        |
| 优先级             | Desktop group to catalog associations carry a priority number, where numerically lower values indicate a higher priority.  
The priority relative to other associations determines which desktop group Remote PC automation will move a qualifying unconfigured machine into when it registers. Priority also determines which desktop group a machine will be published to when a user is assigned to the machine by Remote PC automation.  
If a value is not supplied, then the desktop group association is automatically assigned a lower priority than any existing associations.  
If a priority value is specified that conflicts with an existing association's priority value, then the new association is inserted with that value and existing associations are renumbered upwards to accommodate it. | false | true (ByPropertyName) | See description                                                                        |
| LoggingId       | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| AdminAddress    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

The set of Remote PC desktop groups to be added to the catalog can be piped into this cmdlet.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Get-BrokerDesktopGroup -IsRemotePC $true | Add-BrokerDesktopGroup -RemotePCCatalog 42
    

Description  
\---\---\-----  
Add all Remote PC desktop groups to Remote PC catalog 42.

### 示例 2

    C:\PS> Add-BrokerDesktopGroup -Name *MyGroup* -RemotePCCatalog RPCCat
    

Description  
\---\---\-----  
Add desktop groups with names containing MyGroup to Remote PC catalog with name "RPCCat".