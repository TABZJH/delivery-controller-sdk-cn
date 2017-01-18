# Get-BrokerUnconfiguredMachine

Gets machines that have registered but are not yet configured in this site.

## 语法

    Get-BrokerUnconfiguredMachine -SID <String> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerUnconfiguredMachine [[-MachineName] <String>] [-AgentVersion <String>] [-ControllerDNSName <String>] [-CurrentlyRegistered <Boolean>] [-DNSName <String>] [-FunctionalLevel <FunctionalLevel>] [-LastDeregistrationTime <DateTime>] [-OSType <String>] [-OSVersion <String>] [-SessionSupport <SessionSupport>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieve machines matching the specified criteria, where the machine has or was previously registered with a controller in the site, but the machine has not yet been configured to be part of the site. If no parameters are specified, this cmdlet enumerates all such machines that are currently registered.

See about_Broker_Filtering for information about advanced filtering options, and about_Broker_Machines for background information about machines.

\---\---\---\---\---\---\---\----- BrokerUnconfiguredMachine Object An unconfigured machine is a machine that has registered with the site but is not configured in either a desktop group or a catalog.

    -- AgentVersion (System.String)
       Version of the Citrix Virtual Delivery Agent (VDA) installed on the unconfigured machine.
    
    -- ControllerDNSName (System.String)
       The DNS name of the controller that the unconfigured machine is registered with. This property's value is null for machines that are no longer registered.
    
    -- CurrentlyRegistered (System.Boolean)
       True if the unconfigured machine is currently registered with the site, or false if the unconfigured machine is no longer registered with the site (but was registered at some point in the past).
    
    -- DNSName (System.String)
       The DNS name of the unconfigured machine.
    
    -- FunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?)
       The functional level of the unconfigured machine. This is determined by the version of the Citrix VDA software installed on the machine.
    
    -- LastDeregistrationTime (System.DateTime?)
       The time when the unconfigured machine last deregistered with the Citrix Broker Service.
    
    -- MachineName (System.String)
       The machine name of the unconfigured machine in the form domain\machine.
    
    -- OSType (System.String)
       The type of operating system installed on the unconfigured machine.
    
    -- OSVersion (System.String)
       The version of the operating sysetem installed on the unconfigured machine.
    
    -- SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport?)
       The session support of the unconfigured machine. Valid values are:
       SingleSession, MultiSession
    
    -- SID (System.String)
       Security identifier of the unconfigured machine.
    

## 相关命令

- [Get-BrokerMachine](Get-BrokerMachine.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                  | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| SID                    | Gets machines by their machine SID.                                                                                                                                                                 | true  | false |                                                                                        |
| MachineName            | Gets machines by their machine name (in the form domain\machine).                                                                                                                                  | false | false |                                                                                        |
| AgentVersion           | Gets machines with a specific Virtual Desktop Agent version.                                                                                                                                        | false | false |                                                                                        |
| ControllerDNSName      | Gets machines by the DNS name of the controller they are registered with.                                                                                                                           | false | false |                                                                                        |
| CurrentlyRegistered    | Gets machines by whether they are currently registered with the site. If there is no CurrentlyRegistered filter, then the default is to return unconfigured machines that are currently registered. | false | false |                                                                                        |
| DNSName                | Gets machines by their DNS name.                                                                                                                                                                    | false | false |                                                                                        |
| FunctionalLevel        | Gets machines with a specific FunctionalLevel.  
Valid values are L5, L7, L7_6                                                                                                                      | false | false |                                                                                        |
| LastDeregistrationTime | Gets machines by the time that they were last deregistered.                                                                                                                                         | false | false |                                                                                        |
| OSType                 | Gets machines by the type of operating system they are running.                                                                                                                                     | false | false |                                                                                        |
| OSVersion              | Gets machines by the version of the operating system they are running.                                                                                                                              | false | false |                                                                                        |
| SessionSupport         | Gets machines that have the specified session capability. Values can be:  
o SingleSession - Single-session only machine.  
o MultiSession - Multi-session capable machine.                         | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                    | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                        | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                               | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                            | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                             | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                              | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                  | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.UnconfiguredMachine

Get-BrokerUnconfiguredMachine returns an object for each matching machine## Notes It is generally better to compare dates and times using -Filter and relative comparisons. See about_Broker_Filtering and the examples in this topic for more information.

## 示例

### 示例 1

    C:\PS> Get-BrokerUnconfiguredMachine -Filter { ControllerDNSName -eq 'Controller1.domain.com' -and OSType -eq 'Windows XP Service Pack 3' }
    

Description  
\---\---\-----  
This command returns all unconfigured XP SP3 machines which are registered with the controller called 'Controller1.domain.com'.

### 示例 2

    C:\PS> Get-BrokerUnconfiguredMachine -CurrentlyRegistered $false
    

Description  
\---\---\-----  
This command returns all unconfigured machines which have registered with the site in the past, but which are not registered at present.

### 示例 3

    C:\PS> Get-BrokerUnconfiguredMachine -Filter { CurrentlyRegistered -eq $true -or CurrentlyRegistered -eq $false }
    

Description  
\---\---\-----  
This command returns all unconfigured machines which are currently registered with the site or which have registered with the site in the past.