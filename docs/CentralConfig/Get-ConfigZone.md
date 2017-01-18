# Get-ConfigZone

Gets zones configured for this site.

## 语法

    Get-ConfigZone [[-Name] <String>] [-Uid <Guid>] [-ControllerName <String>] [-ControllerSid <String>] [-Description <String>] [-ExternalUid <Guid>] [-IsPrimary <Boolean>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves zones matching the specified criteria. If no parameters are specified all zones will be returned.

## 相关命令

- [New-ConfigZone](New-ConfigZone.html)
- [Set-ConfigZone](Set-ConfigZone.html)
- [Rename-ConfigZone](Rename-ConfigZone.html)
- [Remove-ConfigZone](Remove-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Set-ConfigService](Set-ConfigService.html)

## 参数

| 名称                     | 说明                                                                                                                                                    | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| 名称                     | Gets zones with the specified name.                                                                                                                   | false | true (ByValue, ByPropertyName) |                                       |
| UID                    | Gets the zone with the specified UID.                                                                                                                 | false | true (ByPropertyName)          |                                       |
| ControllerName         | Gets the zone that contains a specified Controller identified by Name.                                                                                | false | false                          |                                       |
| ControllerSid          | Gets the zone that contains a specified Controller identified by SID.                                                                                 | false | false                          |                                       |
| 说明                     | Gets zones with the specified description.                                                                                                            | false | false                          |                                       |
| ExternalUid            | Specifies the ExternalUid of the zone. This is used for cloud sites to link with the Citrix Resource Location.                                        | false | false                          |                                       |
| IsPrimary              | Gets zones with the specified value of the IsPrimary flag. If true, only the primary zone may be returned; if false, all other zones may be returned. | false | false                          |                                       |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                             | false | false                          |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                | false | false                          |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Config_Filtering for details.                                                    | false | false                          | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                          | false | false                          | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                 | false | false                          |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                              | false | false                          | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Config_Filtering for details.                                               | false | false                          |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                            | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Configuration.Sdk.Zone

Get-ConfigZone returns an object for each matching zone.

## 示例

### 示例 1

    C:\PS> Get-ConfigZone -Name "London"
    

Description  
\---\---\-----  
Gets the details of the zone with the specific name.

### 示例 2

    C:\PS> Get-ConfigZone -IsPrimary $false
    

Description  
\---\---\-----  
Lists all non-primary zones.