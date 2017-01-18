# Remove-BrokerMachineConfiguration

Deletes a machine configuration from the site or removes the association from a desktop group.

## 语法

    Remove-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerMachineConfiguration [-Name] <String> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet has three functions: o Break associations between desktop groups and machine configurations. o Break associations between applications and machine configurations. o Remove machine configurations from the system.

If no desktop group or application is specified, then the Remove-MachineConfiguration cmdlet removes the machine configuration from the site.

If a desktop group is specified, then the Remove-MachineConfiguration cmdlet removes the association between the machine configuration and that desktop group. In this case, the machine configuration is not removed from the site.

If an application is specified, then the Remove-MachineConfiguration cmdlet removes the association between the machine configuration and that application. Again, in this case, the machine configuration is not removed from the site.

## 相关命令

- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
- [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Machine configuration to remove.                                                                                                                                                | true  | true (ByValue)        | 无                                                                                      |
| 名称           | Name of machine configuration for which the remove operation applies.                                                                                                           | true  | true (ByPropertyName) | 无                                                                                      |
| 应用程序         | The application from which this machine configuration is to be removed.                                                                                                         | false | true (ByValue)        | 无                                                                                      |
| DesktopGroup | The desktop group from which this machine configuration is to be removed.                                                                                                       | false | true (ByValue)        | 无                                                                                      |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.MachineConfiguration

Machine configuration to remove

## 返回值

### 无

## Notes A machine configuration can only be removed if it is not currently applied to a desktop group.

## 示例

### 示例 1

    Remove-BrokerMachineConfiguration -Name UPM\Finance
    

Description  
\---\---\-----  
Removes the machine configuration named "UPM\Finance".

### 示例 2

    Remove-BrokerMachineConfiguration -Name Receiver\HumanResources -DesktopGroup SharedWorkers
    

Description  
\---\---\-----  
Removes the association of the machine configuration named "Receiver\HumanResources" from the "SharedWorkers" desktop group.