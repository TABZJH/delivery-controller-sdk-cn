# Get-AnalyticsDBVersionChangeScript

获取用于 Citrix Analytics Service 的 SQL 服务架构更新脚本。

## 语法

    Get-AnalyticsDBVersionChangeScript -DatabaseName <String> -TargetVersion <Version> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

获取可用于更新当前 Citrix Analytics Service 数据库架构的 SQL 脚本。更新可以是升级或降级。

可以获取一个脚本以通过应用 Citrix Analytics Service 上载的可用架构更新软件包将当前服务架构更新到可达到的任何版本。

通常情况下，这种机制用于将当前服务架构更新到较新版本，但它也可用于还原以前应用的更新。

可以使用 SQL Server SQLCMD 实用程序或通过将脚本复制到 SQL Server Management Studio (SSMS) 查询窗口并执行查询来运行获取的 SQL 脚本。 如果使用 SSMS，必须以“SQLCMD 模式”执行查询。

用于生成更新脚本的架构更新软件包存储在数据库中；因此，站点中的任何 Citrix Analytics Service 都可以用于获取架构更新脚本。

数据库中有更新软件包并不表示更新已实际应用于服务架构。 此外，应用更新并不删除关联的更新软件包。

使用更新脚本时务必小心。 Citrix 建议尽可能使用 Studio 执行服务架构升级，而不是手动通过 SDK 升级。 尝试更新之前应备份数据库。 数据库脚本可能还要求独占使用架构，在这种情况下，必须在应用更新之前关闭所有 Citrix Analytics Service。

服务架构应用了更新后，与更新的架构不兼容的任何现有 Citrix Analytics Service 都将停止运行。 服务状态（由 Get-AnalyticsServiceStatus 报告）提供有关服务兼容性的信息（例如 DBNewerVersionThanService）。

## 相关命令

- [Get-AnalyticsInstalledDBVersion](Get-AnalyticsInstalledDBVersion.html)
- [Get-AnalyticsServiceStatus](Get-AnalyticsServiceStatus.html)
- [Get-AnalyticsDBSchema](Get-AnalyticsDBSchema.html)

## 参数

| 名称            | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------- | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DatabaseName  | 包含要更新的 Citrix Analytics Service 架构的数据库的名称。                 | true  | false |                                       |
| TargetVersion | 更新的所需目标服务架构版本。这是应用更新脚本后获取的服务架构版本。                          | true  | false |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.Management.Automation.PSObject

Get-AnalyticsDBVersionChangeScript 返回 PSObject，其中包含一个可以用于更新 Citrix Analytics Service 数据库架构的脚本。 该对象具有以下属性︰  
-- Script  
用于应用更新的 SQL 脚本的原始文本，没有指定目标版本的升级路径时为空。  
-- CanUndo  
如果为 true，指示在应用了更新后，可以获取用于将更新的架构还原到更新之前的架构状态的脚本。 由于 Get-AnalyticsDBVersionChangeScript 只获取与当前架构版本有关的更新脚本，因此只能在应用了更新后获取用于还原更新的脚本。  
-- NeedExclusiveAccess  
如果为 true，指示应用更新时更新需要独占访问 Citrix Analytics Service 架构；必须在更新期间关闭所有 Citrix Analytics Service。## 注意 用于更新架构版本的脚本存储在数据库中，因此服务组中的任何服务都可以获取这些脚本。 使用更新脚本时务必非常小心。 Citrix 建议在尝试升级架构之前备份数据库。 数据库更新脚本可能要求独占使用架构，因此有任何 Analytics Service 正在运行时，这些脚本可能无法执行。 但这取决于要执行的特定更新程序。  
执行架构更新后，需要以前版本的架构的服务可能会停止运行。 Get-AnalyticsServiceStatus 命令报告的 ServiceState 参数提供有关服务兼容性的信息。 例如，如果架构升级到某个服务无法使用的较新版本，该服务将报告“DBNewerVersionThanService”。  
如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
NoOp  
操作成功，但无任何效果。  
NoDBConnections  
未指定 Analytics Service 的数据库连接字符串。  
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

    C:\PS> $update = Get-AnalyticsDBVersionChangeScript -DatabaseName MyDb -TargetVersion 1.0.75.0
    C:\PS> $update.Script > update_75.sql
    

说明  
\---\---\-----  
获取用于将当前架构更新到版本 1.0.75.0 的 SQL 更新脚本。生成的 update_75.sql 脚本适合直接用于 SQL Server SQLCMD 实用程序。