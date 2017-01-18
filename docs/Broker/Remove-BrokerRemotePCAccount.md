# Remove-BrokerRemotePCAccount

Delete RemotePCAccounts from the system.

## 语法

    Remove-BrokerRemotePCAccount [-InputObject] <RemotePCAccount[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Delete RemotePCAccounts from the site.

## 相关命令

- [Get-BrokerRemotePCAccount](Get-BrokerRemotePCAccount.html)
- [New-BrokerRemotePCAccount](New-BrokerRemotePCAccount.html)
- [Set-BrokerRemotePCAccount](Set-BrokerRemotePCAccount.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the RemotePCAccounts to delete.                                                                                                                                       | true  | true (ByValue) | 空值                                                                                     |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.RemotePCAccount

You can pipe the RemotePCAccounts to be deleted into this cmdlet.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerRemotePCAccount 42
    

Description  
\---\---\-----  
Delete RemotePCAccount 42.

### 示例 2

    C:\PS> Get-BrokerRemotePCAccount -OU 'any' | Remove-BrokerRemotePCAccount
    

Description  
\---\---\-----  
Delete the 'any' OU RemotePCAccount.

### 示例 3

    C:\PS> Get-BrokerRemotePCAccount | Remove-BrokerRemotePCAccount
    

Description  
\---\---\-----  
Delete all RemotePCAccounts.