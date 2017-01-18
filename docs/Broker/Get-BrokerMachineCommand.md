# Get-BrokerMachineCommand

Get the list of commands queued for delivery to a desktop.

## 语法

    Get-BrokerMachineCommand -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerMachineCommand [-Category <String>] [-CommandName <String>] [-CompletionTime <DateTime>] [-MachineName <String>] [-MachineUid <Int32>] [-Metadata <String>] [-RequestTime <DateTime>] [-SendDeadline <TimeSpan>] [-SendDeadlineTime <DateTime>] [-SendTrigger <MachineCommandTrigger>] [-SessionUid <Int64>] [-State <MachineCommandState>] [-User <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Get the list of commands queued for delivery to a desktop. Commands are batched and can be configured to be delivered at various times during a desktop session's lifetime. Normally commands are sent within a few minutes of being queued, but it is also possible to queue a command for a user who is not currently logged on or a desktop that is currently switched off.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerMachineCommand Object The command object returned represents a command handled by a specific service on a desktop as determined by the Category property.

    -- Category (System.String)
       Category of the command.
    
    -- CommandData (System.Byte[])
       Additional binary data included when the command is sent.
    
    -- CommandName (System.String)
       Name of the command.
    
    -- CompletionTime (System.DateTime?)
       Time at which the command was sent, expired or canceled.
    
    -- DesktopGroupNames (System.String[])
       List of desktop group names that the command was restricted to.
    
    -- MachineName (System.String)
       Name of the machine this command is targeted at.
    
    -- MachineUid (System.Int32?)
       Unique ID of the machine this command is targeted at.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this command.
    
    -- RequestTime (System.DateTime)
       Time at which this command was created.
    
    -- SendDeadline (System.TimeSpan)
       Duration after which this command expires if it has not been sent yet.
    
    -- SendDeadlineTime (System.DateTime?)
       Time at which this command expires if it has not been sent yet.
    
    -- SendTrigger (Citrix.Broker.Admin.SDK.MachineCommandTrigger?)
       Event that triggers the sending of the command. Valid values are NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect.
    
    -- SessionUid (System.Int64?)
       Unique ID of the session this command is targeted at.
    
    -- State (Citrix.Broker.Admin.SDK.MachineCommandState)
       Indicates whether the command is pending, sent, expired or canceled.
    
    -- Synchronous (System.Boolean)
       Flag that indicates if this is a synchronous command.
    
    -- Uid (System.Int64)
       Unique identifier of this machine command.
    
    -- User (System.String)
       Name of the user this command is targeted at.
    

## 相关命令

- [New-BrokerMachineCommand](New-BrokerMachineCommand.html)
- [Remove-BrokerMachineCommand](Remove-BrokerMachineCommand.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Get only the command with the specified unique identifier.                                                                                                                       | true  | false |                                                                                        |
| 类别                     | Get only commands targeted to the specified service category.                                                                                                                    | false | false |                                                                                        |
| CommandName            | Get only commands with the specified command name.                                                                                                                               | false | false |                                                                                        |
| CompletionTime         | Get only commands that entered the Sent, Failed, Canceled or Expired state at the specified time.                                                                                | false | false |                                                                                        |
| MachineName            | Get only commands targeted to the specified machine.                                                                                                                             | false | false |                                                                                        |
| MachineUid             | Get only commands targeted to the specified machine.                                                                                                                             | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| RequestTime            | Get only commands that were requested at the specified time.                                                                                                                     | false | false |                                                                                        |
| SendDeadline           | Get only commands that expire after the specified time span.                                                                                                                     | false | false |                                                                                        |
| SendDeadlineTime       | Get only commands that have the specified deadline time.                                                                                                                         | false | false |                                                                                        |
| SendTrigger            | Get only commands that are due to be sent when the specified trigger occurs. Valid values are NextContact, Broker, LogOn, Logoff, Disconnect and Reconnect.                      | false | false |                                                                                        |
| SessionUid             | Get only commands targeted to the specified session.                                                                                                                             | false | false |                                                                                        |
| 状态                     | Get only commands in the specified state. Valid values are Pending, Sent, Failed, Canceled and Expired.                                                                          | false | false |                                                                                        |
| 用户                     | Get only commands targeted to the specified user.                                                                                                                                | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

No parameter is accepted from the input pipeline.

## 返回值

### Citrix.Broker.Admin.SDK.MachineCommand

Returns Command objects matching all specified selection criteria.

## 示例

### 示例 1

    Get-BrokerMachineCommand
    

Description  
\---\---\-----  
Returns all pending, canceled, expired and sent commands.

### 示例 2

    Get-BrokerMachineCommand -State Pending
    

Description  
\---\---\-----  
Returns all queued commands.