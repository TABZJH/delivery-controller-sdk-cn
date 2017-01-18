# Remove-BrokerRebootScheduleV2

Removes the reboot schedule.

## 语法

    Remove-BrokerRebootScheduleV2 [-InputObject] <RebootScheduleV2[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerRebootScheduleV2 [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerRebootScheduleV2 cmdlet is used to delete an existing reboot schedule.

## 相关命令

- [Get-BrokerRebootScheduleV2](Get-BrokerRebootScheduleV2.html)
- [Set-BrokerRebootScheduleV2](Set-BrokerRebootScheduleV2.html)
- [New-BrokerRebootScheduleV2](New-BrokerRebootScheduleV2.html)
- [Rename-BrokerRebootScheduleV2](Rename-BrokerRebootScheduleV2.html)
- [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The reboot schedule to be removed.                                                                                                                                              | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the reboot schedule to be removed.                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RebootScheduleV2

Reboot schedules may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Get-BrokerRebootScheduleV2 | Remove-BrokerRebootScheduleV2
    

Description  
\---\---\-----  
Deletes every reboot schedule.

### 示例 2

    C:\PS> Remove-BrokerRebootScheduleV2 12
    

Description  
\---\---\-----  
Deletes the reboot schedule having Uid 12.

### 示例 3

    C:\PS> Remove-BrokerRebootScheduleV2 -Name Accounting
    

Description  
\---\---\-----  
Deletes the reboot schedule named Accounting.