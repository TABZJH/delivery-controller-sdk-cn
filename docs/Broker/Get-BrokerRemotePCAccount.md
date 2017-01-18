# Get-BrokerRemotePCAccount

Get RemotePCAccount entries configured for this site.

## 语法

    Get-BrokerRemotePCAccount -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerRemotePCAccount [-AllowSubfolderMatches <Boolean>] [-CatalogUid <Int32>] [-OU <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves RemotePCAccounts matching the specified criteria. If no parameters are specified this cmdlet enumerates all RemotePCAccounts. Each RemotePCAccount object defines a set of machines either by machine name patterns or by where the machines are placed in Active Directory, and which RemotePC catalog the machines are to be associated with when they are discovered.

\---\---\---\---\---\---\---\----- BrokerRemotePCAccount Object RemotePCAccounts define a set of machines either by machine name patterns or by where the machines are placed in Active Directory, and which RemotePC catalog the machines are to be associated with when they are discovered.

    -- AllowSubfolderMatches (System.Boolean)
       Specifies whether machines subfolders of specified AD OUs are to be considered part of the RemotePCAccount.
    
    -- CatalogUid (System.Int32)
       The Uid of the RemotePC catalog to which machines in the RemotePCAccount automatically join during registration.
    
    -- MachinesExcluded (System.String[])
       A list of machines which are to be excluded from the RemotePCAccount. Wildcard matching is supported.
    
    -- MachinesIncluded (System.String[])
       A list of machines which are to be included in the RemotePCAccount. Wildcard matching is supported.
    
    -- OU (System.String)
       Machines within this specified AD OU are considered part of the RemotePCAccount, unless they are in they match the MachinesExcluded
    
    -- Uid (System.Int32)
       The Uid of the RemotePCAccount object.
    

## 相关命令

- [New-BrokerRemotePCAccount](New-BrokerRemotePCAccount.html)
- [Set-BrokerRemotePCAccount](Set-BrokerRemotePCAccount.html)
- [Remove-BrokerRemotePCAccount](Remove-BrokerRemotePCAccount.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets the RemotePCAccount with the specified unique ID.                                                                                                                           | true  | false |                                                                                        |
| AllowSubfolderMatches  | Gets RemotePCAccounts with the specified value of AllowSubfolderMatches.                                                                                                         | false | false |                                                                                        |
| CatalogUid             | Gets RemotePCAccounts belonging to the specified Remote PC catalog.                                                                                                              | false | false |                                                                                        |
| OU                     | Gets the RemotePCAccount with the specified OU.                                                                                                                                  | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.RemotePCAccount

Get-BrokerRemotePCAccount returns an object for each matching RemotePCAccount.

## 示例

### 示例 1

    C:\PS> Get-BrokerRemotePCAccount
    

Description  
\---\---\-----  
Find all RemotePCAccounts.

### 示例 2

    C:\PS> Get-BrokerRemotePCAccount -CatalogUid 42
    

Description  
\---\---\-----  
Find RemotePCAccounts belonging to Remote PC catalog 42.