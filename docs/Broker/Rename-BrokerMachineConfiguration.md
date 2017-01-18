# Rename-BrokerMachineConfiguration

Renames a machine configuration.

## 语法

    Rename-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerMachineConfiguration [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-MachineConfiguration cmdlet changes the name of a machine configuration. A machine configuration cannot have the same name as another machine configuration associated with the same slot.

## 相关命令

- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
- [Remove-BrokerMachineConfiguration](Remove-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                         | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Machine configuration to rename.                                                                                                                                                                                                                                                           | true  | true (ByValue)        | 无                                                                                      |
| 名称           | Current name of machine configuration.                                                                                                                                                                                                                                                     | true  | true (ByPropertyName) | 无                                                                                      |
| NewName      | New name for machine configuration. This may have the form "ConfigurationSlotName\MachineConfigurationName" or "MachineConfigurationName". If the "ConfigurationSlotName" is provided it must match the name of the configuration slot that the machine configuration is associated with. | true  | false                 | 无                                                                                      |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                             | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                            | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                         | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.MachineConfiguration

Machine configuration to rename.

## 返回值

### None or Citrix.Broker.Admin.SDK.MachineConfiguration

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.MachineConfiguration object.## Notes The configuration slot can not be changed. Thus the left term of the Name and NewName must match.

## 示例

### 示例 1

    Rename-BrokerMachineConfiguration -Name "UPM\All Departments" -NewName "UPM\Finance Department"
    

Description  
\---\---\-----  
Renames the machine configuration named "UPM\All Departments" to "UPM\Finance Department".

### 示例 2

    Rename-BrokerMachineConfiguration -Name "UPM\All Departments" -NewName "Finance Department"
    

Description  
\---\---\-----  
Renames the machine configuration named "UPM\All Departments" to "UPM\Finance Department".