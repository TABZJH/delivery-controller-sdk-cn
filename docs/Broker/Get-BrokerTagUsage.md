# Get-BrokerTagUsage

Produces a usage report for one or more tags.

## 语法

    Get-BrokerTagUsage [-TagUid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerTagUsage [[-TagName] <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns one BrokerTagUsage for each input tag. Each BrokerTagUsage object summarizes the tag's usage throughout the site.

\---\---\---\---\---\---\---\----- BrokerTagUsage Object Each BrokerTagUsage object summarizes on the usage of a single Tag.

    -- TaggedApplicationGroups (System.Int32)
       The number of application groups that are tagged with this tag and that are visible to the calling delegated administrator.
    
    -- TaggedApplications (System.Int32)
       The number of applications that are tagged with this tag and that are visible to the calling delegated administrator.
    
    -- TaggedDesktopGroups (System.Int32)
       The number of desktop groups that are tagged with this tag and that are visible to the calling delegated administrator.
    
    -- TaggedMachines (System.Int32)
       The number of machines that are tagged with this tag and that are visible to the calling delegated administrator.
    
    -- TagName (System.String)
       The name of the Tag.
    
    -- TagRestrictedApplicationGroups (System.Int32)
       The number of application groups that have this tag restriction and that are visible to the calling delegated administrator.
    
    -- TagRestrictedEntitlementPolicyRules (System.Int32)
       The number of desktop rules in the site's entitlement policy that have this tag restriction and that are visible to the calling delegated administrator.
    
    -- TagRestrictedRebootSchedules (System.Int32)
       The number of reboot schedules that have this tag restriction.
    
    -- TagUid (System.Int32)
       The Uid of the Tag.
    
    -- TagUUID (System.Guid)
       The UUID associated to the Tag.
    
    -- TotalTaggedObjects (System.Int32)
       The total number of objects that are tagged with this tag.
    
    -- TotalTagRestrictedObjects (System.Int32)
       The total number of objects that have this tag restriction.
    
    -- UnknownTaggedObjects (System.Int32)
       The number of objects of all types that are tagged with this tag and that are *not* visible to the calling delegated administrator.
    
    -- UnknownTagRestrictedObjects (System.Int32)
       The number of objects of all types that have this tag restriction and that are *not* visible to the calling delegated administrator.
    

## 相关命令

- [Get-BrokerTag](Get-BrokerTag.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| TagUid                 | Report on the tag identified by TagUid.                                                                                                                                          | true  | false |                                                                                        |
| TagName                | Report on the tag identified by TagName.                                                                                                                                         | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.TagUsage

Summarizes the usage of a single tag.## Notes If a tag is applied to an object, but that object would not be visible to the calling delegated administrator via the corresponding Get-Broker* cmdlet, then the object is not counted as an object of that type, but is instead reported as an 'unknown' object.  
For example, suppose that the caller has invoked Get-BrokerTagUsage MyTag, and that there are three desktop groups and no other objects tagged with MyTag. Two of the desktop groups are visible to the caller, but the other is not. In this case, TotalTaggedObjects is 3, TaggedDesktopGroups is 2, and UnknownTaggedObjects is 1.

## 示例

### 示例 1

    Get-BrokerTagUsage
    

Description  
\---\---\-----  
Reports on the usage of all tags in the site.

### 示例 2

    Get-BrokerTagUsage MyTag
    

Description  
\---\---\-----  
Reports on the usage of the tag MyTag.