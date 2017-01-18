# Test-AcctIdentityPoolNameAvailable

检查以确保标识池的建议名称未使用。

## 语法

    Test-AcctIdentityPoolNameAvailable [-IdentityPoolName] <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

检查以确保标识池的建议名称未使用。此检查不考虑现有标识池的作用域，因此还检查不可访问的池的名称。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)

## 参数

| 名称               | 说明                                                         | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------- | ---------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| IdentityPoolName | 要测试的标识池的名称。                                                | true  | true (ByValue, ByPropertyName) |                                       |
| AdminAddress     | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### object[]

配对名称和名称可用性的 PSObject 数组## 注意 如果失败，会发生以下错误。  
错误  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
尝试执行数据库操作时，服务发生错误 - 由于  
各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    Test-AcctIdentityPoolNameAvailable -IdentityPoolName $NewPoolName
    

说明  
\---\---\-----  
测试 $NewPoolName 值是否唯一，以及是否可以用于创建新置备方案或重命名现有置备方案而不会失败。 如果名称正确，则返回 True。