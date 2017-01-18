# Get-BrokerConfigurationSlot

Gets configuration slots configured for this site.

## 语法

    Get-BrokerConfigurationSlot [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerConfigurationSlot [[-Name] <String>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Get the list of configuration slots defined for this site. Each configuration slot determines a collection of related settings that can be specified in a machine configuration associated with this slot.

For example, a configuration slot may be defined to configure only "User Profile Manager" settings.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerConfigurationSlot Object The configuration slot object returned represents a named collection of related settings.

    -- Description (System.String)
       Optional description of this configuration slot.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       A map of metadata associated with this configuration slot.
    
    -- Name (System.String)
       Unique name of this configuration slot.
    
    -- SettingsGroup (System.String)
       The encoded identity of the settings group that every setting in the associated machine configuration instances must belong to.
    
    -- Uid (System.Int32)
       Unique Uid of this configuration slot.
    

## 相关命令

- [New-BrokerConfigurationSlot](New-BrokerConfigurationSlot.html)
- [Remove-BrokerConfigurationSlot](Remove-BrokerConfigurationSlot.html)
- [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Get only the configuration slot with the specified unique identifier.                                                                                                            | true  | false |                                                                                        |
| 名称                     | Get only the configuration slot with the specified name.                                                                                                                         | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.ConfigurationSlot

Get-BrokerConfigurationSlot returns an object for each matching slot.

## 示例

### 示例 1

    Get-ConfigurationSlot
    

Description  
\---\---\-----  
Retrieves every configuration slot.

### 示例 2

    Get-ConfigurationSlot -Name "AppV"
    

Description  
\---\---\-----  
Retrieves the configuration slot named "AppV".