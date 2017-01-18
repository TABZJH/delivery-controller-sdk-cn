# Get-AnalyticsDBSchema

获取用于创建或维护 Citrix Analytics Service 的数据库架构的 SQL 脚本。

## 语法

    Get-AnalyticsDBSchema [-DatabaseName <String>] [-ServiceGroupName <String>] [-ScriptType <ScriptTypes>] [-LocalDatabase] [-Sid <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

获取可用于创建新 Analytics Service 数据库架构、向现有站点添加新 Analytics Service、从站点删除 Analytics Service 或为 Analytics Service 创建数据库服务器登录的 SQL 脚本。 如果未提供 SID 参数，则获取的脚本与当前所选 Analytics Service 实例相关，否则，脚本与提供的 SID 标识的计算机上运行的 Analytics Service 实例相关。 获取 Evict 脚本时，必须提供一个 SID 参数。 当前服务实例在本地计算机上，或由最后一次使用的 -AdminAddress 参数显式指定给 Analytics SDK cmdlet。 用于获取脚本的服务实例不必是站点成员，也不必配置了数据库连接。 数据库脚本仅支持 Microsoft SQL Server 或 SQL Server Express，并要求使用 Windows 集成身份验证。 可以使用 SQL Server SQLCMD 实用程序或通过将脚本复制到 SQL Server Management Studio (SSMS) 查询窗口并执行查询来运行它们。 如果使用 SSMS，必须以“SMDCMD 模式”执行查询。 ScriptType 参数确定获取哪个脚本。 如果未指定 ScriptType，或者 ScriptType 是 FullDatabase 或 Database，则脚本包含︰

o 创建服务架构

o 创建数据库服务器登录

o 创建数据库用户

o 向 Analytics Service 角色添加数据库用户

如果 ScriptType 是 Instance，则返回的脚本包含︰

o 创建数据库服务器登录

o 创建数据库用户

o 向 Analytics Service 角色添加数据库用户

如果 ScriptType 是 Evict，则返回的脚本包含︰

o 从数据库中删除 Analytics Service 实例

o 删除数据库用户

如果 ScriptType 是 Login，则返回的脚本包含︰

o 仅创建数据库服务器登录

如果服务使用两个数据存储，它们可以存在于同一个数据库中。您不需要在使用此命令之前配置数据库。

## 相关命令

- [Set-AnalyticsDBConnection](Set-AnalyticsDBConnection.html)
- [Test-AnalyticsDBConnection](Test-AnalyticsDBConnection.html)

## 参数

<table>
  <tr>
    <th>
      名称
    </th>
    
    <th>
      说明
    </th>
    
    <th>
      是否必需？
    </th>
    
    <th>
      管道输入
    </th>
    
    <th>
      默认值
    </th>
  </tr>
  
  <tr>
    <td>
      DatabaseName
    </td>
    
    <td>
      指定新 Analytics Service 架构要放置在其中的数据库或其中已存在该架构的数据库的名称。 数据库本身不是由任何脚本类型创建；在运行脚本之前，它必须已存在。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      ServiceGroupName
    </td>
    
    <td>
      创建 Citrix Analytics Service 数据库架构时要使用的服务组的名称。 服务组是所有 Analytics Service 的集合，这些服务共享同一个数据库并被视为同等 （即，同一个服务组中的任何服务可以互换使用）。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      ScriptType
    </td>
    
    <td>
      指定返回的数据库脚本类型。 可用脚本类型包括︰<br />-- FullDatabase<br />在一个尚未包含数据库架构的数据库实例中为 Citrix Analytics Service 创建数据库架构。 这在创建新站点时使用。 DatabaseName 和 ServiceGroupName 是此脚本类型的必要参数。<br />-- Database<br />与“FullDatabase”执行相同功能。<br />-- Instance<br />将 Analytics Service 实例添加到数据库，因而添加到关联站点。 创建适当的数据库服务器登录和用户以允许服务实例访问所需服务架构。<br />-- Evict<br />从数据库中删除 Analytics Service 实例，因而从站点中删除。 对服务实例的所有引用都将从数据库中删除。 DatabaseName 和 SID 是此脚本类型的必要参数。<br />-- Login<br />将 Analytics Service 实例的登录添加到数据库服务器。 这专门在镜像服务器必须具有为站点中所有服务实例创建的适当登录的情况下配置 SQL Server 镜像时使用。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      LocalDatabase
    </td>
    
    <td>
      指定是否要在与服务组中的其他服务相同的控制器上运行的数据库实例中使用数据库脚本。 包括此参数可确保脚本只创建本地服务访问 Analytics Service 的数据库架构所需的权限。 如果此参数指定不当，服务实例将无法连接到数据库。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      SID
    </td>
    
    <td>
      指定要从数据库中删除的 Analytics Service 实例在其中运行的控制器的 SID（仅对 Evict 脚本类型有效）。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByValue)
    </td>
    
    <td>
      无
    </td>
  </tr>
  
  <tr>
    <td>
      AdminAddress
    </td>
    
    <td>
      指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
      Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。
    </td>
  </tr>
</table>

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

包含应用于数据库的所需 SQL 脚本的字符串。## 注意 返回的脚本仅支持 Microsoft SQL Server Express Edition、Microsoft SQL Server Standard Edition 及 Microsoft SQL Server Enterprise Edition 数据库，且生成的前提条件是将使用集成身份验证。  
如果未包括 ScriptType 参数，或该参数设置为“FullDatabase”或“Database”，则返回完整数据库脚本，脚本将：  
创建数据库架构。  
创建用户和角色（假定架构尚不存在）。  
创建登录（假定架构尚不存在）。  
如果 ScriptType 参数设置为“Instance”，脚本将：  
创建用户和角色（假定架构尚不存在）。  
创建登录（假定架构尚不存在）并将其与用户关联。  
如果 ScriptType 参数设置为“Login”，脚本将：  
创建登录（假定架构尚不存在）并将其与预先存在的同名用户关联。   
如果包含 LocalDatabase 参数，NetworkService 帐户将添加到允许访问数据库的帐户列表中。 仅当数据库在控制器上运行时需要。  
如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
GetSchemasFailed  
找不到数据库架构。  
ActiveDirectoryAccountResolutionFailed  
找不到指定的 Active Directory 帐户或组。  
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

    C:\PS>Get-AnalyticsDBSchema -DatabaseName MySiteDB -ServiceGroupName  MyServiceGroup > C:\AnalyticsSchema.sql
    

说明  
\---\---\-----  
获取用于为 Citrix Analytics Service 创建完整数据库架构的脚本，并将其复制到名为“C:\AnalyticsSchema.sql”的文件  
此脚本可以用于在名为“MySiteDB”的数据库中创建服务架构，该数据库必须已存在且不得已包含 Analytics Service 架构。

### 示例 2

    C:\PS>Get-AnalyticsDBSchema -DatabaseName MySiteDB -ScriptType Login > C:\AnalyticsLogins.sql
    

说明  
\---\---\-----  
获取用于为 Analytics Service 创建适当的数据库服务器登录的脚本。这可以在配置镜像服务器时使用。