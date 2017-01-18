# Remove-BrokerMachineCommand

Cancel a pending command queued for delivery to a desktop.

## 语法

    Remove-BrokerMachineCommand [-InputObject] <MachineCommand[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the state of a pending command queued for delivery to a desktop to Canceled. The command is not removed from the system.

## 相关命令

- [Get-BrokerMachineCommand](Get-BrokerMachineCommand.html)
- [New-BrokerMachineCommand](New-BrokerMachineCommand.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Commands to cancel.                                                                                                                                                             | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.MachineCommand

Commands to cancel.

## 返回值

### 无

## 示例

### 示例 1

    Get-BrokerMachineCommand | Remove-BrokerMachineCommand
    

Description  
\---\---\-----  
Cancel all pending commands.

### 示例 2

    Get-BrokerMachineCommand -Category "UPM" | Remove-BrokerMachineCommand
    

Description  
\---\---\-----  
Cancel all pending commands that have the category "UPM".