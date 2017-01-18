# New-BrokerConfigurationSlot

Creates a new configuration slot.

## 语法

    New-BrokerConfigurationSlot [-Name] <String> -SettingsGroup <String> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creates a new configuration slot. The SettingsGroup of the slot determines the particular collection of related settings that may be specified in a machine configuration associated with this slot.

For example, the configuration slot may be restricted to configuring Citrix User Profile Manager settings by specifying the SettingsGroup parameter as "G=UPM".

## 相关命令

- [Get-BrokerConfigurationSlot](Get-BrokerConfigurationSlot.html)
- [Remove-BrokerConfigurationSlot](Remove-BrokerConfigurationSlot.html)
- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)

## 参数

| 名称            | 说明                                                                                                                                                                                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 名称            | Name of the new configuration slot. This must be alphanumeric and not contain white space.                                                                                                                                                                                                                                             | true  | true (ByPropertyName) |                                                                                        |
| SettingsGroup | The settings group determines the particular collection of related settings that may be controlled by this slot. This must match the format of a Citrix Group Policy configuration group (e.g. "G=UPM"). Only settings that have this exact group may be specified in a machine configuration associated with this configuration slot. | true  | true (ByPropertyName) |                                                                                        |
| 说明            | Description of configuration slot.                                                                                                                                                                                                                                                                                                     | false | true (ByPropertyName) |                                                                                        |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                        | false | false                 |                                                                                        |
| AdminAddress  | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                     | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.ConfigurationSlot

New-BrokerConfigurationSlot returns an object representing the newly created configuration slot

## 示例

### 示例 1

    New-BrokerConfigurationSlot -Name "UPM" -SettingsGroup "G=UPM"
    

Description  
\---\---\-----  
Create a new slot named "UPM" to configure settings specific to "User Profile Management"