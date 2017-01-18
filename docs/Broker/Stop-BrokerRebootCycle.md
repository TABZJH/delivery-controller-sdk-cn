# Stop-BrokerRebootCycle

Cancels the specified reboot cycle.

## 语法

    Stop-BrokerRebootCycle [-InputObject] <RebootCycle[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Stop-BrokerRebootCycle cmdlet is used to cancel the specified reboot cycle.

## 相关命令

- [Get-BrokerRebootCycle](Get-BrokerRebootCycle.html)
- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
- [Start-BrokerDesktopGroupRebootCycle](Start-BrokerDesktopGroupRebootCycle.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Cancels this reboot cycle.                                                                                                                                                      | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RebootCycle

Reboot cycles may be specified through pipeline input.

## 返回值

### none

## 示例

### 示例 1

    C:\PS> Get-BrokerRebootCycle -CatalogUid 7 | Stop-BrokerRebootCycle
    

Description  
\---\---\-----  
Cancels every reboot cycle for the catalog that has the Uid of 7.