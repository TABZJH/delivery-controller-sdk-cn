# Get-BrokerTag

Gets one or more tags.

## 语法

    Get-BrokerTag [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerTag [[-Name] <String>] [-Description <String>] [-Metadata <String>] [-UUID <Guid>] [-ApplicationUid <Int32>] [-ApplicationGroupUid <Int32>] [-DesktopUid <Int32>] [-DesktopGroupUid <Int32>] [-MachineUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets tags that match all of the supplied criteria.

\---\---\---\---\---\---\---\----- BrokerTag Object The BrokerTag object represents a single instance of a Tag associated to other objects. It contains the following properties:

    -- Description (System.String)
       Description of the tag.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       The metadata for this command.
    
    -- Name (System.String)
       The name of the Tag
    
    -- Uid (System.Int32)
       The Uid of the Tag
    
    -- UUID (System.Guid)
       The UUID associated to the Tag
    

## 相关命令

- [Add-BrokerTag](Add-BrokerTag.html)
- [New-BrokerTag](New-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)
- [Rename-BrokerTag](Rename-BrokerTag.html)
- [Set-BrokerTag](Set-BrokerTag.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets the tag identified by Uid                                                                                                                                                   | true  | false |                                                                                        |
| 名称                     | Gets tags that match the specified name.                                                                                                                                         | false | false |                                                                                        |
| 说明                     | Gets tags with the specified description.                                                                                                                                        | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| UUID                   | Gets tags associated with a given UUID.                                                                                                                                          | false | false |                                                                                        |
| ApplicationUid         | Gets tags associated with the specified application.                                                                                                                             | false | false |                                                                                        |
| ApplicationGroupUid    | Get tags associated with the specified application group.                                                                                                                        | false | false |                                                                                        |
| DesktopUid             | Gets tags associated with the specified desktop.                                                                                                                                 | false | false |                                                                                        |
| DesktopGroupUid        | Gets tags associated with the specified desktop group.                                                                                                                           | false | false |                                                                                        |
| MachineUid             | Gets tags associated with the specified machine.                                                                                                                                 | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.Tag

Returns matching tags.

## 示例

### 示例 1

    C:\PS> Get-BrokerTag
    

Description  
\---\---\-----  
Enumerate all tags.

### 示例 2

    C:\PS> Get-BrokerTag -Uid 5
    

Description  
\---\---\-----  
Get a single specific tag with a Uid of 5.

### 示例 3

    C:\PS> $machine = Get-BrokerMachine DOMAIN\Machine
    C:\PS> Get-BrokerTag -MachineUid $machine.Uid
    

Description  
\---\---\-----  
Get tags associated with machine DOMAIN\Machine.