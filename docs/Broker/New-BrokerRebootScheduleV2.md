# New-BrokerRebootScheduleV2

Creates a new reboot schedule for a desktop group.

## 语法

    New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupName <String> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupUid <Int32> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerRebootScheduleV2 cmdlet is used to define a reboot schedule for a desktop group.

## 相关命令

- [Get-BrokerRebootScheduleV2](Get-BrokerRebootScheduleV2.html)
- [Set-BrokerRebootScheduleV2](Set-BrokerRebootScheduleV2.html)
- [Remove-BrokerRebootScheduleV2](Remove-BrokerRebootScheduleV2.html)
- [Rename-BrokerRebootScheduleV2](Rename-BrokerRebootScheduleV2.html)
- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                                                                                                            | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 名称                    | The name of the new reboot schedule.                                                                                                                                                                                                                                                                                                                                                                                          | true  | true (ByPropertyName) |                                                                                        |
| RebootDuration        | Approximate maximum number of minutes over which the scheduled reboot cycle runs.                                                                                                                                                                                                                                                                                                                                             | true  | true (ByPropertyName) |                                                                                        |
| DesktopGroupName      | The name of the desktop group that this reboot schedule is applied to.                                                                                                                                                                                                                                                                                                                                                        | true  | true (ByPropertyName) |                                                                                        |
| DesktopGroupUid       | The Uid of the desktop group that this reboot schedule is applied to.                                                                                                                                                                                                                                                                                                                                                         | true  | true (ByPropertyName) |                                                                                        |
| 天                     | For weekly schedules, the day of the week on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday).                                                                                                                                                                                                                                                                 | false | true (ByPropertyName) |                                                                                        |
| 说明                    | An optional description for the reboot schedule.                                                                                                                                                                                                                                                                                                                                                                              | false | true (ByPropertyName) |                                                                                        |
| 已启用                   | Boolean that indicates if the new reboot schedule is enabled.                                                                                                                                                                                                                                                                                                                                                                 | false | true (ByPropertyName) |                                                                                        |
| 频率                    | Frequency with which this schedule runs (either Weekly or Daily).                                                                                                                                                                                                                                                                                                                                                             | false | true (ByPropertyName) |                                                                                        |
| RestrictToTag         | If set the reboot schedule only applies to machines in the desktop group with the specified tag.                                                                                                                                                                                                                                                                                                                              | false | true (ByPropertyName) |                                                                                        |
| StartTime             | Time of day at which the scheduled reboot cycle starts (HH:MM).                                                                                                                                                                                                                                                                                                                                                               | false | true (ByPropertyName) |                                                                                        |
| WarningDuration       | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | true (ByPropertyName) |                                                                                        |
| WarningMessage        | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot.                                                                                                                                                                                                         | false | true (ByPropertyName) |                                                                                        |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning.                                                                                                                                                                                  | false | true (ByPropertyName) |                                                                                        |
| WarningTitle          | The window title used when showing the warning message in user sessions on a machine scheduled for reboot.                                                                                                                                                                                                                                                                                                                    | false | true (ByPropertyName) |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                               | false | false                 |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                            | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.RebootScheduleV2

## 示例

### 示例 1

    C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "02:00" -Enabled $true -RebootDuration 120
    

Description  
\---\---\-----  
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 2 AM and 4 AM.

### 示例 2

    C:\PS> New-BrokerRebootScheduleV2 -Name 'Saturday reboots' -DesktopGroupUid 17 -Frequency Weekly -Day Saturday -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
    

Description  
\---\---\-----  
Schedules the machines in the desktop group having Uid 17 to be rebooted every Saturday night between 1 AM and 5 AM. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.

### 示例 3

    C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
    

Description  
\---\---\-----  
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.

### 示例 4

    C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5 -RestrictToTag 'Daily Reboot'
    

Description  
\---\---\-----  
Schedules only machines with the tag 'Daily Reboot' in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.