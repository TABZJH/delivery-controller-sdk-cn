# Remove-BrokerHypervisorConnection

Removes a hypervisor connection from the system.

## 语法

    Remove-BrokerHypervisorConnection [-InputObject] <HypervisorConnection[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerHypervisorConnection [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove-BrokerHypervisorConnection removes a hypervisor connection from the system. A hypervisor connection cannot be removed if it's being used by a machine.

## 相关命令

- [Get-BrokerHypervisorConnection](Get-BrokerHypervisorConnection.html)
- [Set-BrokerHypervisorConnection](Set-BrokerHypervisorConnection.html)
- [New-BrokerHypervisorConnection](New-BrokerHypervisorConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the hypervisor connection object to remove.                                                                                                                           | true  | true (ByValue)        |                                                                                        |
| 名称           | Specifies the name of the hypervisor connection object to remove.                                                                                                               | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.HypervisorConnection

You can pipe the hypervisor connection to be removed to Remove-BrokerHypervisorConnection.

## 返回值

### 无

## 示例

### 示例 1

    c:\PS> Remove-BrokerHypervisorConnection -Name "Xen Server Connection"
    

Description  
\---\---\-----  
This command removes a hypervisor connection by name.

### 示例 2

    c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "controllerName" -Name "Xen Server Connection"
    c:\PS> Remove-BrokerHypervisorConnection -InputObject $hvConn
    

Description  
\---\---\-----  
Gets a hypervisor connection by preferred controller and removes it.