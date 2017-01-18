# Get-BrokerDesktopUsage

Get usage history of desktop groups.

## 语法

    Get-BrokerDesktopUsage [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-InUse <Int32>] [-Timestamp <DateTime>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns information, recorded by the broker on an hourly basis, about the number of desktops in use for each desktop group. Analyzing the historical usage records can give some guidance on usage patterns and help choosing idle pool settings.

Without parameters, Get-BrokerDesktopUsage returns the first 250 records. By using parameters, you can be more selective about the records that are returned.

To retrieve more than the default 250 records, use the -MaxRecordCount parameter. To select data for a specific desktop group, use either the -DesktopGroupName or -DesktopGroupUid parameters.

See the examples for this cmdlet and about_Broker_Filtering for details of how to perform advanced filtering.

\---\---\---\---\---\---\---\----- BrokerDesktopUsage Object Desktop usage object contains information to tell how many desktops in a desktop group are in use at a given time (identified by a timestamp).

    -- DesktopGroupUid (System.Int32)
       Uid of the desktop group that the usage data corresponds to.
    
    -- InUse (System.Int32)
       Specifies how many desktop are in use at the time the timestamp corresponds to.
    
    -- Timestamp (System.DateTime)
       Date and time the desktop usage information corresponds to.
    

## 相关命令

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DesktopGroupName       | Gets usage records for the named desktop group or for multiple desktop groups if wildcards have been specified.                                                                  | false | false |                                                                                        |
| DesktopGroupUid        | Gets usage records for a specific desktop group.                                                                                                                                 | false | false |                                                                                        |
| InUse                  | Gets usage records where the in-use count matches the specified value. This is useful when checking for zero or when used inside a -Filter expression.                           | false | false |                                                                                        |
| Timestamp              | Gets usage records that occurred at the given time.  
In general, Citrix recommends, using -Filter and relative comparisons. For a demonstration, see the examples.              | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

You cannot pipe objects to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.DesktopUsage

Get-BrokerDesktopUsage returns an object for each matching record.## Notes Desktop usage information is automatically deleted after 7 days.

## 示例

### 示例 1

    C:\PS> Get-BrokerDesktopUsage -DesktopGroupName TestGroup -MaxRecordCount 24 -SortBy '-Timestamp' | ft -a @{Name='Time';Expression={'{0:t}' -f $_.Timestamp}},InUse
    

Description  
\---\---\-----  
Returns the last 24 hours of usage information for desktop group TestGroup, formatting it as two columns labeled Time and InUse.

### 示例 2

    C:\PS> $d = Get-Date -Hour 0 -Minute 0 -Second 0
    C:\PS> Get-BrokerDesktopUsage -Filter { DesktopGroupName -eq 'TestGroup' -and Timestamp -ge $d }
    

Description  
\---\---\-----  
Returns today's usage information for desktop group TestGroup.

### 示例 3

    C:\PS> $dg = Get-BrokerDesktopGroup TestGroup
    C:\PS> Get-BrokerDesktopUsage -DesktopGroupUid $dg.Uid | Select Timestamp,InUse,@{Name='Percent';Expression={'{0:P0}' -f ($_.InUse / $dg.TotalDesktops)}}
    

Description  
\---\---\-----  
Retrieves the usage history for desktop group TestGroup and adds a column showing the number of desktops in that group in use, as a percentage.