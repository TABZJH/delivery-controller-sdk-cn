# Get-AdminService

Gets the service record entries for the DelegatedAdmin Service.

## 语法

    Get-AdminService [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns instances of the DelegatedAdmin Service that the service publishes. The service records contain account security identifier information that can be used to remove each service from the database.

要使用此命令，需要服务的数据库连接。

## 相关命令

## 参数

| 名称                     | 说明                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------- |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。              | false | false |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                 | false | false |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Admin_Filtering for details.      | false | false | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                           | false | false | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                  | false | false |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。               | false | false | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Admin_Filtering for details. | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.DelegatedAdmin.Sdk.Service

The Get-AdminServiceInstance command returns an object containing the following properties.  
UID <integer>  
指定组中服务的唯一标识符。该唯一标识符是索引号。  
ServiceHostId <guid>  
指定服务实例的唯一标识符。  
DNSName <string>  
指定在其中运行服务的主机的域名。  
MachineName <string>  
指定在其中运行服务的主机的短名称。  
CurrentState <Citrix.Fma.Sdk.ServiceCore.ServiceState>  
指定服务是正在运行、已启动但处于非活动状态、已停止还是已失败。  
LastStartTime <datetime>  
指定上次重新启动服务的日期和时间。  
LastActivityTime <datetime>  
指定上次停止或重新启动服务的日期和时间。  
OSType  
指定在其中运行服务的主机上安装的操作系统。  
OSVersion  
指定在其中运行服务的主机上安装的操作系统版本。  
ServiceVersion  
指定服务实例的版本号。版本号是反映服务的完整内部版本的字符串。  
DatabaseUserName <string>  
为服务实例指定具有访问数据库的权限的 Active Directory 帐户名称。 这将是计算机帐户或（如果数据库在控制器上运行）NetworkService 帐户。  
SID <string>  
指定在其中运行服务实例的计算机的 Active Directory 帐户安全标识符。  
ActiveSiteServices <string[]>  
指定服务中当前正在运行的活动站点服务的名称。 站点服务是在某些服务中执行长时间运行的后台处理的组件。 对于不包含站点服务的服务，此字段为空。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
UnknownObject  
未找到其中一个指定的对象。  
PartialData  
只返回了一部分可用数据。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
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

    c:\PS>Get-AdminService
    
    Uid                : 1
    ServiceHostId      : aef6f464-f1ee-4042-a523-66982e0cecd0
    DNSName            : MyServer.company.com
    MachineName        : MYSERVER
    CurrentState       : On
    LastStartTime      : 04/04/2011 15:25:38
    LastActivityTime   : 04/04/2011 15:33:39
    OSType             : Win32NT
    OSVersion          : 6.1.7600.0
    ServiceVersion     : 5.1.0.0
    DatabaseUserName   : NT AUTHORITY\NETWORK SERVICE
    SID                : S-1-5-21-2316621082-1546847349-2782505528-1165
    ActiveSiteServices : {MySiteService1, MySiteService2...}
    

Description  
\---\---\-----  
Get all the instances of the DelegatedAdmin Service running in the current service group.