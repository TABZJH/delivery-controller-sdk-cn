# Rename-BrokerRebootScheduleV2

Renames a reboot schedule.

## 语法

    Rename-BrokerRebootScheduleV2 [-InputObject] <RebootScheduleV2[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerRebootScheduleV2 [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerRebootScheduleV2 cmdlet changes the name of a reboot schedule. A reboot schedule cannot have the same name as another reboot schedule.

## 相关命令

- [Get-BrokerRebootScheduleV2](Get-BrokerRebootScheduleV2.html)
- [Set-BrokerRebootScheduleV2](Set-BrokerRebootScheduleV2.html)
- [New-BrokerRebootScheduleV2](New-BrokerRebootScheduleV2.html)
- [Remove-BrokerRebootScheduleV2](Remove-BrokerRebootScheduleV2.html)
- [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the reboot schedule to rename.                                                                                                                                        | true  | true (ByValue)        | 空值                                                                                     |
| 名称           | Specifies the name of the reboot schedule to rename.                                                                                                                            | true  | true (ByPropertyName) | 空值                                                                                     |
| NewName      | Specifies the new name for the reboot schedule.                                                                                                                                 | true  | false                 | 空值                                                                                     |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RebootScheduleV2

You can pipe reboot schedules into Rename-BrokerRebootScheduleV2.

## 返回值

### None or Citrix.Broker.Admin.SDK.RebootScheduleV2

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.RebootScheduleV2 object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerRebootScheduleV2 -Name "Old Name" -NewName "New Name"
    

Description  
\---\---\-----  
Renames the reboot schedule with name "Old Name" to "New Name".

### 示例 2

    C:\PS> Get-BrokerRebootScheduleV2 -Uid 1 | Rename-BrokerRebootScheduleV2 -NewName "New Name" -PassThru
    

Description  
\---\---\-----  
Renames reboot schedule with the Uid 1 to "New Name", showing the result.