# Get-BrokerUser

Gets broker users configured for this site.

## 语法

    Get-BrokerUser -SID <String> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerUser [[-Name] <String>] [-FullName <String>] [-HomeZoneName <String>] [-HomeZoneUid <Guid>] [-UPN <String>] [-ApplicationGroupUid <Int32>] [-ApplicationUid <Int32>] [-SessionLingerDesktopGroupUid <Int32>] [-SessionPreLaunchDesktopGroupUid <Int32>] [-MachineUid <Int32>] [-PrivateDesktopUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieve broker users matching the specified criteria. If no parameters are specified this cmdlet enumerates all broker users.

For information about advanced filtering options, see about_Broker_Filtering.

\---\---\---\---\---\---\---\----- BrokerUser Object The BrokerUser object represents a single instance of an user. It contains the following properties:

    -- FullName (System.String)
       The full name of an user
    
    -- HomeZoneName (System.String)
       Name of home zone associated with user
    
    -- HomeZoneUid (System.Guid?)
       Home zone associated with this user
    
    -- Name (System.String)
       The name of an user
    
    -- SID (System.String)
       The SID of an user
    
    -- UPN (System.String)
       The UPN of an user
    

## 相关命令

- [Add-BrokerUser](Add-BrokerUser.html)
- [Remove-BrokerUser](Remove-BrokerUser.html)

## 参数

| 名称                              | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| SID                             | Gets the broker user with the specified SID property value.                                                                                                                      | true  | false |                                                                                        |
| 名称                              | Gets the broker user with the specified Name property.                                                                                                                           | false | false |                                                                                        |
| FullName                        | Gets the broker user with the specified FullName property.                                                                                                                       | false | false |                                                                                        |
| HomeZoneName                    | Gets user/group accounts having a home zone preference matching the specified name.                                                                                              | false | false |                                                                                        |
| HomeZoneUid                     | Gets user/group accounts having a home zone preference matching the specified UID.                                                                                               | false | false |                                                                                        |
| UPN                             | Gets the broker user with the specified UPN property value.                                                                                                                      | false | false |                                                                                        |
| ApplicationGroupUid             | Gets broker users associated with the application group with the specified Uid.                                                                                                  | false | false |                                                                                        |
| ApplicationUid                  | Gets broker users associated with the application with the specified Uid.                                                                                                        | false | false |                                                                                        |
| SessionLingerDesktopGroupUid    | Gets broker users associated with the desktop group session linger settings with the specified Uid.                                                                              | false | false |                                                                                        |
| SessionPreLaunchDesktopGroupUid | Gets broker users associated with the desktop group session pre-launch settings with the specified Uid.                                                                          | false | false |                                                                                        |
| MachineUid                      | Gets broker users associated with the broker machine with the specified Uid.                                                                                                     | false | false |                                                                                        |
| PrivateDesktopUid               | Gets broker users associated with the private desktop with the specified Uid.                                                                                                    | false | false |                                                                                        |
| ReturnTotalRecordCount          | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount                  | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                              | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                          | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                             | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                              | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress                    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.User

Get-BrokerUser returns an object for each matching broker user.

## 示例

### 示例 1

    Get-BrokerUser DOMAIN7\*
    

Description  
\---\---\-----  
Get all broker user objects with names matching the supplied pattern

### 示例 2

    $pdt = Get-BrokerPrivateDesktop DOMAIN\MACHINENAME\n
                  Get-BrokerUser -PrivateDesktopUid $pdt.Uid
    

Description  
\---\---\-----  
Get all broker user objects added to the specified private desktop