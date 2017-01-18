# Set-BrokerMachine

Sets properties on a machine.

## 语法

    Set-BrokerMachine [-InputObject] <Machine[]> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-HostedMachineId <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsReserved <Boolean>] [-PublishedName <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerMachine [-MachineName] <String> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-HostedMachineId <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsReserved <Boolean>] [-PublishedName <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerMachine cmdlet sets properties on a machine or set of machines. You can specify a single machine by name or multiple machine instances can be passed to the command by piping or using the -InputObject parameter.

## 相关命令

- [Get-BrokerMachine](Get-BrokerMachine.html)
- [New-BrokerMachine](New-BrokerMachine.html)

## 参数

| 名称                      | 说明                                                                                                                                                                                                                                                  | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject             | The machine instances whose properties you want to set.                                                                                                                                                                                             | true  | true (ByValue)        |                                                                                        |
| MachineName             | The machine whose properties you want to set.                                                                                                                                                                                                       | true  | true (ByPropertyName) |                                                                                        |
| PassThru                | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                      | false | false                 | False                                                                                  |
| AssignedClientName      | Changes the client name assignment of the machine. Set this to $null to remove the assignment. You can assign machines to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time.       | false | false                 |                                                                                        |
| AssignedIPAddress       | Changes the client IP address assignment of the machine. Set this to $null to remove the assignment. You can assign machines to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time. | false | false                 |                                                                                        |
| HostedMachineId         | The unique ID by which the hypervisor recognizes the machine. This may only be set for VMs which are not provisioned by MCS.                                                                                                                        | false | false                 |                                                                                        |
| HypervisorConnectionUid | The hypervisor connection that runs the machine. This may only be set for VMs which are not provisioned by MCS.                                                                                                                                     | false | false                 |                                                                                        |
| 处于维护模式                  | Sets whether the machine is in maintenance mode or not. A machine in maintenance mode is not available for new sessions, and for managed machines all automatic power management is disabled.                                                       | false | false                 |                                                                                        |
| IsReserved              | Specifies whether the machine should be reserved for special use, for example, for AppDisk preparation. A machine cannot be reserved if it is already a member of a desktop group.                                                                  | false | false                 |                                                                                        |
| PublishedName           | The name of the machine that is displayed in StoreFront, if the machine has been published. It can be set only for private desktops.                                                                                                                | false | false                 |                                                                                        |
| LoggingId               | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                     | false | false                 |                                                                                        |
| AdminAddress            | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                  | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines whose properties you want to set.

## 返回值

### None or Citrix.Broker.Admin.SDK.Machine

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Machine object.

## 示例

### 示例 1

    C:\PS> Set-BrokerMachine -MachineName 'MyDomain\MyMachine' -HypervisorConnectionUid 3
    

Description  
\---\---\-----  
This example specifies a machine by name and sets its hypervisor connection.

### 示例 2

    C:\PS> $machines = Get-BrokerMachine -MachineName 'MyDomain\*'
    C:\PS> Set-BrokerMachine -InputObject $machines -HypervisorConnectionUid 3
    

Description  
\---\---\-----  
This example finds all machines in domain MyDomain and sets their hypervisor connections.

### 示例 3

    C:\PS> Get-BrokerMachine -MachineName 'MyDomain\*' | Set-BrokerMachine -HypervisorConnectionUid 3
    

Description  
\---\---\-----  
This example also finds all machines in domain MyDomain and sets their hypervisor connections.