# Set-BrokerMachineMaintenanceMode

Sets whether the specified machine(s) are in maintenance mode.

## 语法

    Set-BrokerMachineMaintenanceMode [-InputObject] <Machine[]> [-MaintenanceMode] <Boolean> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The cmdlet can be used to set whether a machine is in maintenance mode or not. A machine in maintenance mode is not available for new sessions, and for managed machines all automatic power management is disabled.

There are times when it is necessary to disable desktops. You can do this by setting the InMaintenanceMode property of a desktop to $true. This puts it into maintenance mode. The broker excludes single-session desktops in maintenance mode from brokering decisions and does not start new sessions on them. Existing sessions are unaffected. For multi-session desktops in maintenance mode, reconnections to existing sessions are allowed, but no new sessions are created on the machine.

Desktops in maintenance mode are also excluded from automatic power management, although explicit power actions are still performed.

This cmdlet is equivalent to using the Set-BrokerMachine cmdlet to set the value of only the InMaintenanceMode property.

## 相关命令

- [Set-BrokerMachine](Set-BrokerMachine.html)

## 参数

| 名称              | 说明                                                                                                                                                                                            | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject     | The machine instances whose InMaintenanceMode property you want to set.                                                                                                                       | true  | true (ByValue) |                                                                                        |
| MaintenanceMode | Sets whether the machine is in maintenance mode or not. A machine in maintenance mode is not available for new sessions, and for managed machines all automatic power management is disabled. | true  | true (ByValue) |                                                                                        |
| LoggingId       | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。               | false | false          |                                                                                        |
| AdminAddress    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                            | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines whose properties you want to set.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> $machines = Get-BrokerMachine -MachineName 'MyDomain\*'
              C:\PS> Set-BrokerMachineMaintenanceMode -InputObject $machines $false
    

Description  
\---\---\-----  
This example finds all machines in domain MyDomain and removes them from maintenance mode by setting their InMaintenanceMode property to false.