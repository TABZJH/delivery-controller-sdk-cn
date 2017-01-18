# Set-BrokerRebootSchedule

Updates the values of one or more desktop group reboot schedules.

## 语法

    Set-BrokerRebootSchedule [-InputObject] <RebootSchedule[]> [-PassThru] [-Day <RebootScheduleDays>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RebootDuration <Int32>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerRebootSchedule [-DesktopGroupName] <String> [-PassThru] [-Day <RebootScheduleDays>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RebootDuration <Int32>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerRebootSchedule cmdlet is used to alter the settings of an existing desktop group reboot schedule.

## 相关命令

- [Get-BrokerRebootSchedule](Get-BrokerRebootSchedule.html)
- [New-BrokerRebootSchedule](New-BrokerRebootSchedule.html)
- [Remove-BrokerRebootSchedule](Remove-BrokerRebootSchedule.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                                                                                                            | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject           | The reboot schedule to be modified.                                                                                                                                                                                                                                                                                                                                                                                           | true  | true (ByValue)        |                                                                                        |
| DesktopGroupName      | The name of the desktop group whose reboot schedule is to be modified.                                                                                                                                                                                                                                                                                                                                                        | true  | true (ByPropertyName) |                                                                                        |
| PassThru              | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                                                                                                                                                                | false | false                 | False                                                                                  |
| 天                     | For weekly schedules, the day of the week on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday).                                                                                                                                                                                                                                                                 | false | false                 |                                                                                        |
| 已启用                   | Boolean that indicates if the reboot schedule is to be enabled or disabled.                                                                                                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| 频率                    | Frequency with which this schedule runs (either Weekly or Daily).                                                                                                                                                                                                                                                                                                                                                             | false | false                 |                                                                                        |
| RebootDuration        | Approximate maximum number of minutes over which the scheduled reboot cycle runs.                                                                                                                                                                                                                                                                                                                                             | false | false                 |                                                                                        |
| StartTime             | Time of day at which the scheduled reboot cycle starts (HH:MM).                                                                                                                                                                                                                                                                                                                                                               | false | false                 |                                                                                        |
| WarningDuration       | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | false                 |                                                                                        |
| WarningMessage        | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot.                                                                                                                                                                                                         | false | false                 |                                                                                        |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning.                                                                                                                                                                                  | false | false                 |                                                                                        |
| WarningTitle          | The window title used when showing the warning message in user sessions on a machine scheduled for reboot.                                                                                                                                                                                                                                                                                                                    | false | false                 |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                               | false | false                 |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                            | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RebootSchedule

Reboot schedules may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Set-BrokerRebootSchedule -DesktopGroupName Accounting -WarningMessage "Save your work" -WarningDuration 10 -WarningTitle "WARNING: Reboot pending"
    

Description  
\---\---\-----  
Sets the reboot schedule for the desktop group named Accounting to display a message with the title "WARNING: Reboot pending" and body "Save your work" ten minutes prior to rebooting each machine. The message is displayed in every user session on that machine.

### 示例 2

    C:\PS> Get-BrokerRebootSchedule -Frequency Weekly | Set-BrokerRebootSchedule -Day Friday
    

Description  
\---\---\-----  
Sets all weekly reboot schedules to run on Friday.

### 示例 3

    C:\PS> Set-BrokerRebootSchedule -DesktopGroupUid 17 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
    

Description  
\---\---\-----  
Sets the reboot schedule for the desktop group having Uid 17 to display the message "Rebooting in %m% minutes." Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.