# Set-AnalyticsDBConnection

为 Analytics Service 配置数据库连接。

## 语法

    Set-AnalyticsDBConnection [-DBConnection] <String> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

指定由当前所选 Citrix Analytics Service 实例使用的数据库连接字符串。

服务会记录连接字符串并尝试联系指定的数据库。 如果最初无法联系数据库，服务将以一定的时间间隔重试连接，直到成功与数据库建立了联系。

如果已记录一个数据库连接字符串，则不能为服务设置新的数据库连接字符串。 必须先将连接字符串设置为 $null。 此操作会导致服务重置并回到空闲状态，此时可以设置新的连接字符串。

成功为服务设置数据库连接字符串后，cmdlet 将返回“OK”状态。如果数据库连接字符串设置为 $null，则返回“DBUnconfigured”状态。

语法无效的连接字符串不会记录。

仅支持在连接字符串中使用 Windows 身份验证；如果连接字符串包含 SQL 身份验证凭据，总是会因为无效而被拒绝。

当前服务实例在本地计算机上，或由最后一次使用的 -AdminAddress 参数显式指定给 Analytics SDK cmdlet。

## 相关命令

- [Get-AnalyticsServiceStatus](Get-AnalyticsServiceStatus.html)
- [Get-AnalyticsDBConnection](Get-AnalyticsDBConnection.html)
- [Test-AnalyticsDBConnection](Test-AnalyticsDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DBConnection | 指定要由 Analytics Service 使用的数据库连接字符串。传送 $null 将清除配置的任何现有数据库连接。                                                                                                           | true  | false |                                       |
| Force        | 如果存在，允许在联系数据库或其他服务出现问题时，本地管理员可以将连接字符串设置为 null。                                                                                                                         | false | false | false                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

Set-AnalyticsDBConnection cmdlet 返回描述 Analytics Service 状态的对象以及额外的诊断信息。 可能的值包括︰   
-- OK：  
为 Analytics Service 实例配置了有效的数据库和服务架构。 服务可以运行。  
-- DBUnconfigured：  
没有为 Analytics Service 实例设置数据库连接字符串。  
-- DBRejectedConnection：  
数据库拒绝了来自 Analytics Service 的登录尝试。 这可能是因为服务曾尝试使用无效凭据登录，或者因为尚未在指定位置安装数据库。  
-- InvalidDBConfigured：  
指定的数据库不存在、对 Analytics Service 实例不可见或数据库中的服务架构无效。  
-- DBNotFound：  
使用配置的连接字符串找不到指定的数据库。  
-- DBNewerVersionThanService：  
当前正在使用的 Analytics Service 版本高于数据库中的 Analytics Service 架构版本，并与其不兼容。 请将 Analytics Service 升级到较新版本。  
-- DBOlderVersionThanService：  
数据库中的 Analytics Service 架构版本高于当前正在使用的 Analytics Service 版本，并与其不兼容。 请将数据库架构升级到较新版本。  
-- DBVersionChangeInProgress：  
正在升级数据库架构。  
-- PendingFailure：  
Analytics Service 实例与数据库之间的连接已断开。 这可能是暂时性的网络错误，但可能指示出现需要管理员干预的连接断开情况。  
-- Failed：  
Analytics Service 实例与数据库之间的连接已断开很长一段时间，或者由于配置问题失败。 服务实例与数据库之间的连接不可用时，服务实例无法运行。  
-- Unknown：  
无法确定 Analytics Service 的状态。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
InvalidDBConnectionString  
数据库连接字符串格式无效。  
DatabaseConnectionDetailsAlreadyConfigured  
已配置了数据库连接。 设置了配置后，只能将其设置为 $null。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Set-AnalyticsDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
    

说明  
\---\---\-----  
配置服务实例以使用名为 XDDB 的数据库，该数据库在名为 dbserver 的计算机上运行的 SQL Server Express 数据库上。 需要集成 Windows 身份验证。

### 示例 2

    C:\PS>Set-AnalyticsDBConnection -DBConnection $null
    

说明  
\---\---\-----  
重置服务实例的数据库连接字符串。 服务实例重置并回到空闲状态，直到指定有效的新数据库连接字符串。

### 示例 3

    c:\PS>Set-AnalyticsDBConnection -DBConnection "Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True"
              OK
    

说明  
\---\---\-----  
为 Analytics Service 配置数据库连接字符串。

### 示例 4

    c:\PS>Set-AnalyticsDBConnection -DBConnection "Invalid Connection String"
    
              Invalid database connection string format.
    

说明  
\---\---\-----  
为 Analytics Service 配置的数据库连接字符串无效。