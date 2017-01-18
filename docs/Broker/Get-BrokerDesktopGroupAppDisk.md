# Get-BrokerDesktopGroupAppDisk

Gets the AppDisks that are being used by desktop group

## 语法

    Get-BrokerDesktopGroupAppDisk [[-DesktopGroupName] <String>] [-AppDiskUid <Guid>] [-AppDnaCompatibility <AppDnaCompatibility>] [-DesktopGroupUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerDesktopGroupAppDisk cmdlet returns all the AppDisks that are currently being used by the desktop groups and if they are compatible with their desktop group

\---\---\---\---\---\---\---\----- BrokerDesktopGroupAppDisk Object The BrokerDesktopGroupAppDisk object represents a single instance of a desktop group and AppDisk and if they are compatible

    -- AppDiskUid (System.Guid)
       The Uid of the AppDisk
    
    -- AppDnaCompatibility (Citrix.Broker.Admin.SDK.AppDnaCompatibility?)
       Specifies if the AppDisk is compatible with the desktop group
    
    -- DesktopGroupName (System.String)
       The name of the desktop group
    
    -- DesktopGroupUid (System.Int32)
       The Uid of the desktop group
    

## 相关命令

- [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DesktopGroupName       | Gets only the entries that match the specified Desktop Group Name                                                                                                                | false | false |                                                                                        |
| AppDiskUid             | Gets only the entries that match the specified AppDisk Uid                                                                                                                       | false | false |                                                                                        |
| AppDnaCompatibility    | Gets only the entries that match the specified AppDnaCompatibility                                                                                                               | false | false |                                                                                        |
| DesktopGroupUid        | Gets only the entries that match the specified Desktop Group Uid                                                                                                                 | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.DesktopGroupAppDisk

Returns an object for each enumerated Desktop Group and AppDisk combination.

## 示例

### 示例 1

    C:\PS> Get-BrokerDesktopGroupAppDisk -DesktopGroupName MyGroup
    

Description  
\---\---\-----  
Gets all the AppDisks that are assocated to the desktop group MyGroup