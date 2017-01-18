# Get-LogDBSchema

Gets SQL scripts to create or maintain the database schema for the Citrix ConfigurationLogging Service.

## 语法

    Get-LogDBSchema [-DataStore <String>] [-DatabaseName <String>] [-ServiceGroupName <String>] [-ScriptType <ScriptTypes>] [-LocalDatabase] [-Sid <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets SQL scripts that can be used to create a new ConfigurationLogging Service database schema, add a new ConfigurationLogging Service to an existing site, remove a ConfigurationLogging Service from a site, or create a database server logon for a ConfigurationLogging Service. If no Sid parameter is provided, the scripts obtained relate to the currently selected ConfigurationLogging Service instance, otherwise the scripts relate to ConfigurationLogging Service instance running on the machine identified by the Sid provided. 获取 Evict 脚本时，必须提供一个 SID 参数。 The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a ConfigurationLogging SDK cmdlet. 用于获取脚本的服务实例不必是站点成员，也不必配置了数据库连接。 数据库脚本仅支持 Microsoft SQL Server 或 SQL Server Express，并要求使用 Windows 集成身份验证。 可以使用 SQL Server SQLCMD 实用程序或通过将脚本复制到 SQL Server Management Studio (SSMS) 查询窗口并执行查询来运行它们。 如果使用 SSMS，必须以“SMDCMD 模式”执行查询。 ScriptType 参数确定获取哪个脚本。 如果未指定 ScriptType，或者 ScriptType 是 FullDatabase 或 Database，则脚本包含︰

o 创建服务架构

o 创建数据库服务器登录

o 创建数据库用户

o Addition of database user to ConfigurationLogging Service roles

如果 ScriptType 是 Instance，则返回的脚本包含︰

o 创建数据库服务器登录

o 创建数据库用户

o Addition of database user to ConfigurationLogging Service roles

如果 ScriptType 是 Evict，则返回的脚本包含︰

o Removal of ConfigurationLogging Service instance from database

o 删除数据库用户

如果 ScriptType 是 Login，则返回的脚本包含︰

o 仅创建数据库服务器登录

如果服务使用两个数据存储，它们可以存在于同一个数据库中。您不需要在使用此命令之前配置数据库。

## 相关命令

- [Get-LogDataStore](Get-LogDataStore.html)
- [Set-LogDBConnection](Set-LogDBConnection.html)
- [Test-LogDBConnection](Test-LogDBConnection.html)

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
      DataStore
    </td>
    
    <td>
      Specifies the logical name of the data store for the ConfigurationLogging Service. Can be either be 'Site' or the logical name of the secondary data store.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
      站点
    </td>
  </tr>
  
  <tr>
    <td>
      DatabaseName
    </td>
    
    <td>
      Specifies the name of the database into which the new ConfigurationLogging service schema is to be placed, or in which it already exists. 数据库本身不是由任何脚本类型创建；在运行脚本之前，它必须已存在。
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
      The name of the service group to be used when creating the Citrix ConfigurationLogging Service database schema. The service group is the collection of all ConfigurationLogging Services that share the same database and are considered equal (i.e. any service in the same service group can be used interchangeably).
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
      指定返回的数据库脚本类型。 Available script types are:<br />-- FullDatabase<br />Creates a database schema for the Citrix ConfigurationLogging Service in a database instance that does not already contain one. 这在创建新站点时使用。 DatabaseName and ServiceGroupName are required parameters for this script type.<br />-- Database<br />Performs the same function as "FullDatabase".<br />-- Instance<br />Adds a ConfigurationLogging Service instance to a database and so to the associated site. Appropriate database server logons and users are created to allow the service instance access to the required service schemas.<br />-- Evict<br />Removes a ConfigurationLogging Service instance from the database and so from the site. 对服务实例的所有引用都将从数据库中删除。 DatabaseName and Sid are required parameters for this script type.<br />-- Login<br />Adds a logon for the ConfigurationLogging Service instance to a database server. 这专门在镜像服务器必须具有为站点中所有服务实例创建的适当登录的情况下配置 SQL Server 镜像时使用。
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
      指定是否要在与服务组中的其他服务相同的控制器上运行的数据库实例中使用数据库脚本。 Including this parameter ensures the script creates only the required permissions for local services to access the database schema for ConfigurationLogging services. 如果此参数指定不当，服务实例将无法连接到数据库。
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
      Specifies the SID of the controller on which the ConfigurationLogging Service instance to remove from the database is running (only valid for a script type of Evict).
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

    C:\PS>Get-LogDBSchema -DatabaseName MySiteDB -ServiceGroupName  MyServiceGroup > C:\ConfigurationLoggingSchema.sql
    

Description  
\---\---\-----  
Gets a script to create the full database schema for the Citrix ConfigurationLogging Service and copies it to a file called "C:\ConfigurationLoggingSchema.sql"  
This script can be used to create the service schema in a database with name "MySiteDB", which must already exist, and must not already contain a ConfigurationLogging service schema.

### 示例 2

    C:\PS>Get-LogDBSchema -DatabaseName MySiteDB -ScriptType Login > C:\ConfigurationLoggingLogins.sql
    

Description  
\---\---\-----  
Gets a script to create the appropriate database server logon for the ConfigurationLogging service. This can be used when configuring a mirror server for use.

### 示例 3

    C:\PS>Get-LogDBSchema -DatabaseName MySecondaryDB -ServiceGroupName MyServiceGroup -DataStore Secondary > C:\LogSchema.sql
    

Description  
\---\---\-----  
Get the full database schema for the secondary data store of the ConfigurationLogging Service and copy it to a file called 'C:\LogSecondarySchema.sql'.  
This script can then be used to create the schema in a pre-existing database named 'MyDB' that does not already contain a ConfigurationLogging Service secondary schema.