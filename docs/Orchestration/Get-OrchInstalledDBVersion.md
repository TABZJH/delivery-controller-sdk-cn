# Get-OrchInstalledDBVersion

Gets a list of all available database schema versions for the Orchestration Service.

## 语法

    Get-OrchInstalledDBVersion [-Upgrade] [-Downgrade] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets the current version number of the Citrix Orchestration Service database schema when called with no parameters.

如果调用时使用 -Upgrade 参数，则获取升级可以执行到的服务架构版本号。

如果调用时使用 -Downgrade 参数，则获取降级可以执行到的服务架构版本号。

The SQL scripts to perform schema upgrades and downgrades can be obtained using the Get-OrchDBVersionChangeScript cmdlet. Citrix 建议尽可能使用 Studio 执行服务架构升级，而不是手动通过 SDK 升级。

一次只能提供 -Upgrade 参数或 -Downgrade 参数之一。

## 相关命令

- [Get-OrchDBVersionChangeScript](Get-OrchDBVersionChangeScript.html)
- [Get-OrchDBSchema](Get-OrchDBSchema.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 升级           | 指定只应返回当前数据库版本可以更新到的架构版本。                                   | false | false |                                       |
| Downgrade    | 指定只应返回当前数据库版本可以还原到的架构版本。                                   | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.Version

Get-OrchInstalledDBVersion returns database schema version numbers as requested.  
主要 <integer> 次要 <integer> 内部版本 <integer> Revision <integer>## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
InvalidParameterCombination  
指定了 Upgrade 和 Downgrade 这两个标志。  
NoOp  
操作成功，但无任何效果。  
NoDBConnections  
The database connection string for the Orchestration Service has not been specified.  
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
发生意外错误。有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    PS C:\>Get-OrchInstalledDBVersion
    
    Major  Minor  Build  Revision
    -----  -----  -----  --------
    5      6      0      0
    

Description  
\---\---\-----  
Gets the current Citrix Orchestration Service database schema version number.

### 示例 2

    C:\PS>Get-OrchInstalledDBVersion -Upgrade
    

Description  
\---\---\-----  
Get the versions of the Orchestration Service database schema for which upgrade scripts are supplied.