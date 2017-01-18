# Start-BrokerDesktopGroupRebootCycle

Creates and starts a reboot cycle for each specified desktop group.

## 语法

    Start-BrokerDesktopGroupRebootCycle [-InputObject] <DesktopGroup[]> -RebootDuration <Int32> [-WarningDuration <Int32>] [-WarningTitle <String>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Start-BrokerDesktopGroupRebootCycle cmdlet is used to create and start a reboot cycle for specified desktop groups.

The functionality offered is similar to that of New-BrokerRebootSchedule but the resulting reboot cycles execute once as defined by the command parameters rather than on a repeating schedule.

## 相关命令

- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
- [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)
- [Get-BrokerRebootCycle](Get-BrokerRebootCycle.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                          | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject           | Creates a reboot cycle for the specified desktop groups. Groups can be specified using UID values, name values (including wildcards) or desktop group SDK objects.                          | true  | true (ByValue) |                                                                                        |
| RebootDuration        | Approximate maximum duration in minutes over which the reboot cycle runs.                                                                                                                   | true  | false          |                                                                                        |
| WarningDuration       | Time in minutes prior to a machine reboot at which a warning message is displayed in all user sessions on that machine. If the warning duration value is zero then no message is displayed. | false | false          |                                                                                        |
| WarningTitle          | The window title used when showing the warning message in user sessions on a machine scheduled for reboot.                                                                                  | false | false          |                                                                                        |
| WarningMessage        | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed.                                                         | false | false          |                                                                                        |
| WarningRepeatInterval | Number of minutes to wait before showing the reboot warning message again.                                                                                                                  | false | false          |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。             | false | false          |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                          | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

Desktop groups may be specified through pipeline input. The groups can be specified using UID values, name values (including wildcards) or desktop group objects

## 返回值

### none

## 示例

### 示例 1

    C:\PS> Get-BrokerDesktopGroup "SampleGroup" | Start-BrokerDesktopGroupRebootCycle -RebootDuration 240 -WarningMessage "Save your work" -WarningDuration 15
    

Description  
\---\---\-----  
Starts a new reboot cycle for the desktop group called "SampleGroup". Each reboot cycle has a duration of six hours. Fifteen minutes prior to rebooting a machine, the message "Save your work" is displayed in each active user session.