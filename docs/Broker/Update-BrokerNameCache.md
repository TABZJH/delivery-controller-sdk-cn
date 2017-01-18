# Update-BrokerNameCache

Performs administrative operations on the user and machine name cache.

## 语法

    Update-BrokerNameCache [-Machines] [-Users] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Triggers an immediate asynchronous refresh of the name cache. This may be useful to ensure up-to-date name information is present in the cache after user and/or machine accounts are known to have changed and you need to see those changes immediately instead of waiting for the periodic automatic refresh.

The Broker Service maintains a cache of the names of users and machines in use by the site. By default, name information is obtained periodically from Active Directory and the cache refreshed automatically.

During normal usage, you should not need to perform administrative operations on the name cache.

For users/groups, the following name information is cached: Windows name (DOMAIN\user) User Principal Name or 'UPN' (user@upndomain) Full Name or 'Common Name' (typically a user's full name)

For machines, the following name information is cached: Windows name (DOMAIN\machine) DNS name (machine.dnsdomain)

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| 计算机          | Triggers an asynchronous refresh of all cached machine name information.                                                                           | false | false |                                                                                        |
| 用户           | Triggers an asynchronous refresh of all cached user name information.                                                                              | false | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### 无

## Notes For some user accounts, for example, the built-in domain administrator, the UPN and/or Full Name values may not be available because they are not typically specified within Active Directory.  
For group accounts, UPN and Full Name values are not available because they are not applicable or not specified within Active Directory.  
The DNS name information for a machine is obtained from Active Directory and not from the DNS sub-system. If a machine has only recently been configured, the DNS information may not be available initially.

## 示例

### 示例 1

    C:\PS> Update-BrokerNameCache -Machines
    

Description  
\---\---\-----  
Triggers an immediate asynchronous refresh of all machine name information held within the name cache.

### 示例 2

    C:\PS> Update-BrokerNameCache -Machines -Users
    

Description  
\---\---\-----  
Triggers an immediate asynchronous refresh of all machine and user name information held within the name cache.