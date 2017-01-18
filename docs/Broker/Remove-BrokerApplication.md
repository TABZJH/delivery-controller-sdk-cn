# Remove-BrokerApplication

Deletes one or more applications, or an association of an application.

## 语法

    Remove-BrokerApplication [-InputObject] <Application[]> [-Force] [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerApplication [-Name] <String> [-Force] [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerApplication cmdlet deletes one or more applications, or you can use it to delete just the association of an application to a desktop group or application group.

Its usage dictates the behavior of the cmdlet. If only the application is specified as a parameter, then the cmdlet deletes the application. It also deletes any associations this application has with other objects, such as with access policy rules or desktop groups. More specifically, when an application is deleted the following happens: o The association to any desktop groups is removed. o The association to any application groups is removed. o The association to any tags is removed. o Any configured file-type association objects for this application are deleted. o The association to any user accounts is removed. o The association to any access session conditions is removed. o The access policy rule object for this application, if one existed, is deleted. o Finally, the application object itself is deleted.

Note that if the application is in use by a user then the application cannot be deleted.

If more than just the application is supplied as a parameter to the cmdlet (for instance, if a DesktopGroup object is also specified) then the application is not deleted. Instead, only the association from the application to that desktop group is removed.

## 相关命令

- [New-BrokerApplication](New-BrokerApplication.html)
- [Add-BrokerApplication](Add-BrokerApplication.html)
- [Get-BrokerApplication](Get-BrokerApplication.html)
- [Rename-BrokerApplication](Rename-BrokerApplication.html)
- [Move-BrokerApplication](Move-BrokerApplication.html)
- [Set-BrokerApplication](Set-BrokerApplication.html)

## 参数

| 名称               | 说明                                                                                                                                                                                                                                                                                                                                                                                                               | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies the applications to delete. The Uid can also be substituted for the application objects.                                                                                                                                                                                                                                                                                                               | true  | true (ByValue)        |                                                                                        |
| 名称               | Specifies the name of the application to remove.                                                                                                                                                                                                                                                                                                                                                                 | true  | true (ByPropertyName) |                                                                                        |
| Force            | Remove application even if it's in use. Removing an application that is currently in use, can potentially leave an application session containing no applications. If all the applications that are currently active in a disconnected application session are removed, the user will be unable to reconnect to the session. Forcing removal of an in-use application does not impact the actual session itself. | false | false                 | false                                                                                  |
| ApplicationGroup | Specifies the application group that this application should no longer be associated with. The Uid or Name can also be substituted for the application group object.                                                                                                                                                                                                                                             | false | true (ByValue)        |                                                                                        |
| DesktopGroup     | Specifies the desktop group that this application should no longer be associated with. The Uid or Name can also be substituted for the desktop group object.                                                                                                                                                                                                                                                     | false | true (ByValue)        |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                  | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                               | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Application

The application objects can be specified as input.

## 返回值

### 无

This cmdlet does not return any output.

## 示例

### 示例 1

    C:\PS> Remove-BrokerApplication "Notepad"
    

Description  
\---\---\-----  
This command deletes the application that has a BrowserName of "Notepad".

### 示例 2

    C:\PS> $app = Get-BrokerApplication -BrowserName "Notepad"
    C:\PS> $group = Get-BrokerDesktopGroup -Name "Private DesktopGroup"
    C:\PS> Remove-BrokerApplication -InputObject $app -DesktopGroup $group
    

Description  
\---\---\-----  
This command removes the association of the desktop group that has a name of "Private DesktopGroup" from the application that has a BrowserName of "Notepad". It does not otherwise modify the application.