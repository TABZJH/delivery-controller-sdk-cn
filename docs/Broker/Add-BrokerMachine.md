# Add-BrokerMachine

Adds one or more machines to a desktop group.

## 语法

    Add-BrokerMachine [-InputObject] <Machine[]> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerMachine [-MachineName] <String> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Add-BrokerMachine cmdlet adds specified machines to a desktop group. There are three forms:

o Use the -InputObject parameter to add a single machine instance or array of instances to the group. o Use the -MachineName parameter to add a single, named machine to the group. o Use pipelining to pipe machines instances to the command.

The desktop group to which the machines are added can be specified by name, unique identifier (UID), or instance.

For a machine to be used in a site, the machine must be added to a desktop group. The machine and desktop group must be compatible in order for the process to succeed; for example a machine in a single-session catalog cannot be added to a multi-session desktop group.

For more information about machines, see about_Broker_Machines.

## 相关命令

- [Add-BrokerMachinesToDesktopGroup](Add-BrokerMachinesToDesktopGroup.html)
- [Remove-BrokerMachine](Remove-BrokerMachine.html)
- [Get-BrokerMachine](Get-BrokerMachine.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | An array of machines to add to the group.                                                                                                                                       | true  | true (ByValue)        |                                                                                        |
| MachineName  | The name of the single machine to add (must match the MachineName property of the machine).                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| DesktopGroup | The desktop group to which the machines are added, specified by name, Uid, or instance.                                                                                         | false | true (ByValue)        |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines you want to add.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup $desktopGroup
    C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup 2
    C:\PS> Add-BrokerMachine $machine -DesktopGroup "MyDesktopGroup"
    

Description  
\---\---\-----  
These examples all add a single machine instance to a desktop group, identifying the group by instance, UID, or name.

### 示例 2

    C:\PS> Add-BrokerMachine -MachineName "MyDomain\MyMachine" -DesktopGroup 2
    C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup "MyDesktopGroup"
    C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup $desktopGroup
    

Description  
\---\---\-----  
These examples add the machine called MyMachine to a desktop group.

### 示例 3

    C:\PS> Get-BrokerMachine -Uid 3 | Add-BrokerMachine -DesktopGroup 2
    C:\PS> Get-BrokerMachine -CatalogUid 4 | Add-BrokerMachine -DesktopGroup 2
    

Description  
\---\---\-----  
These examples find specific machines and add them to a desktop group.