# Add-BrokerApplicationGroup

Adds application groups to a desktop group.

## 语法

    Add-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerApplicationGroup [-Name] <String> [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Add-BrokerApplicationGroup cmdlet is used to associate one or more application groups with an existing desktop group.

Associating an application group with a desktop group makes the desktop groups's machines available for launching applications in that application group. Until an application group is associated with a desktop group, its applications cannot be launched.

There are two parameter sets for this cmdlet, allowing you to specify the application groups either by Name or by an array of object references. Uids can also be substituted for the object references.

See about_Broker_Applications for more information.

## 相关命令

- [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
- [New-BrokerApplicationGroup](New-BrokerApplicationGroup.html)
- [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
- [Rename-BrokerApplicationGroup](Rename-BrokerApplicationGroup.html)
- [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the application group to associate with the desktop group. Its Uid can also be substituted for the object reference.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 名称           | Specifies the name of the application group to associate with the desktop group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | true  | true (ByPropertyName) |                                                                                        |
| DesktopGroup | Specifies the desktop groups with which the application groups should be associated.  
Note that application groups can only be associated with desktop groups whose delivery type is either AppsOnly or DesktopsAndApps.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | false | true (ByValue)        |                                                                                        |
| 优先级          | Specifies the priority of the mapping between the application group and desktop group. Lower numbers imply higher priority with zero being highest.  
If one association has a higher priority than the other, machines from that group will be selected for launching sessions until all machines are at maximum load, in maintenance mode, unregistered, or unavailable for any other reason. Only when all machines from the higher-priority desktop group are unavailable will new connections be routed to the next lowest priority desktop group.  
If multiple associations with equal priorities are encountered, session launches will be load balanced across all machines in both desktop groups. The least-loaded machine across the desktop groups will be chosen. | false | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.ApplicationGroup, or as appropriate by property name

You can pipe the application group to be added to Add-BrokerApplicationGroup. You can also pipe some of the other parameters by name.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-BrokerApplicationGroup -Name "Office Apps" -DesktopGroup "Private DesktopGroup"
    

Description  
\---\---\-----  
Adds the application group with the Name "Office Apps" to the desktop group called "Private DesktopGroup".