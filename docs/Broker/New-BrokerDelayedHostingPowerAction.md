# New-BrokerDelayedHostingPowerAction

Causes a power action to be queued after a delay.

## 语法

    New-BrokerDelayedHostingPowerAction [-MachineName] <String> -Action <PowerManagementAction> -Delay <TimeSpan> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Causes a power action to be queued after the specified period of time.

Only ShutDown or Suspend actions can be requested to be delayed in this manner.

For a detailed description of the queuing mechanism, see 'help about_Broker_PowerManagement'.

## 相关命令

- [Get-BrokerDelayedHostingPowerAction](Get-BrokerDelayedHostingPowerAction.html)
- [New-BrokerDelayedHostingPowerAction](New-BrokerDelayedHostingPowerAction.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| MachineName  | Specifies the machine that the action is to be performed on.  
The machine can be identified by DNS name, short name, SID, or name of the form domain\machine.                 | true  | true (ByPropertyName) |                                                                                        |
| 操作           | Specifies the power state change action that is to be performed on the specified machine after the specified delay.  
Valid values are Shutdown and Suspend.                    | true  | true (ByPropertyName) |                                                                                        |
| 延迟           | Specifies a timespan delay before the action is queued.                                                                                                                         | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.DelayedHostingPowerAction

New-BrokerDelayedHostingPowerAction returns the created delayed power action.

## 示例

### 示例 1

    C:\PS> New-BrokerDelayedHostingPowerAction -Action Shutdown -MachineName 'XD_VDA1' -Delay '00:02:00'
    

Description  
\---\---\-----  
Causes the machine called XD_VDA1 to be shut down after a delay of two minutes.