# Get-BrokerHypervisorConnection

Gets hypervisor connections matching the specified criteria.

## 语法

    Get-BrokerHypervisorConnection [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerHypervisorConnection [[-Name] <String>] [-ExplicitPreferredController <Boolean>] [-HypHypervisorConnectionUid <Guid>] [-IsReady <Boolean>] [-MachineCount <Int32>] [-MaxAbsoluteActiveActions <Int32>] [-MaxAbsoluteNewActionsPerMinute <Int32>] [-MaxAbsolutePvdPowerActions <Int32>] [-MaxPercentageActiveActions <Int32>] [-MaxPvdPowerActionsPercentageOfDesktops <Int32>] [-Metadata <String>] [-PreferredController <String>] [-State <HypervisorConnectionState>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerHypervisorConnection cmdlet gets hypervisor connections matching the specified criteria. If no parameters are specified this cmdlet enumerates all hypervisor connections.

\---\---\---\---\---\---\---\----- BrokerHypervisorConnection Object The BrokerHypervisorConnection represents hypervisor connection object. It contains the following properties:

    -- Capabilities (System.String[])
       The set of capabilities as reported by the hypervisor.
    
    -- ExplicitPreferredController (System.Boolean?)
       Whether the PreferredController property was explicity set through the SDK or automatically chosen.
    
    -- HypHypervisorConnectionUid (System.Guid)
       The Guid that identifies the hypervisor connection.
    
    -- IsReady (System.Boolean)
       Indicates that the connection is ready to be used in the configuration of managed machines.
    
    -- MachineCount (System.Int32)
       Count of machines associated with this hypervisor connection.
    
    -- MaxAbsoluteActiveActions (System.Int32?)
       Maximum number of active power actions allowed at any one time (defined in the metadata named 'Citrix_Broker_MaxAbsoluteActiveActions' on the hypervisor connection in the Citrix Hosting Service).
    
    -- MaxAbsoluteNewActionsPerMinute (System.Int32?)
       Maximum number of new actions that can be fired off to the hypervisor in any one minute (defined in the metadata named 'Citrix_Broker_MaxAbsoluteNewActionsPerMinute' on the hypervisor connection in the Citrix Hosting Service).
    
    -- MaxAbsolutePvdPowerActions (System.Int32?)
       Maximum number of active PvD power actions allowed at any one time (defined in the metadata named 'Citrix_Broker_MaxAbsolutePvdPowerActions' on the hypervisor connection in the Citrix Hosting Service).
    
    -- MaxPercentageActiveActions (System.Int32?)
       Maximum percentage of machines on the connection that can have active power actions at any one time (defined in the metadata named 'Citrix_Broker_MaxPowerActionsPercentageOfDesktops' on the hypervisor connection in the Citrix Hosting Service).
    
    -- MaxPvdPowerActionsPercentageOfDesktops (System.Int32?)
       Maximum percentage of machines on the connection that can be in personal VDisk image preparation mode at any one time (defined in the metadata named 'Citrix_Broker_MaxPvdPowerActionsPercentageOfDesktops' on the hypervisor connection in the Citrix Hosting Service).
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Collection of all the metadata associated to the hypervisor connection.
    
    -- Name (System.String)
       The display name of the hypervisor connection.
    
    -- PreferredController (System.String)
       The name of the controller which is preferred to be used, when available, to perform all communication to the hypervisor. The name is in DOMAIN\machine form. A preferred controller may have been automatically chosen when the hypervisor connection was created.
    
    -- State (Citrix.Broker.Admin.SDK.HypervisorConnectionState)
       The state of the hypervisor connection.
    
    -- Uid (System.Int32)
       Unique internal identifier of hypervisor connection.
    

## 相关命令

- [New-BrokerHypervisorConnection](New-BrokerHypervisorConnection.html)
- [Remove-BrokerHypervisorConnection](Remove-BrokerHypervisorConnection.html)
- [Set-BrokerHypervisorConnection](Set-BrokerHypervisorConnection.html)

## 参数

| 名称                                     | 说明                                                                                                                                                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                                    | Gets the hypervisor connection with the specified internal id.                                                                                                                                                                                                                     | true  | false |                                                                                        |
| 名称                                     | Gets hypervisor connections with the specified name.                                                                                                                                                                                                                               | false | false |                                                                                        |
| ExplicitPreferredController            | Gets hypervisor connections based on whether their preferred controller was explicitly specified or not                                                                                                                                                                            | false | false |                                                                                        |
| HypHypervisorConnectionUid             | Gets hypervisor connections with the specified Guid.                                                                                                                                                                                                                               | false | false |                                                                                        |
| IsReady                                | Gets hypervisor connections with the specified value of the IsReady flag.                                                                                                                                                                                                          | false | false |                                                                                        |
| MachineCount                           | Gets hypervisor connections with the specified machine count.                                                                                                                                                                                                                      | false | false |                                                                                        |
| MaxAbsoluteActiveActions               | Gets hypervisor connections with the specified MaxAbsoluteActiveActions value.                                                                                                                                                                                                     | false | false |                                                                                        |
| MaxAbsoluteNewActionsPerMinute         | Gets hypervisor connections with the specified MaxAbsoluteNewActionsPerMinute value.                                                                                                                                                                                               | false | false |                                                                                        |
| MaxAbsolutePvdPowerActions             | Gets hypervisor connections with the specified MaxAbsolutePvdPowerActions value.                                                                                                                                                                                                   | false | false |                                                                                        |
| MaxPercentageActiveActions             | Gets hypervisor connections with the specified MaxPercentageActiveActions value.                                                                                                                                                                                                   | false | false |                                                                                        |
| MaxPvdPowerActionsPercentageOfDesktops | Gets hypervisor connections with the specified MaxPvdPowerActionsPercentageOfDesktops value.                                                                                                                                                                                       | false | false |                                                                                        |
| 元数据                                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                                                                          | false | false |                                                                                        |
| PreferredController                    | Gets hypervisor connections with the specified preferred controller. Specify the SAM name of the controller.                                                                                                                                                                       | false | false |                                                                                        |
| 状态                                     | Gets hypervisor connections with the specified connection state. Values can be can be:  
o Unavailable - The broker is unable to contact the hypervisor.  
o InMaintenanceMode - The hosting server is in maintenance mode.  
o On - The broker is in contact with the hypervisor. | false | false |                                                                                        |
| ReturnTotalRecordCount                 | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                                   | false | false | False                                                                                  |
| MaxRecordCount                         | 指定要返回的最大记录数。                                                                                                                                                                                                                                                                       | false | false | 250                                                                                    |
| 跳过                                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                              | false | false |                                                                                        |
| SortBy                                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                                           | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                                            | false | false |                                                                                        |
| 属性                                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                             | false | false |                                                                                        |
| AdminAddress                           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                 | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

## 返回值

### Citrix.Broker.Admin.SDK.HypervisorConnection

Get-BrokerHypervisorConnection returns an object for each matching hypervisor connection.

## 示例

### 示例 1

    c:\PS> $hvConn = Get-BrokerHypervisorConnection -Name "hvConnectionName"
    

Description  
\---\---\-----  
Gets a hypervisor connection by name.

### 示例 2

    c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "domainName\controllerName"
    

Description  
\---\---\-----  
Gets hypervisor connections by preferred controller.

### 示例 3

    c:\PS> $machine = Get-BrokerMachine -Uid $machineUid
    c:\PS> $hvConn = Get-BrokerHypervisorConnection -Uid $machine.HypervisorConnectionUid
    

Description  
\---\---\-----  
Gets hypervisor connection used by a (power managed) machine.