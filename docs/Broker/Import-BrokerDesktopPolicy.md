# Import-BrokerDesktopPolicy

Sets the site wide Citrix Group Policy settings for the site.

## 语法

    Import-BrokerDesktopPolicy [-Policy] <Byte[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Import-BrokerDesktopPolicy sets the site wide Citrix Group Policy settings. A successful call to this cmdlet will result in the supplied data being uploaded to every machine in the site prior to its next session launch.

## 相关命令

- [Export-BrokerDesktopPolicy](Export-BrokerDesktopPolicy.html)
- [New-BrokerConfigurationSlot](New-BrokerConfigurationSlot.html)
- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| 策略           | The configuration data containing the Citrix Group Policy settings to apply to every machine in the site.                                                                       | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### System.Byte[]

The configuration data as an opaque binary blob.

## 返回值

### 无

## Notes Import-BrokerDesktopPolicy performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation be performed via the Citrix Studio.

## 示例

### 示例 1

    C:\PS> Import-BrokerDesktopPolicy $policyData
    

Description  
\---\---\-----  
This command sets the Citrix Group Policy settings in the site. These policy settings are then applied to every machine prior to the next session launch.