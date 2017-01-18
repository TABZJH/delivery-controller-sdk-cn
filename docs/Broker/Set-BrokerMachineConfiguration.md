# Set-BrokerMachineConfiguration

Sets the properties of a machine configuration.

## 语法

    Set-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-PassThru] [-Description <String>] [-Policy <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerMachineConfiguration [-Name] <String> [-PassThru] [-Description <String>] [-Policy <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the properties of a machine configuration. The encoded settings data must only contain settings that match the SettingsGroup of the associated configuration slot. Use the SDK snap-in that matches the SettingsGroup of the associated configuration slot to generate new encoded settings data or modify existing settings values.

## 相关命令

- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
- [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
- [Remove-BrokerMachineConfiguration](Remove-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Machine configuration to modify.                                                                                                                                                | true  | true (ByValue)        |                                                                                        |
| 名称           | Name of machine configuration to modify.                                                                                                                                        | true  | true (ByPropertyName) |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| 说明           | New description for the machine configuration.                                                                                                                                  | false | false                 |                                                                                        |
| 策略           | New binary array of encoded settings data.                                                                                                                                      | false | false                 |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.MachineConfiguration

Machine configuration to modify.

## 返回值

### None or Citrix.Broker.Admin.SDK.MachineConfiguration

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.MachineConfiguration object.

## 示例

### 示例 1

    Set-BrokerMachineConfiguration -Name "UPM\Finance Department" -Policy $newPolicy
    

Description  
\---\---\-----  
Use the encoded settings binary data in $newPolicy to update the machine configuration.

### 示例 2

    Get-BrokerMachineConfiguration -Name "UPM\*" | Set-BrokerMachineConfiguration -Description "User Profile Management"
    

Description  
\---\---\-----  
Assign the description "User Profile Management" to every machine configuration associated with the UPM slot.