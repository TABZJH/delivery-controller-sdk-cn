# Remove-BrokerUserZonePreference

Removes any zone preference associated with a user/group account in this site

## 语法

    Remove-BrokerUserZonePreference [-InputObject] <UserZonePreference[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerUserZonePreference [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-BrokerUserZonePreference cmdlet removes any preferred home zone associated with a user/group account.

Removing a home preference means that the account no longer has an influence on any choice of zone used for resource launches.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The account zone preference to be removed.                                                                                                                                      | true  | true (ByValue)        |                                                                                        |
| 名称           | The name of the user/group account whose home zone preference is to be removed.                                                                                                 | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.UserZonePreference

The account zone preference to be removed.

## 返回值

### 无

## 示例

### 示例 1

    Remove-BrokerUserZonePreference APAC\sales
    

Description  
\---\---\-----  
Removes any home zone preference associated with the APAC\sales account for this site.