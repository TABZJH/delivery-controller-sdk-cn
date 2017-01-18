# Export-BrokerConfiguration

Obtains an XML document containing the configuration of the broker and optionally a script to import it into another broker

## 语法

    Export-BrokerConfiguration [-TargetBrokerVersion <Version>] [-ExistingImportScriptId <String>] [-ExistingConfigLastChangeTime <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

## 参数

| 名称                           | 说明                                                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| TargetBrokerVersion          | The version of the broker receiving the configuration                                                                                                                                                            | false | false | $null                                                                                  |
| ExistingImportScriptId       | The Id of the script the caller already has; a new script will be returned in the XML document if different.                                                                                                     | false | false | $null                                                                                  |
| ExistingConfigLastChangeTime | The value of ConfigLastChangeTime in the site object of any configuration already held by the caller. If nothing has changed, an empty configuration will be returned with the "Updated" attribute set to false. | false | false | $null                                                                                  |
| AdminAddress                 | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### This cmdlet does not accept input

## 返回值

### 字符串

The XML document