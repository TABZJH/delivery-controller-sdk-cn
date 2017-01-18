# Set-BrokerApplicationGroup

Changes properties of application groups.

## 语法

    Set-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-PassThru] [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-SessionSharingEnabled <Boolean>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerApplicationGroup [-Name] <String> [-PassThru] [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-SessionSharingEnabled <Boolean>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerApplicationGroup cmdlet changes the properties of one or more application groups. The changed properties and the new values of those properties are specified as parameters to Set-BrokerApplicationGroup.

This cmdlet cannot change the relationships of application group objects with other objects. For instance, it cannot change which users can access applications in this application group, or change which desktop groups this application group is published to. To do this, you need to remove the existing association, and then add a new association.

The following example shows how to change the desktop group that application group $applicationGroup is associated with from $desktopGroup1 to $desktopGroup2: Remove-BrokerApplicationGroup $applicationGroup -DesktopGroup $desktopGroup1 Add-RemoveApplicationGroup $applicationGroup -DesktopGroup $desktopGroup2

Application groups may not be renamed using this cmdlet. To rename an application group, use Rename-BrokerApplicationGroup.

## 相关命令

- [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
- [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
- [New-BrokerApplicationGroup](New-BrokerApplicationGroup.html)
- [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
- [Rename-BrokerApplicationGroup](Rename-BrokerApplicationGroup.html)

## 参数

| 名称                    | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject           | Specifies the application group whose properties should be altered. Its Uid can also be substituted for the object reference.                                                   | true  | true (ByValue)        |                                                                                        |
| 名称                    | Alters the properties of application groups whose name matches the supplied pattern.                                                                                            | true  | true (ByPropertyName) |                                                                                        |
| PassThru              | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| 说明                    | The new description for the application group.                                                                                                                                  | false | false                 |                                                                                        |
| 已启用                   | Whether the application group's applications should be launchable by end users.                                                                                                 | false | false                 |                                                                                        |
| RestrictToTag         | Specifies the new values of the application group's tag restriction.                                                                                                            | false | false                 |                                                                                        |
| SessionSharingEnabled | Specifies the new value of the application group's SessionSharingEnabled flag.                                                                                                  | false | false                 |                                                                                        |
| UserFilterEnabled     | Specifies the new value of the application group's UserFilterEnabled flag.                                                                                                      | false | false                 |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.ApplicationGroup

You can pipe application groups to Set-BrokerApplication.

## 返回值

### None or Citrix.Broker.Admin.SDK.ApplicationGroup

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ApplicationGroup object.

## 示例

### 示例 1

    C:\PS> Set-BrokerApplicationGroup 'Helpdesk Apps' -Enabled $false
    

Description  
\---\---\-----  
Prevent new instances of applications in the 'Helpdesk Apps' application group from being launched.

### 示例 2

    C:\PS> Get-BrokerApplicationGroup | Set-BrokerApplicationGroup -UserFilterEnabled $false
    

Description  
\---\---\-----  
Disable the user filter on every application group in the system. (Other access control mechanisms, such as access policy and user filters on individual applications, still apply.)