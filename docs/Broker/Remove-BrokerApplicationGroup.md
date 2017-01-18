# Remove-BrokerApplicationGroup

Remove application groups from the system, or break the association between an application group and a desktop group.

## 语法

    Remove-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerApplicationGroup [-Name] <String> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet has 2 functions: o Break associations between application groups and desktop groups. o Remove application groups from the system.

Associating an application group with a desktop group allows the applications that are members of that application group to be launched on machines that are members of the associated desktop group. Breaking that association means that those applications may no longer be launched on those machines.

To remove an application group from the system, you must first remove all of its applications. Use the Remove-BrokerApplication cmdlet to remove an application (either to remove it from an application group, or to remove it from the system entirely).

## 相关命令

- [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
- [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
- [New-BrokerApplicationGroup](New-BrokerApplicationGroup.html)
- [Rename-BrokerApplicationGroup](Rename-BrokerApplicationGroup.html)
- [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the application groups to remove.                                                                                                                                                                                                                                                                                                                                                                                                                       | true  | true (ByValue)        |                                                                                        |
| 名称           | Removes application groups whose name matches the given pattern.                                                                                                                                                                                                                                                                                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| Force        | When this flag is specified, an application group may be removed from the system even if its SessionSharingEnabled property is false and one of its applications is still running in some session.  
Such an application group cannot by default be removed, because doing so would allow for other applications to be launched into existing sessions. Either wait until the sessions associated with the application group have exited, or use the -Force flag. | false | false                 |                                                                                        |
| DesktopGroup | When this parameter is specified, the application groups are removed from the given desktop group. The desktop group may be specified either by its Uid or by its name.  
When this parmeter is not specified, the application groups are removed from the system entirely.                                                                                                                                                                                       | false | true (ByValue)        |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                                                | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.ApplicationGroup

You can pipe application groups to Remove-BrokerApplicationGroup.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerApplicationGroup Office -DesktopGroup Windows10VDAs
    

Description  
\---\---\-----  
Remove the association between the 'Office' application group and the 'Windows10VDAs' desktop group. The 'Office' applications will no longer be launchable on the machines in the 'Windows10VDAs' desktop group.

### 示例 2

    C:\PS> Remove-BrokerApplicationGroup Office
    

Description  
\---\---\-----  
Remove the 'Office' application group from the system altogether. You must remove all applications from the application group first.