# New-BrokerApplicationGroup

Create a new application group to which applications can be added.

## 语法

    New-BrokerApplicationGroup [-Name] <String> [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-Scope <String[]>] [-SessionSharingEnabled <Boolean>] [-TenantId <Guid>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerApplicationGroup cmdlet creates a new application group. Applications that are added to the application group can then be managed centrally by setting properties on the application group rather than on each application individually.

Application groups may also be used to isolate applications that should not share sessions with other applications. To do this, create an application group with SessionSharingEnabled equal to $false, and then add to it those applications that you wish to isolate. The isolated applications continue to share sessions with each other, but not with any other published applications.

To create a new application and add it to an application group, use New-BrokerApplication -ApplicationGroup. To add an existing application to an application group, use Add-BrokerApplication -ApplicationGroup.

After adding applications to an application group, you must then publish the application group to a desktop group before its applications can be launched. Use the Add-BrokerApplicationGroup cmdlet to do this.

To manipulate the user filter associated with an application group, use Add-BrokerUser -ApplicationGroup and Remove-BrokerUser -ApplicationGroup.

To manipulate the set of tags associated with an application group, use Add-BrokerTag -ApplicationGroup and Remove-BrokerTag -ApplicationGroup.

See about_Broker_Applications for more information.

## 相关命令

- [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
- [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
- [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
- [Rename-BrokerApplicationGroup](Rename-BrokerApplicationGroup.html)
- [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)
- [Add-BrokerApplication](Add-BrokerApplication.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)
- [Add-BrokerUser](Add-BrokerUser.html)
- [Remove-BrokerUser](Remove-BrokerUser.html)
- [Add-BrokerTag](Add-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                      | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 名称                    | A name for the application group. Not visible to end users.                                                                                                                                                                                                                                                                             | true  | true (ByPropertyName) |                                                                                        |
| 说明                    | A description for the application group. Not visible to end users.                                                                                                                                                                                                                                                                      | false | true (ByPropertyName) | 空值                                                                                     |
| 已启用                   | Whether the application group's applications can be launched by end users.                                                                                                                                                                                                                                                              | false | true (ByPropertyName) | true                                                                                   |
| RestrictToTag         | Optional tag that may be used further to restrict which machines may be used for launching the application group's applications. A machine may be used by an application group if either the application group has no tag restriction or the application group does have a tag restriction and the machine is tagged with the same tag. | false | true (ByPropertyName) | 空值                                                                                     |
| 作用域                   | Specifies the name of the delegated administration scope to which the application group should belong.                                                                                                                                                                                                                                  | false | true (ByPropertyName) | 空值                                                                                     |
| SessionSharingEnabled | Whether the application group's applications can share sessions with applications that are not a member of this application group.                                                                                                                                                                                                      | false | true (ByPropertyName) | true                                                                                   |
| TenantId              | Specifies identity of tenant associated with application group. Must always be specified in multitenant sites, must not be specified otherwise.                                                                                                                                                                                         | false | true (ByPropertyName) |                                                                                        |
| UserFilterEnabled     | Whether the application group's user filter is enabled or disabled. Where the user filter is enabled, the application is visible only to users who appear in the filter (either explicitly or by virtue of group membership).                                                                                                           | false | true (ByPropertyName) | false                                                                                  |
| UUID                  | The UUID of the application group. If a UUID is not provided, then one will be generated automatically.                                                                                                                                                                                                                                 | false | true (ByPropertyName) | 空值                                                                                     |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                         | false | false                 |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                      | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.ApplicationGroup

The newly created application group.

## 示例

### 示例 1

    C:\PS> New-BrokerApplicationGroup "Helpdesk Apps"
    

Description  
\---\---\-----  
Creates a new application group called 'Helpdesk Apps'.

### 示例 2

    C:\PS> New-BrokerApplicationGroup "Accounts Apps" -UserFilterEnabled $true
    C:\PS> Add-BrokerUser "MYDOMAIN\Accounts" -ApplicationGroup "Accounts Apps"
    

Description  
\---\---\-----  
Creates a new application group called 'Accounts Apps', and then restrict access so that only members of the MYDOMAIN\Accounts user group can launch applications in 'Accounts Apps'.