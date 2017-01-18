# Reset-AdminEnabledFeatureList

请求刷新已启用功能列表。

## 语法

    Reset-AdminEnabledFeatureList [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

此 cmdlet 可以用于请求服务刷新其已启用站点功能内部列表。

这将有效地将已启用站点功能列表与其中一个 Central Configuration Service 同步。

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 注意 如果命令失败，会返回以下错误。 错误代码  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Reset-AdminEnabledFeatureList
    

说明  
\---\---\-----  
刷新已启用站点功能内部列表。