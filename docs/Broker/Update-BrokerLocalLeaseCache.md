# Update-BrokerLocalLeaseCache

Flushes the local lease cache.

## 语法

    Update-BrokerLocalLeaseCache [-Workers] [-Applications] [-Icons] [-Desktops] [-Leases] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes all local cached lease data and any state information stored in the registry.

## 相关命令

- [Remove-BrokerLease](Remove-BrokerLease.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| Workers      | Removes all locally cached workers on the controller. The worker cache will be repopulated from the current site database contents after a short delay.                         | false | false | false                                                                                  |
| 应用程序         | Removes all locally cached applications on the controller. The application cache will be repopulated from the current site database contents after a short delay.               | false | false | false                                                                                  |
| 图标           | Removes all locally cached icons on the controller. The icon cache will be repopulated from the current site database contents after a short delay.                             | false | false | false                                                                                  |
| 桌面           | Removes all locally cached desktops on the controller. The desktop cache will be repopulated from the current site database contents after a short delay.                       | false | false | false                                                                                  |
| Leases       | Removes all locally cached leases on the controller. The lease cache will be repopulated from the current site database contents after a short delay.                           | false | false | false                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

## 返回值

### 无

## Notes The local cache for lease and other data like worker, desktop, application and icon information is removed and will be repopulated from the current site database contents after a short delay.

## 示例

### 示例 1

    C:\PS> Update-BrokerLocalLeaseCache
    

Description  
\---\---\-----  
Flushes the local lease cache for all objects and deletes any state information stored in the registry.

### 示例 2

    C:\PS> Update-BrokerLocalLeaseCache -Workers
    

Description  
\---\---\-----  
Flushes the local lease cache for all workers and deletes any state information stored in the registry.