# Set-BrokerHostingPowerAction

Changes the priority of one or more pending power actions.

## 语法

    Set-BrokerHostingPowerAction [-InputObject] <HostingPowerAction[]> [-PassThru] [-ActualPriority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHostingPowerAction [-MachineName] <String> [-PassThru] [-ActualPriority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerHostingPowerAction cmdlet modifies an existing power action in the site's power action queue. The only property of power actions you can change, is the current priority of the action.

For a detailed description of the queuing mechanism, see 'help about_Broker_PowerManagement'.

## 相关命令

- [Get-BrokerHostingPowerAction](Get-BrokerHostingPowerAction.html)
- [New-BrokerHostingPowerAction](New-BrokerHostingPowerAction.html)
- [Remove-BrokerHostingPowerAction](Remove-BrokerHostingPowerAction.html)

## 参数

| 名称             | 说明                                                                                                                                                                                                                                                                                                                                  | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject    | The power action whose priority is to be changed.                                                                                                                                                                                                                                                                                   | true  | true (ByValue)        |                                                                                        |
| MachineName    | Changes the priority of actions that are for machines whose name (of the form domain\machine) matches the specified string.                                                                                                                                                                                                        | true  | true (ByPropertyName) |                                                                                        |
| PassThru       | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                                                                      | false | false                 | False                                                                                  |
| ActualPriority | Specifies a new priority value for the action in the queue.  
This priority is the current action priority; the 'base' or original priority for actions cannot be altered. Numerically lower priority values indicate more important actions that are processed in preference to actions with numerically higher priority settings. | false | false                 |                                                                                        |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                     | false | false                 |                                                                                        |
| AdminAddress   | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                  | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.HostingPowerAction

The power action whose priority is to be changed.

## 返回值

### None or Citrix.Broker.Admin.SDK.HostingPowerAction

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.HostingPowerAction object.

## 示例

### 示例 1

    C:\PS> Set-BrokerHostingPowerAction -MachineName 'XD_VDA1' -ActualPriority 25
    

Description  
\---\---\-----  
Sets the current priority of actions for the machine called 'XD_VDA1' to 25. Numerically lower priority values indicate more important actions that will be processed in preference to actions with numerically higher priority settings.