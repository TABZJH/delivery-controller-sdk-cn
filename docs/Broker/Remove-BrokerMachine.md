# Remove-BrokerMachine

Removes one or more machines from its desktop group or catalog.

## 语法

    Remove-BrokerMachine [-InputObject] <Machine[]> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerMachine [-MachineName] <String> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerMachine cmdlet removes one or more machines from their desktop group or catalog. There are three forms:

o Use the -InputObject parameter to remove a single machine instance or array of instances from their desktop group or catalog. o Use the -MachineName parameter to remove the single named machine from its group or catalog. o Use pipelining to pipe machine instances to the command.

To remove machines from their desktop group use the -DesktopGroup parameter; the specified group must be the one that contains the machines. If more than one machine is being removed from its group they must all be members of the same group.

If the -DesktopGroup parameter is not used then the machines are removed from their catalog. Removing a machine from its catalog deletes the record of the machine from the Citrix Broker Service.

Machines cannot be removed from their catalog while they are members of a desktop group.

## 相关命令

- [Add-BrokerMachine](Add-BrokerMachine.html)
- [Get-BrokerMachine](Get-BrokerMachine.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                 | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | An array of machines to be removed from their desktop group or catalog.                                                                                                                                            | true  | true (ByValue)        |                                                                                        |
| MachineName  | The name of the single machine to remove (must match the MachineName property of the machine).                                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| Force        | Forces removal of machine from a desktop group even if it is still in use (that is, there are user sessions running on the machine). Forcing removal of a machine does not disconnect or logoff the user sessions. | false | false                 |                                                                                        |
| DesktopGroup | The desktop group from which the machines are to be removed, specified by name, UID, or instance.                                                                                                                  | false | true (ByValue)        |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                    | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                 | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines to be removed.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerMachine -InputObject $machine -DesktopGroup $desktopGroup
    C:\PS> Remove-BrokerMachine -InputObject $machine -DesktopGroup 2
    C:\PS> Remove-BrokerMachine $machine -DesktopGroup "MyDesktopGroup"
    

Description  
\---\---\-----  
These all remove a single machine from a desktop group, identifying the group by instance, UID, or name.

### 示例 2

    C:\PS> Remove-BrokerMachine -MachineName "DOMAIN\MyMachine" -DesktopGroup 2
    C:\PS> Remove-BrokerMachine DOMAIN\MyMachine -DesktopGroup "MyDesktopGroup"
    C:\PS> Remove-BrokerMachine DOMAIN\MyMachine -DesktopGroup $desktopGroup
    

Description  
\---\---\-----  
These remove the machine called "DOMAIN\MyMachine" from its desktop group.

### 示例 3

    C:\PS> Remove-BrokerMachine -MachineName DOMAIN\MyMachine
    C:\PS> Remove-BrokerMachine "DOMAIN\MyMachine"
    C:\PS> Remove-BrokerMachine $machine
    

Description  
\---\---\-----  
These all remove a machine from its catalog.

### 示例 4

    C:\PS> Get-BrokerMachine -Uid 3 | Remove-BrokerMachine -DesktopGroup $dg
    C:\PS> Get-BrokerMachine -CatalogUid 4 | Remove-BrokerMachine
    

Description  
\---\---\-----  
These find specific machines and remove them from their desktop group or catalog.