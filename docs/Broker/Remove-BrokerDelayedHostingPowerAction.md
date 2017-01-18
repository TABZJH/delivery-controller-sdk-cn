# Remove-BrokerDelayedHostingPowerAction

Cancels one or more delayed power actions.

## 语法

    Remove-BrokerDelayedHostingPowerAction [-InputObject] <DelayedHostingPowerAction[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerDelayedHostingPowerAction [-MachineName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes one or more delayed power actions that have not yet been queued for execution.

## 相关命令

- [Get-BrokerDelayedHostingPowerAction](Get-BrokerDelayedHostingPowerAction.html)
- [New-BrokerDelayedHostingPowerAction](New-BrokerDelayedHostingPowerAction.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The power action to be cancelled.                                                                                                                                               | true  | true (ByValue)        |                                                                                        |
| MachineName  | Cancels only actions for machines whose name (of the form domain\machine) matches the specified string.                                                                        | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DelayedHostingPowerAction

The power action to be cancelled.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerHostingPowerAction -MachineName 'XD_VDA1'
    

Description  
\---\---\-----  
Cancels any pending delayed power actions for the machine called XD_VDA1.