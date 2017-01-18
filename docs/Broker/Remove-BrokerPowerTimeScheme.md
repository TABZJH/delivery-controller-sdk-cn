# Remove-BrokerPowerTimeScheme

Deletes an existing power time scheme.

## 语法

    Remove-BrokerPowerTimeScheme [-InputObject] <PowerTimeScheme[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerPowerTimeScheme [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerPowerTimeScheme cmdlet deletes a power time scheme from the system, and leaves the days that the time scheme used to cover for the associated desktop group as defaulting to all hours off-peak and all hours with pool size of -1.

Each power time scheme is associated with a particular desktop group, and covers one or more days of the week, defining which hours of those days are considered peak times and which are off-peak times. In addition, the time scheme defines a pool size value for each hour of the day for the days of the week covered by the time scheme. No one desktop group can be associated with two or more time schemes that cover the same day of the week.

For more information about the power policy mechanism and pool size management, see 'help about_Broker_PowerManagement'.

## 相关命令

- [Get-BrokerPowerTimeScheme](Get-BrokerPowerTimeScheme.html)
- [Set-BrokerPowerTimeScheme](Set-BrokerPowerTimeScheme.html)
- [New-BrokerPowerTimeScheme](New-BrokerPowerTimeScheme.html)
- [Rename-BrokerPowerTimeScheme](Rename-BrokerPowerTimeScheme.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The power time scheme to be deleted.                                                                                                                                            | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the power time scheme to be deleted.                                                                                                                                | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.PowerTimeScheme

The power time scheme to be deleted.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerPowerTimeScheme -Name 'Development Weekdays'
    

Description  
\---\---\-----  
Deletes the power time scheme named 'Development Weekdays'.

### 示例 2

    C:\PS> Get-BrokerPowerTimeScheme -DesktopGroupUid (Get-BrokerDesktopGroup -name 'Finance desk1').Uid  | Remove-BrokerPowerTimeScheme
    

Description  
\---\---\-----  
Deletes all power time schemes for the desktop group named 'Finance desk1'.