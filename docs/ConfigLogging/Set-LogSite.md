# Set-LogSite

Sets global configuration logging settings.

## 语法

    Set-LogSite [-State <LoggingState>] [-Locale <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet sets the global configuration logging settings.

## 相关命令

- [Get-LogSite](Get-LogSite.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 状态           | Sets the state of configuration logging. Values can be:  
o Enabled - state changes will be logged. If logging is unavailable, the state change will still be permitted. o Disabled - state changes will not be logged.  
o Mandatory - state change will be logged. If logging is unavailable, the state change will not be permitted.  
When the state is set to Enabled or Mandatory, XenDesktop services will attempt to log operations (which perform configuration changes) before performing them. | false | false |                                       |
| 区域设置         | Sets the language that logs should be recorded in. Values can be: 'en', 'ja', 'zh-CN', 'de', 'es' or 'fr'.                                                                                                                                                                                                                                                                                                                                                                                                | false | false |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                                                                                                                                                                                                                                                                                                                                                        | false | false | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                    | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                                                                                | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ConfigurationLogging.Sdk.Site

Current logging settings## Notes Configuration logging will automatically transition to a 'NotSupported' state if the logging feature is not licensed. Set-LogSite will reject request to set logging to 'Enabled' or 'Mandatory' while the logging feature is not licensed.

## 示例

### 示例 1

    C:\PS> Set-LogSite -Locale "zh-CN"
    

Description  
\---\---\-----  
Set the logging language to Chinese. The logging state will be unchanged.

### 示例 2

    C:\PS> Set-LogSite -State "Mandatory"
    

Description  
\---\---\-----  
Set the logging state to mandatory. The logging locale will be unaffected. In this state, no configuration change will be allowed unless it is successfully logged.

### 示例 3

    C:\PS> Set-LogSite -Locale "de" -State "Enabled"
    

Description  
\---\---\-----  
Set the logging language to German and the state to Enabled.