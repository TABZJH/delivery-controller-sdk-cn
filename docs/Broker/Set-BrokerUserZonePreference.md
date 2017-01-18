# Set-BrokerUserZonePreference

Changes the zone preference associated with a user/group account in this site

## 语法

    Set-BrokerUserZonePreference [-InputObject] <UserZonePreference[]> [-PassThru] [-HomeZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerUserZonePreference [-Name] <String> [-PassThru] [-HomeZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerUserZonePreference cmdlet allows the preferred home zone for resources launched using the specified user/group account to be changed.

Subject to the configuration of the desktop groups in use, and the availability of machines in the preferred zone, desktops and applications are launched using machines in that zone where possible.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The account zone preference to be modified.                                                                                                                                     | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the user/group account whose home zone preference is to be changed.                                                                                                 | true  | true (ByPropertyName) |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| HomeZoneUid  | The home zone preference to be associated with the user/group account for this site.                                                                                            | false | false                 |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.UserZonePreference

The account zone preference to be modified.

## 返回值

### None or Citrix.Broker.Admin.SDK.UserZonePreference

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.UserZonePreference object.

## 示例

### 示例 1

    Set-BrokerUserZonePreference APAC\marketing -HomeZoneUid 2E885C02-6B65-47AA-8B03-E855BE2FF7D7
    

Description  
\---\---\-----  
Changes the preferred zone for resources launched by members of the APAC\marketing group account.