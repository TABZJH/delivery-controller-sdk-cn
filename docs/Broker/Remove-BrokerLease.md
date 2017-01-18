# Remove-BrokerLease

Remove the specified lease in the Database.

## 语法

    Remove-BrokerLease [-InputObject] <Lease[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerLease [-Key] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Marks the specified lease for deletion. Note that the lease is eventually fully deleted when enough time has been allowed for the deletion to propagate to all controller machines in the site, but is immediately removed from lease search results.

## 相关命令

- [Update-BrokerLocalLeaseCache](Update-BrokerLocalLeaseCache.html)
- [Remove-BrokerCache](Remove-BrokerCache.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the lease to remove.                                                                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 注册表项         | Specifies the lease key of the lease to remove. A pattern can be specified.                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Lease

The lease to be removed can be piped into the cmdlet.

## 返回值

### 无

This cmdlet does not return any output.## Notes The lease is marked for deletion after this cmdlet is run. Note that the lease is eventually fully deleted when enough time has been allowed for the deletion to propagate to all controller machines in the site, but is immediately removed from lease search results.

## 示例

### 示例 1

    C:\PS> $lease = Get-BrokerLease -Uid 1
    C:\PS> Remove-BrokerLease $lease
    

Description  
\---\---\-----  
Marks the specified lease for deletion.