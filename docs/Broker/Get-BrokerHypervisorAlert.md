# Get-BrokerHypervisorAlert

Gets hypervisor alerts recorded by the controller.

## 语法

    Get-BrokerHypervisorAlert -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerHypervisorAlert [-HostingServerName <String>] [-HypervisorConnectionUid <Int32>] [-Metadata <String>] [-Metric <AlertMetric>] [-Severity <AlertSeverity>] [-Time <DateTime>] [-TriggerInterval <TimeSpan>] [-TriggerLevel <Double>] [-TriggerPeriod <TimeSpan>] [-TriggerValue <Double>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerHypervisorAlert cmdlet gets alert objects reported by the hypervisors that the controller is monitoring.

Without parameters, Get-BrokerHypervisorAlert gets all of the alerts recorded. Use parameters to select which alerts are returned.

Once you have configured suitable alerts in your hypervisor, and configured the controller with your hypervisor details (see New-BrokerHypervisorConnection), the controller monitors each hypervisor for new alerts.

Four hypervisor alert metrics are recorded; these relate to the hypervisor host, not individual virtual machines: -- Cpu: Reports excessive CPU usage. -- Memory: Reports excessive memory usage. -- Network: Reports high network activity. -- Disk: Reports high disk activity.

Each alert also includes information about where and when the alert occurred, the severity of the alert (Red/Yellow), and the configuration of the triggered alert.

The following metrics are supported with these hypervisors: -- VMware ESX (Cpu, Memory, Network, Disk) -- Citrix XenServer (Cpu, Network) -- Microsoft Hyper-V (None)

\---\---\---\---\---\---\---\----- BrokerHypervisorAlert Object The BrokerHypervisorAlert represents a hypervisor alert object. It contains the following properties:

    -- HostingServerName (System.String)
       The name of the hypervisor hosting this machine.
    
    -- HypervisorConnectionUid (System.Int32)
       The Uid of the hypervisor connection that reported this alert.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this hypervisor alert.
    
    -- Metric (Citrix.Broker.Admin.SDK.AlertMetric)
       The metric this alert relates to: Cpu, Memory, Network or Disk.
    
    -- Severity (Citrix.Broker.Admin.SDK.AlertSeverity)
       Severity of the alert (Red or Yellow). Red is more serious than Yellow.
    
    -- Time (System.DateTime)
       Time that the alert occurred.
    
    -- TriggerInterval (System.TimeSpan?)
       Number of ticks (100ns) before the alert can be raised again.
    
    -- TriggerLevel (System.Double?)
       Threshold level that the alert was configured to trigger at.
    
    -- TriggerPeriod (System.TimeSpan?)
       Duration the value was above the trigger level.
    
    -- TriggerValue (System.Double?)
       The value of the monitored metric that triggered the alert.
    
    -- Uid (System.Int64)
       The unique internal identifier of this alert.
    

## 相关命令

- [New-BrokerHypervisorConnection](New-BrokerHypervisorConnection.html)

## 参数

| 名称                      | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                     | Gets the hypervisor alert with the specified UID.                                                                                                                                | true  | false |                                                                                        |
| HostingServerName       | Gets alerts for the specified hosting hypervisor server.                                                                                                                         | false | false |                                                                                        |
| HypervisorConnectionUid | Gets alerts for the specified hypervisor connection.                                                                                                                             | false | false |                                                                                        |
| 元数据                     | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| 指标                      | Gets alerts for a specified metric.  
Valid values are: Cpu, Memory, Network and Disk.                                                                                           | false | false |                                                                                        |
| 严重程度                    | Gets alerts with the specified severity.  
Valid values are: Red and Yellow.                                                                                                     | false | false |                                                                                        |
| 时间                      | Gets alerts that occurred at a specific time.  
You can also use -Filter and relative comparisons; see the examples for more information.                                        | false | false |                                                                                        |
| TriggerInterval         | Gets alerts with a specific trigger interval. This is the interval before the alert is raised again.                                                                             | false | false |                                                                                        |
| TriggerLevel            | Gets alerts with a specific trigger threshold level.                                                                                                                             | false | false |                                                                                        |
| TriggerPeriod           | Gets alerts with a specific trigger period. This is the duration the threshold level was exceeded for, prior to the alert triggering.                                            | false | false |                                                                                        |
| TriggerValue            | Gets the value of the monitored metric that triggered the alert.                                                                                                                 | false | false |                                                                                        |
| ReturnTotalRecordCount  | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount          | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                      | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                  | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                     | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                      | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress            | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

You cannot pipe objects to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.HypervisorAlert

Get-BrokerHypervisorAlert returns an object for each matching alert.

## 示例

### 示例 1

    C:\PS> Get-BrokerHypervisorAlert -HostingServerName TestHyp* -Severity Red
    

Description  
\---\---\-----  
Returns all serious (Red) alerts for any hosting server with a name that starts with 'TestHyp'.

### 示例 2

    C:\PS> Get-BrokerHypervisorAlert -Filter { Metric -eq 'Cpu' -and Time -ge '-1:0' }
    

Description  
\---\---\-----  
Returns all CPU usage alerts that occurred in the last hour.