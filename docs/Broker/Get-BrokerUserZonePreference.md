# Get-BrokerUserZonePreference

Gets user/group accounts with zone preferences configured for this site

## 语法

    Get-BrokerUserZonePreference -SID <String> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerUserZonePreference [[-Name] <String>] [-FullName <String>] [-HomeZoneName <String>] [-HomeZoneUid <Guid>] [-UPN <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieve user/group account details with a home zone preference specified and matching the specified criteria. If no parameters are specified this cmdlet enumerates all account details with associated home zones preferences.

For information about advanced filtering options, see about_Broker_Filtering.

\---\---\---\---\---\---\---\----- BrokerUserZonePreference Object The BrokerUserZonePreference object represents a user/group account having an associated home zone preference to be used when launching desktop or application sessions. 其中包含以下属性：

    -- FullName (System.String)
       Full name of user/group account.
    
    -- HomeZoneName (System.String)
       Name of home zone preference associated with user/group account for this site.
    
    -- HomeZoneUid (System.Guid)
       Home zone preference associated with user/group account for this site.
    
    -- Name (System.String)
       SAM name of user group/account (domain\user).
    
    -- SID (System.String)
       SID of user/group account.
    
    -- UPN (System.String)
       UPN of user/group account (user@domain).
    

## 相关命令

- [New-BrokerUserZonePreference](New-BrokerUserZonePreference.html)
- [Set-BrokerUserZonePreference](Set-BrokerUserZonePreference.html)
- [Remove-BrokerUserZonePreference](Remove-BrokerUserZonePreference.html)
- [Get-BrokerUser](Get-BrokerUser.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| SID                    | Gets user/group accounts with a home zone preference and the specified SID.                                                                                                      | true  | false |                                                                                        |
| 名称                     | Gets user/group accounts with a home zone preference and the specified SAM name (domain\user).                                                                                  | false | false |                                                                                        |
| FullName               | Gets user/group accounts with a home zone preference and the specified full name.                                                                                                | false | false |                                                                                        |
| HomeZoneName           | Gets user/group accounts having a home zone preference with the specified name.                                                                                                  | false | false |                                                                                        |
| HomeZoneUid            | Gets user/group accounts having a home zone preference with the specified UID.                                                                                                   | false | false |                                                                                        |
| UPN                    | Gets user/group accounts with a home zone preference and the specified UPN (user@domain).                                                                                        | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.UserZonePreference

Get-BrokerUserZonePreference returns an object for each user/group account with a home zone preference.

## 示例

### 示例 1

    Get-BrokerUserZonePreference DOMAIN7\*
    

Description  
\---\---\-----  
Get all user/group accounts with a home zone preference whose names match the supplied pattern

### 示例 2

    Get-BrokerUserZonePreference -HomeZoneUid 79AD8059-05B7-4BAA-9369-5C74EF52D3EB
    

Description  
\---\---\-----  
Get all user/group accounts with the specified zone as their home zone preference.