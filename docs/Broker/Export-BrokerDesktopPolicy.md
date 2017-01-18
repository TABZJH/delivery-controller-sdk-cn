# Export-BrokerDesktopPolicy

Gets the site wide Citrix Group Policy settings.

## 语法

    Export-BrokerDesktopPolicy [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Export-BrokerDesktopPolicy returns an array of bytes containing the site-wide Citrix Group Policy settings. These policy settings are applied to every machine in the site.

## 相关命令

- [Import-BrokerDesktopPolicy](Import-BrokerDesktopPolicy.html)
- [New-BrokerConfigurationSlot](New-BrokerConfigurationSlot.html)
- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

## 返回值

### System.Byte[]

The configuration data as an opaque binary blob. This will be null if no site wide Citrix Group Policy settings are in place.## Notes Export-BrokerDesktopPolicy performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation only be performed via the Citrix Studio.

## 示例

### 示例 1

    C:\PS> $policy = Export-BrokerDesktopPolicy
    

Description  
\---\---\-----  
This command exports the site wide Citrix Group Policy settings.