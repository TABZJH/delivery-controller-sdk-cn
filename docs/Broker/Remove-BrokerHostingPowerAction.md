# Remove-BrokerHostingPowerAction

Cancel one or more pending power actions.

## 语法

    Remove-BrokerHostingPowerAction [-InputObject] <HostingPowerAction[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerHostingPowerAction [-MachineName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Causes one or more of the pending power actions in the queue to be marked as cancelled. The affected power actions are not sent to the hypervisor for processing, and take no further part in the queuing activity.

Power actions cannot be cancelled once they have started to be processed by the hypervisor.

## 相关命令

- [Get-BrokerHostingPowerAction](Get-BrokerHostingPowerAction.html)
- [New-BrokerHostingPowerAction](New-BrokerHostingPowerAction.html)
- [Set-BrokerHostingPowerAction](Set-BrokerHostingPowerAction.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The power action to be cancelled.                                                                                                                                               | true  | true (ByValue)        |                                                                                        |
| MachineName  | Cancels only actions for machines whose name (of the form domain\machine) matches the specified string.                                                                        | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.HostingPowerAction

The power action to be cancelled.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerHostingPowerAction -MachineName 'XD_VDA1'
    

Description  
\---\---\-----  
Cancels any pending power actions for the machine called 'XD_VDA1'.

### 示例 2

    C:\PS> Get-BrokerHostingPowerAction -Filter { State -eq "Pending" -and RequestTime -gt "-00:05" } | Remove-BrokerHostingPowerAction
    

Description  
\---\---\-----  
Cancels any pending power actions requested in the last five minutes.