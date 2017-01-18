# Get-BrokerLease

Gets stored leases.

## 语法

    Get-BrokerLease [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerLease [[-Key] <String>] [-Expiration <DateTime>] [-LastModified <DateTime>] [-LeaseType <BrokerLeaseType>] [-OwnerSAMName <String>] [-OwnerSID <String>] [-OwnerUPN <String>] [-ZoneUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets leases filtered by specific Uid or Owner information.

\---\---\---\---\---\---\---\----- BrokerLease Object The BrokerLease object represents a single instance of a lease. It contains the following properties:

    -- Expiration (System.DateTime)
       The expiration time of the lease.
    
    -- Key (System.String)
       The SHA1 representation of the lease key.
    
    -- LastModified (System.DateTime)
       The modification time of the lease.
    
    -- LeaseType (Citrix.Broker.Admin.SDK.BrokerLeaseType)
       The type of lease.
    
    -- OwnerSAMName (System.String)
       The SAM name of the user associated with the lease.
    
    -- OwnerSID (System.String)
       The SID of the user associated with the lease.
    
    -- OwnerUPN (System.String)
       The UPN of the user associated with the lease.
    
    -- Uid (System.Int64)
       The UID of the lease itself.
    
    -- Value (System.String)
       The serialized lease data in XML.
    
    -- ZoneName (System.String)
       Name of the Zone this resource belongs to.
    
    -- ZoneUid (System.Guid)
       Uid of the Zone this resource belongs to.
    

## 相关命令

- [Remove-BrokerLease](Remove-BrokerLease.html)
- [Update-BrokerLocalLeaseCache](Update-BrokerLocalLeaseCache.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets only the lease specified by unique identifier.                                                                                                                              | true  | false |                                                                                        |
| 注册表项                   | Gets only the leases matching the specified lease key pattern.                                                                                                                   | false | false |                                                                                        |
| 过期                     | Gets only the leases matching the specified expiration date and time.                                                                                                            | false | false |                                                                                        |
| LastModified           | Gets only the leases matching the specified modified date and time.                                                                                                              | false | false |                                                                                        |
| LeaseType              | Gets only leases of a specific type. Possible values Enumeration, Launch.                                                                                                        | false | false |                                                                                        |
| OwnerSAMName           | Gets only the leases associated with the specified Domain\User.                                                                                                                 | false | false |                                                                                        |
| OwnerSID               | Gets only the leases associated with the specified user SID.                                                                                                                     | false | false |                                                                                        |
| OwnerUPN               | Gets only the leases associated with the specified user UPN.                                                                                                                     | false | false |                                                                                        |
| ZoneUid                | Gets only the leases of resources beloning to Zone with specified Uid.                                                                                                           | false | false |                                                                                        |
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

### Citrix.Broker.Admin.SDK.Lease

Returns an Lease object for each enumerated lease.

## 示例

### 示例 1

    C:\PS> $lease = Get-BrokerLease -Uid 1
    

Description  
\---\---\-----  
Gets the lease with internal Uid 1.

### 示例 2

    C:\PS> $leases = Get-BrokerLease -OwnerSAMName Domain\User
    

Description  
\---\---\-----  
Gets the leases associated with the specified user.