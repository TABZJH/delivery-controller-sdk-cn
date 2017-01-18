# Remove-BrokerScope

Remove the specified catalog/desktop group from the given scope(s).

## 语法

    Remove-BrokerScope [-InputObject] <Scope[]> [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerScope cmdlet is used to remove a scopeable object object from the given scope(s). A scopeable object is one of: o a catalog o a desktop group o an application group

To remove a scopeable object from a scope you need permission to change the scopes of the scopeable object.

If the scopeable object is not in a specified scope, that scope will be silently ignored.

## 相关命令

## 参数

| 名称               | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies the scopes to remove the object from.                                                                                                                                 | true  | true (ByValue) | 空值                                                                                     |
| ApplicationGroup | Specifies the application group object to be removed.                                                                                                                           | false | true (ByValue) |                                                                                        |
| 目录               | Specifies the catalog object to be removed.                                                                                                                                     | false | true (ByValue) |                                                                                        |
| DesktopGroup     | Specifies the desktop group object to be removed.                                                                                                                               | false | true (ByValue) |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Scope

You can pipe scopes to Remove-BrokerScope.

## 返回值

### 

## 示例

### 示例 1

    C:\PS> Remove-BrokerScope Sales,Marketing -DesktopGroup "Win7 Desktops"
    

Description  
\---\---\-----  
Removes the "Win7 Desktops" desktop group from both the Sales and Marketing scopes.

### 示例 2

    C:\PS> Sales,Marketing | Remove-BrokerScope -DesktopGroup 'Win7 Desktops'
    

Description  
\---\---\-----  
Removes the "Win7 Desktops" desktop group from both the Sales and Marketing scopes.