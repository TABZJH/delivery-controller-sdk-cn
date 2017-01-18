# Start-BrokerRebootCycle

Creates and starts a reboot cycle for each desktop group that contains machines from the specified catalog.

## 语法

    Start-BrokerRebootCycle [-InputObject] <Catalog[]> -RebootDuration <Int32> [-WarningDuration <Int32>] [-WarningTitle <String>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Start-BrokerRebootCycle cmdlet is used to create and start a reboot cycle for each desktop group that contains machines from the specified catalog. For a given desktop group, only the machines from the target catalog are rebooted and any machines from other catalogs are not rebooted.

Creating a reboot cycle for catalog ensures that all machines in the catalog are running the most recent image for the catalog and that all PvD image updates have been performed.

## 相关命令

- [Start-BrokerDesktopGroupRebootCycle](Start-BrokerDesktopGroupRebootCycle.html)
- [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)
- [Get-BrokerRebootCycle](Get-BrokerRebootCycle.html)

## 参数

| 名称                    | 说明                                                                                                                                                                                                                                                                                                                                                                                                                          | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject           | Creates a reboot cycle for each desktop group that contains machines from this input catalog SDK object. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects.                                                                                                                                                                                                              | true  | true (ByValue) |                                                                                        |
| RebootDuration        | Approximate maximum duration in minutes over which the reboot cycle runs.                                                                                                                                                                                                                                                                                                                                                   | true  | false          |                                                                                        |
| WarningDuration       | Time in minutes prior to a machine reboot at which a warning message is displayed in all user sessions on that machine. If the warning duration value is zero then no message is displayed. In some cases the time required to process a reboot cycle may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | false          |                                                                                        |
| WarningTitle          | The window title used when showing the warning message in user sessions on a machine scheduled for reboot.                                                                                                                                                                                                                                                                                                                  | false | false          |                                                                                        |
| WarningMessage        | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot.                                                                                                                                                                                                       | false | false          |                                                                                        |
| WarningRepeatInterval | Number of minutes to wait before showing the reboot warning message again.                                                                                                                                                                                                                                                                                                                                                  | false | false          |                                                                                        |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                             | false | false          |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                          | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

Catalogs may be specified through pipeline input. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects

## 返回值

### none

## 示例

### 示例 1

    C:\PS> Get-BrokerCatalog -Name "SampleCatalog" | Start-BrokerRebootCycle -RebootDuration 240 -WarningMessage "Save your work" -WarningDuration 15
    

Description  
\---\---\-----  
Starts a new reboot cycle for each desktop group containing machines from the catalog "SampleCatalog". Each reboot cycle has a duration of six hours. Fifteen minutes prior to rebooting a machine, the message "Save your work" is displayed in each active user session.

### 示例 2

    C:\PS> Get-BrokerCatalog -Name "SampleCatalog" | Start-BrokerRebootCycle -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
    

Description  
\---\---\-----  
Starts a new reboot cycle for each desktop group containing machines from the catalog "SampleCatalog". Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.