# Get-BrokerPowerTimeScheme

Gets power management time schemes for desktop groups.

## 语法

    Get-BrokerPowerTimeScheme [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerPowerTimeScheme [[-Name] <String>] [-DesktopGroupUid <Int32>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Finds power time schemes matching the specified search criteria. Each desktop group in the site can have a number of power time schemes associated with it, and these time schemes control how the power states of machines in the group are managed.

If no search criteria are specified all power time schemes for all desktop groups are obtained.

Each power time scheme covers one or more days of the week, and defines which hours of those days are considered peak times and which are off-peak times. In addition, the time scheme defines a pool size value for each hour of the day for the days of the week covered by the time scheme. No one desktop group can be associated with two or more time schemes that cover the same day of the week.

For any day of the week not covered by any power time scheme, it is assumed that all hours are off-peak and no pool size management is required for any of the hours.

For more information about the power policy mechanism and pool size management, see 'help about_Broker_PowerManagement'.

\---\---\---\---\---\---\---\----- BrokerPowerTimeScheme Object The BrokerPowerTimeScheme object represents a power time scheme, defining peak/off-peak hours and idle pool sizes for desktop groups. 其中包含以下属性：

    -- DaysOfWeek (Citrix.Broker.Admin.SDK.TimeSchemeDays)
       The days of the week for which this scheme applies to (Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Weekdays, Weekend).
    
    -- DesktopGroupUid (System.Int32)
       The desktop group that this time scheme is for.
    
    -- DisplayName (System.String)
       The name of this time scheme, as displayed in the Studio console.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this power time scheme.
    
    -- Name (System.String)
       The unique name of this time scheme.
    
    -- PeakHours (System.Boolean[])
       A set of 24 boolean flag values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. If the flag is $true it means that the associated hour of the day is considered a peak time; if it is $false it means that it is considered off-peak.
    
    -- PoolSize (System.Int32[])
       A set of 24 integer values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. The value defines the number of machines (either as an absolute number or a percentage of the machines in the desktop group) that are to be maintained in a running state, whether they are in use or not. A value of -1 has special meaning: pool size management does not apply during such hours.
    
    -- PoolUsingPercentage (System.Boolean?)
       A boolean flag to indicate whether the integer values in the pool size array are to be treated as absolute values (if this value is $false) or as percentages of the number of machines in the desktop group (if this value is $true).
    
    -- Uid (System.Int32)
       Unique internal identifier of a time scheme.
    

## 相关命令

- [New-BrokerPowerTimeScheme](New-BrokerPowerTimeScheme.html)
- [Set-BrokerPowerTimeScheme](Set-BrokerPowerTimeScheme.html)
- [Remove-BrokerPowerTimeScheme](Remove-BrokerPowerTimeScheme.html)
- [Rename-BrokerPowerTimeScheme](Rename-BrokerPowerTimeScheme.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets only the power time scheme with the specified Uid.                                                                                                                          | true  | false |                                                                                        |
| 名称                     | Gets only power time schemes with the specified name.                                                                                                                            | false | false |                                                                                        |
| DesktopGroupUid        | Gets only the power time schemes associated with the specified desktop group.                                                                                                    | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.PowerTimeScheme

Get-BrokerPowerTimeScheme returns all power time schemes that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerPowerTimeScheme
    

Description  
\---\---\-----  
Fetches all known power time schemes for all desktop groups in the site.

### 示例 2

    C:\PS> Get-BrokerPowerTimeScheme -DesktopGroupUid ( Get-BrokerDesktopGroup 'Sales Desktops' ).Uid
    

Description  
\---\---\-----  
Fetches all the power time schemes for the desktop group called 'Sales Desktops'.