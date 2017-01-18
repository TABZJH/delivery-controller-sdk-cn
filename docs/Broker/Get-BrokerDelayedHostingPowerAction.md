# Get-BrokerDelayedHostingPowerAction

Gets power actions that are executed after a delay.

## 语法

    Get-BrokerDelayedHostingPowerAction [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerDelayedHostingPowerAction [[-MachineName] <String>] [-Action <PowerManagementAction>] [-ActionDueTime <DateTime>] [-DNSName <String>] [-HostedMachineName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Finds all delayed power actions that match the specified search criteria.

\---\---\---\---\---\---\---\----- BrokerDelayedHostingPowerAction Object The BrokerDelayedHostingPowerAction object represents an instance of a power action that is executed after a delay. 其中包含以下属性：

    -- Action (Citrix.Broker.Admin.SDK.PowerManagementAction)
       The power action to apply to the machine. Possible values are ShutDown and Suspend.
    
    -- ActionDueTime (System.DateTime)
       The UTC time at which the power action is due to be queued for execution.
    
    -- DNSName (System.String)
       The fully qualified DNS name of the machine that the power action applies to.
    
    -- HostedMachineName (System.String)
       The hypervisor's name for the machine that the power action applies to.
    
    -- HypervisorConnectionUid (System.Int32)
       The unique identifier of the hypervisor connection that is associated with the target machine.
    
    -- MachineName (System.String)
       The name of the machine that the power action applies to, in the form domain\machine.
    
    -- Uid (System.Int64)
       The unique identifier of the power action.
    

## 相关命令

- [New-BrokerDelayedHostingPowerAction](New-BrokerDelayedHostingPowerAction.html)
- [Remove-BrokerDelayedHostingPowerAction](Remove-BrokerDelayedHostingPowerAction.html)
- [Remove-BrokerHostingPowerAction](Remove-BrokerHostingPowerAction.html)

## 参数

| 名称                       | 说明                                                                                                                                                                                  | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                      | Gets only the single action record whose ID matches the specified value.                                                                                                            | true  | false |                                                                                        |
| MachineName              | Gets only the records for actions that are for machines whose name (of the form domain\machine) matches the specified string.                                                      | false | false |                                                                                        |
| 操作                       | Gets only the records for actions with the specified action type.  
Valid values are Shutdown and Suspend.                                                                          | false | false |                                                                                        |
| ActionDueTime            | Gets only the records for actions due to be queued for execution at the specified time. This is useful with advanced filtering; for more information, see about_Broker_Filtering. | false | false |                                                                                        |
| DNSName                  | Gets only the records for actions that are for machines whose DNS name matches the specified string.                                                                                | false | false |                                                                                        |
| HostedMachineName        | Gets only the records for actions that are for machines whose Hosting Name (the machine name as understood by the hypervisor) matches the specified string.                         | false | false |                                                                                        |
| HypervisorConnectionName | Gets only the records for actions for machines hosted through a hypervisor connection whose name matches the specified string.                                                      | false | false |                                                                                        |
| HypervisorConnectionUid  | Gets only the records for actions for machines hosted through a hypervisor connection whose ID matches the specified value.                                                         | false | false |                                                                                        |
| ReturnTotalRecordCount   | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.    | false | false | False                                                                                  |
| MaxRecordCount           | 指定要返回的最大记录数。                                                                                                                                                                        | false | false | 250                                                                                    |
| 跳过                       | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                               | false | false |                                                                                        |
| SortBy                   | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                            | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                      | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                             | false | false |                                                                                        |
| 属性                       | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                              | false | false |                                                                                        |
| AdminAddress             | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                  | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.DelayedHostingPowerAction

Get-BrokerDelayedHostingPowerAction returns all delayed power actions that match the specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerDelayedHostingPowerAction
    

Description  
\---\---\-----  
Fetches records for all known delayed power actions that have not yet been queued for execution.