# Get-BrokerMachineConfiguration

Gets machine configurations defined for this site.

## 语法

    Get-BrokerMachineConfiguration [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerMachineConfiguration [[-Name] <String>] [-ConfigurationSlotUid <Int32>] [-LeafName <String>] [-Metadata <String>] [-ApplicationUid <Int32>] [-DesktopGroupUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves machine configurations matching the specified criteria. If no parameters are specified this cmdlet enumerates all machine configurations.

Machine configurations contain binary arrays of settings data that are managed using SDK snap-ins. Each machine configuration is associated with a configuration slot and referenced by Name. The configuration slot restricts the settings that can be held by the machine configuration. For example, only configurations for Citrix User Profile Manager can be associated with the "User Profile Manager" slot.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerMachineConfiguration Object The machine configuration object returned represents a named collection of related settings values that are applied to a desktop group.

    -- ApplicationUids (System.Int32[])
       List of application Uids that this machine configuration has been added to.
    
    -- ConfigurationSlotUid (System.Int32)
       Uid of the associated configuration slot.
    
    -- Description (System.String)
       Optional description of the machine configuration.
    
    -- DesktopGroupUids (System.Int32[])
       List of desktop group Uids that this machine configuration has been added to.
    
    -- LeafName (System.String)
       Name of this machine configuration.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Map of metadata associated with this machine configuration.
    
    -- Name (System.String)
       Unique "SlotName\MachineConfigurationName" for this machine configuration.
    
    -- Policy (System.Byte[])
       A binary array of encoded settings.
    
    -- Uid (System.Int32)
       Uid of this machine configuration.
    

## 相关命令

- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
- [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
- [Remove-BrokerMachineConfiguration](Remove-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Get only the machine configuration with the specified unique identifier.                                                                                                         | true  | false |                                                                                        |
| 名称                     | Get only the machine configuration with the specified name.                                                                                                                      | false | false |                                                                                        |
| ConfigurationSlotUid   | Get only the machine configurations associated with the specified configuration slot.                                                                                            | false | false |                                                                                        |
| LeafName               | Get only the machine configurations that have the specified leaf name.                                                                                                           | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| ApplicationUid         | Get only the machine configurations that have been assigned to the specified application.                                                                                        | false | false |                                                                                        |
| DesktopGroupUid        | Get only the machine configurations that have been assigned to the specified desktop group.                                                                                      | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.MachineConfiguration

Get-BrokerMachineConfiguration returns an object for each matching machine configuration.

## 示例

### 示例 1

    Get-BrokerMachineConfiguration
    

Description  
\---\---\-----  
Retrieves a list of every defined machine configuration.

### 示例 2

    Get-BrokerMachineConfiguration -Name Receiver\Engineering
    

Description  
\---\---\-----  
Retrieves the machine configuration named "Receiver\Engineering".

### 示例 3

    Get-BrokerMachineConfiguration -Name UPM\*
    

Description  
\---\---\-----  
Retrieves a list of every machine configuration associated with the configuration slot named "UPM".

### 示例 4

    Get-BrokerMachineConfiguration -LeafName "Dept*"
    

Description  
\---\---\-----  
Retrieves a list of every machine configuration with a LeafName that starts with "Dept", regardless of the associated configuration slot.