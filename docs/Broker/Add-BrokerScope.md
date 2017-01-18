# Add-BrokerScope

Add the specified catalog/desktop group to the given scope(s).

## 语法

    Add-BrokerScope [-InputObject] <Scope[]> [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Add-BrokerScope cmdlet is used to associate a scopeable object with the given scope(s). A scopeable object is one of: o a catalog o a desktop group o an application group

To add a scopeable object to a scope you need permission to change the scopes of the scopeable object and permission to add objects to all of the scopes you have specified.

If the scopeable object is already in any scope supplied, that scope will be silently ignored.

## 相关命令

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies the scope(s) to add the object to. Each can take the form of either the string form of the scope's GUID or its name.                                                  | true  | true (ByValue) |                                                                                        |
| ApplicationGroup | Specifies the application group to be added. This can take the form of an existing application group object, an application group Uid or name.                                  | false | true (ByValue) |                                                                                        |
| 目录               | Specifies the catalog object to be added. This can take the form of an existing catalog object, a catalog Uid or name.                                                          | false | true (ByValue) |                                                                                        |
| DesktopGroup     | Specifies the desktop group object to be added. This can take the form of an existing desktop group object, a desktop group Uid or name.                                        | false | true (ByValue) |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Scope

You can pipe scopes to Add-BrokerScope.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-BrokerScope Sales –DesktopGroup 27
    

Description  
\---\---\-----  
Adds the desktop group with Uid 27 to the Sales scope.

### 示例 2

    C:\PS> Add-BrokerScope BFC74867-C6EF-482C-996F-3E0D340E96AC -Catalog BangaloreMachines
    

Description  
\---\---\-----  
Adds the BangaloreMachines catalog to the scope with the specified ScopeID.