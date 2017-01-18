# New-BrokerUserZonePreference

Creates a zone preference for a user/group account in this site

## 语法

    New-BrokerUserZonePreference [-Name] <String> -HomeZoneUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerUserZonePreference [-SID] <String> -HomeZoneUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The New-BrokerUserZonePreference cmdlet specifies a preferred home zone for resources launched using the specified user/group account.

Subject to the configuration of the desktop groups in use, and the availability of machines in the preferred zone, desktops and applications are launched using machines in that zone where possible.

## 相关命令

- [Get-BrokerUserZonePreference](Get-BrokerUserZonePreference.html)
- [Set-BrokerUserZonePreference](Set-BrokerUserZonePreference.html)
- [Remove-BrokerUserZonePreference](Remove-BrokerUserZonePreference.html)
- [Get-BrokerUser](Get-BrokerUser.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 名称           | Name of the user/group account with which the new home zone preference is to be associated.                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| SID          | SID of the user/group account with which the new home zone preference is to be associated.                                                                                      | true  | true (ByPropertyName) |                                                                                        |
| HomeZoneUid  | The home zone preference to be associated with the user/group account.                                                                                                          | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.UserZonePreference

New-BrokerUserZonePreference returns the newly created zone preference object.

## 示例

### 示例 1

    $zp = New-BrokerUserZonePreference EMEA\sales -HomeZoneUid 2E885C02-6B65-47AA-8B03-E855BE2FF7D7
    

Description  
\---\---\-----  
Sets the preferred zone for resources launched by members of the EMEA\sales group account.