# Set-BrokerSessionPreLaunch

Updates the values of one or more desktop group session pre-launch settings.

## 语法

    Set-BrokerSessionPreLaunch [-InputObject] <SessionPreLaunch[]> [-PassThru] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerSessionPreLaunch [-DesktopGroupName] <String> [-PassThru] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerSessionPreLaunch cmdlet is used to alter the settings of an existing desktop group session pre-launch setting.

## 相关命令

- [New-BrokerSessionPreLaunch](New-BrokerSessionPreLaunch.html)
- [Get-BrokerSessionPreLaunch](Get-BrokerSessionPreLaunch.html)
- [Remove-BrokerSessionPreLaunch](Remove-BrokerSessionPreLaunch.html)

## 参数

| 名称                         | 说明                                                                                                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject                | The session pre-launch to be modified.                                                                                                                                                                                                                 | true  | true (ByValue)        |                                                                                        |
| DesktopGroupName           | The name of the desktop group whose session pre-launch setting is to be modified.                                                                                                                                                                      | true  | true (ByPropertyName) |                                                                                        |
| PassThru                   | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                         | false | false                 | False                                                                                  |
| 已启用                        | Boolean that indicates if the session pre-launch setting is to be enabled or disabled.                                                                                                                                                                 | false | false                 |                                                                                        |
| MaxAverageLoadThreshold    | Specifies the average load threshold across the desktop group. When the threshold hits, pre-launched sessions across the group be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first.                    | false | false                 |                                                                                        |
| MaxLoadPerMachineThreshold | Specifies the maximum load threshold per machine in the desktop group. When the threshold hits, pre-launched sessions on each loaded machine will be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first. | false | false                 |                                                                                        |
| MaxTimeBeforeDisconnect    | Specifies the time by which a pre-launched session will be disconnected. The disconnect time cannot be greater than the terminate timer (if enabled). When the disconnect and terminate times are the same, the terminate time takes precedence.       | false | false                 |                                                                                        |
| MaxTimeBeforeTerminate     | Specifies the time by which a pre-launched session will be terminated. When the disconnect and terminate times are the same, the terminate time takes precedence.                                                                                      | false | false                 |                                                                                        |
| UserFilterEnabled          | Specifies whether the session pre-launch's user filter is enabled or disabled. Where the user filter is enabled, pre-launch is enabled only to users who appear in the filter (either explicitly or by virtue of group membership).                    | false | false                 |                                                                                        |
| LoggingId                  | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                        | false | false                 |                                                                                        |
| AdminAddress               | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                     | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.SessionPreLaunch

Session pre-launch settings may be specified through pipeline input.

## 返回值

### None or Citrix.Broker.Admin.SDK.SessionPreLaunch

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.SessionPreLaunch object.

## 示例

### 示例 1

    C:\PS> Set-BrokerSessionPreLaunch -DesktopGroupName Accounting -MaxTimeBeforeDisconnect 0:10
    

Description  
\---\---\-----  
Sets the disconnect time for the session pre-launch setting associated with desktop group named Accounting.