# Set-BrokerHypervisorConnection

Sets the properties of a hypervisor connection.

## 语法

    Set-BrokerHypervisorConnection [-InputObject] <HypervisorConnection[]> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHypervisorConnection [-Name] <String> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerHypervisorConnection cmdlet sets the properties on a hypervisor connection.

## 相关命令

- [Get-BrokerHypervisorConnection](Get-BrokerHypervisorConnection.html)
- [New-BrokerHypervisorConnection](New-BrokerHypervisorConnection.html)
- [Remove-BrokerHypervisorConnection](Remove-BrokerHypervisorConnection.html)

## 参数

| 名称                  | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject         | Specifies the hypervisor connection object to adjust.                                                                                                                           | true  | true (ByValue)        |                                                                                        |
| 名称                  | Specifies the name of the hypervisor connection object to adjust.                                                                                                               | true  | true (ByPropertyName) |                                                                                        |
| PassThru            | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| PreferredController | Supplies the new value of the PreferredController property.                                                                                                                     | false | false                 |                                                                                        |
| LoggingId           | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress        | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.HypervisorConnection

You can pipe the hypervisor connection to be modified to Set-BrokerHypervisorConnection.

## 返回值

### None or Citrix.Broker.Admin.SDK.HypervisorConnection

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.HypervisorConnection object.

## 示例

### 示例 1

    c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "oldController" -Name "Xen Server Connection"
    c:\PS> Set-BrokerHypervisorConnection -InputObject $hvConn -PreferredController "newController"
    

Description  
\---\---\-----  
Updates the preferred controller for a hypervisor connection.