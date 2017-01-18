# New-BrokerMachineConfiguration

Creates a new machine configuration associated with an existing configuration slot.

## 语法

    New-BrokerMachineConfiguration -ConfigurationSlotUid <Int32> -LeafName <String> -Policy <Byte[]> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creates a new machine configuration containing settings that match the SettingsGroup of the associated configuration slot. This machine configuration can then be applied to a desktop group to have the settings applied to machines in that group.

The SettingsGroup of the configuration slot restricts the permitted settings. Use the SDK snap-in that matches the SettingsGroup to create the encoded settings data.

## 相关命令

- [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
- [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
- [Remove-BrokerMachineConfiguration](Remove-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)

## 参数

| 名称                   | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| ConfigurationSlotUid | Unique identifier of the configuration slot to associate with this machine configuration.                                                                                       | true  | true (ByPropertyName) | 无                                                                                      |
| LeafName             | Name of the new machine configuration. This must be unique amongst the machine configurations associated with the same configuration slot.                                      | true  | true (ByPropertyName) | 无                                                                                      |
| 策略                   | A binary array of encoded settings (policy) data created with the SDK snap-in that matches the SettingsGroup of the configuration slot.                                         | true  | true (ByPropertyName) | 无                                                                                      |
| 说明                   | Description of the new machine configuration.                                                                                                                                   | false | true (ByPropertyName) |                                                                                        |
| LoggingId            | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress         | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.MachineConfiguration

New-BrokerMachineConfiguration returns the newly created configuration## Notes Delegated Administration can be used to restrict the configuration slots that an administrator can use and hence which components of the system that can be configured.

## 示例

### 示例 1

    New-BrokerMachineConfiguration -LeafName "Finance Department" -Description "Finance Dept. User Profile Management policy" -Policy $policy -ConfigurationSlotUid $csUid
    

Description  
\---\---\-----  
Creates a new configuration named "%SlotName%\Finance Department" where %SlotName% is the name of the configuration slot having the Uid $csUid. The encoded settings in the $policy variable must match the SettingsGroup of the configuration slot having the Uid $csUid.