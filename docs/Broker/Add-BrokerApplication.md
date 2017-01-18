# Add-BrokerApplication

Adds applications to a desktop group or application group.

## 语法

    Add-BrokerApplication [-InputObject] <Application[]> [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerApplication [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Add-BrokerApplication cmdlet is used to associate one or more applications with an existing desktop group or application group.

There are two parameter sets for this cmdlet, allowing you to specify the application either by its BrowserName or by an array of object references. Uids can also be substituted for the object references.

See about_Broker_Desktops and about_Broker_Applications for more information.

## 相关命令

- [New-BrokerApplication](New-BrokerApplication.html)
- [Add-BrokerApplication](Add-BrokerApplication.html)
- [Add-BrokerTag](Add-BrokerTag.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)
- [Rename-BrokerApplication](Rename-BrokerApplication.html)
- [Move-BrokerApplication](Move-BrokerApplication.html)
- [Set-BrokerApplication](Set-BrokerApplication.html)

## 参数

| 名称               | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies the application to associate. Its Uid can also be substituted for the object reference.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | true  | true (ByValue)        |                                                                                        |
| 名称               | Specifies the name of the application to be associated with the desktop group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | true  | true (ByPropertyName) |                                                                                        |
| ApplicationGroup | Specifies which application group this application should be associated with.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | false | true (ByValue)        |                                                                                        |
| DesktopGroup     | Specifies which desktop group this application should be associated with. Note that applications can only be associated with desktop groups of the AppsOnly or DesktopsAndApps delivery type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | false | true (ByValue)        |                                                                                        |
| 优先级              | Specifies the priority of the mapping between the application and desktop group where lower numbers imply higher priority with zero being highest.  
If one association has a higher priority than the other, machines from that group will be selected for launching sessions until all machines are at maximum load, in maintenance mode, unregistered, or unavailable for any other reason. Only when all machines from the higher-priority group are unavailable will new connections be routed to the next lowest priority group.  
If multiple associations with equal priorities are encountered, session launches will be load balanced across all machines in both groups. The least-loaded machine across the groups will be chosen.  
This parameter is used only when adding an application to a desktop group. It is an error to specify a priority when adding an application to an application group. | false | true (ByPropertyName) |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Application, or as appropriate by property name

You can pipe the application to be added to Add-BrokerApplication. You can also pipe some of the other parameters by name.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-BrokerApplication -Name "Notepad" -DesktopGroup "Private DesktopGroup"
    

Description  
\---\---\-----  
Adds the application with a Name of "Notepad" to the desktop group called "Private DesktopGroup".