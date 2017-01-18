# New-BrokerHostingPowerAction

Creates a new action in the power action queue.

## 语法

    New-BrokerHostingPowerAction [-MachineName] <String> -Action <PowerManagementAction> [-ActualPriority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerHostingPowerAction cmdlet adds a new power action record into the queue of power actions to be performed. The power actions in the queue are processed on a priority basis and sent to the relevant hypervisor to change the power state of a virtual machine.

A power action record defines the action to be performed, the machine on which the action is to be performed, and an initial priority value for the action. Multiple actions may be created that relate to the same machine.

For a detailed description of the queuing mechanism, see 'help about_Broker_PowerManagement'.

## 相关命令

- [Get-BrokerHostingPowerAction](Get-BrokerHostingPowerAction.html)
- [Set-BrokerHostingPowerAction](Set-BrokerHostingPowerAction.html)
- [Remove-BrokerHostingPowerAction](Remove-BrokerHostingPowerAction.html)

## 参数

| 名称             | 说明                                                                                                                                                                                                                                                                                                                                              | 是否必需？ | 管道输入                           | 默认值                                                                                    |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | -------------------------------------------------------------------------------------- |
| MachineName    | Specifies the machine that the action is to be performed on.  
The machine can be identified by DNS name or short name or SID or 'machine\domain' form name.                                                                                                                                                                                   | true  | true (ByValue, ByPropertyName) |                                                                                        |
| 操作             | Specifies the power state change action that is to be performed on the specified machine.  
Valid values are: TurnOn, TurnOff, ShutDown, Reset, Restart, Suspend and Resume.                                                                                                                                                                    | true  | true (ByPropertyName)          |                                                                                        |
| ActualPriority | Specifies an initial priority value for the action in the queue.  
This priority is the current action priority; the 'base' priority for actions created via this cmdlet is always 30. Numerically lower priority values indicate more important actions that are processed in preference to actions with numerically higher priority settings. | false | true (ByPropertyName)          | 30                                                                                     |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                 | false | false                          |                                                                                        |
| AdminAddress   | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                              | false | false                          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### MachineName (System.String)

A list of machine names can be supplied as input.

## 返回值

### Citrix.Broker.Admin.SDK.HostingPowerAction

New-BrokerHostingPowerAction returns the newly created power action record.

## 示例

### 示例 1

    C:\PS> New-BrokerHostingPowerAction -Action Shutdown -MachineName 'XD_VDA1'
    

Description  
\---\---\-----  
Causes the machine called 'XD_VDA1' to be shut down.