# Get-BrokerConnectionLog

Get entries from the site's session connection log.

## 语法

    Get-BrokerConnectionLog [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerConnectionLog [[-MachineName] <String>] [-BrokeringTime <DateTime>] [-BrokeringUserName <String>] [-BrokeringUserUPN <String>] [-ConnectionFailureReason <ConnectionFailureReason>] [-Disconnected <Boolean>] [-EndTime <DateTime>] [-EstablishmentTime <DateTime>] [-MachineDNSName <String>] [-MachineUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets connection log entries matching the specified criteria. If no parameters are specified all connection log entries are returned.

The session connection log contains entries describing each brokered connection, or reconnection, attempt to a session in the site.

Each log entry describes a single connection brokering attempt to a new or existing session within the site. A single session can have multiple entries in the connection log, for example where the end user brokers a connection to a new session, disconnects and later brokers a reconnection. Conversely, other sessions may have none (e.g. console sessions).

By default connection log entries are removed after 48 hours.

For information about advanced filtering options when using the -Filter parameter, see about_Broker_Filtering; for information about machines, see about_Broker_Machines.

\---\---\---\---\---\---\---\----- BrokerConnectionLog Object The BrokerConnectionLog object represents a single brokered connection attempt to a new or existing session on a machine in the site. 其中包含以下属性：

    -- BrokeringTime (System.DateTime)
       The time at which the connection attempt was made.
    
    -- BrokeringUserName (System.String)
       The name of the user making the connection (in DOMAIN\User format).
    
    -- BrokeringUserUPN (System.String)
       The name of the user making the connection (in user@upndomain.com format).
    
    -- ConnectionFailureReason (Citrix.Broker.Admin.SDK.ConnectionFailureReason?)
       The status of the connection attempt. A value of None indicates that the connection was successfully established, $null that the attempt is still in progress, and other values indicate that the attempt failed for the specified reason.
    
    -- Disconnected (System.Boolean?)
       Indicates if the connection was ended by disconnection (True), logoff or establishment failure (False), or is still active ($null).
    
    -- EndTime (System.DateTime?)
       The time at which the connection ended. If the connection ended by disconnection, the underlying machine session would still exist in a disconnected state.
    
    -- EstablishmentTime (System.DateTime?)
       The time at which the connection was successfully established. The value is $null if the connection attempt failed or is still in progress.
    
    -- MachineDNSName (System.String)
       The name of the machine to which the connection was made (in machine@dnsdomain.com form).
    
    -- MachineName (System.String)
       The name of the machine to which the connection was made (in DOMAIN\Machine format).
    
    -- MachineUid (System.Int32)
       The UID of the machine to which the connection was made.
    
    -- Uid (System.Int64)
       The UID of the connection log entry itself.
    

## 相关命令

## 参数

| 名称                      | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                     | Gets a specific connection log entry identified by its UID.                                                                                                                      | true  | false |                                                                                        |
| MachineName             | Gets connection log entries for the specified machines (in DOMAIN\Machine format).                                                                                              | false | false |                                                                                        |
| BrokeringTime           | Gets connection log entries with a specified brokering time. For more flexibility when searching on brokering time use the -Filter parameter.                                    | false | false |                                                                                        |
| BrokeringUserName       | Gets connection log entries for the specified users (in DOMAIN\User format).                                                                                                    | false | false |                                                                                        |
| BrokeringUserUPN        | Gets connection log entries for the specified users (in user@upndomain.com format).                                                                                              | false | false |                                                                                        |
| ConnectionFailureReason | Gets connection log entries which failed for the specified reason.                                                                                                               | false | false |                                                                                        |
| 已断开连接                   | Gets connection log entries with the specified disconnection status, that is, whether the connection was disconnected, or logged-off.                                            | false | false |                                                                                        |
| EndTime                 | Gets connection log entries with the specified end time. For more flexibility when searching on end time use the -Filter parameter.                                              | false | false |                                                                                        |
| EstablishmentTime       | Gets connection log entries with the specific establishment time. For more flexibility when searching on establishment time use the -Filter parameter.                           | false | false |                                                                                        |
| MachineDNSName          | Gets connection log entries for the specified machines (in machine@dnsdomain.com format).                                                                                        | false | false |                                                                                        |
| MachineUid              | Gets connection log entries for a specific machine identified by its UID.                                                                                                        | false | false |                                                                                        |
| ReturnTotalRecordCount  | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount          | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                      | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                  | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                     | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                      | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress            | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.ConnectionLog

An entry from the connection log.

## 示例

### 示例 1

    C:\PS> $when = [DateTime]::Now - [TimeSpan]::FromMinutes(30)
    C:\PS> Get-BrokerConnectionLog -Filter {BrokeringTime -gt $when} -SortBy '+MachineName,-EndTime'
    

Description  
\---\---\-----  
Gets all connection log entries for sessions brokered in the past 30 minutes, ordered first by machine name (ascending), then by session end time (descending).