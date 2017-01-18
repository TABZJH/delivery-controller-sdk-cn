# Get-BrokerDBSchema

Gets SQL scripts to create or maintain the database schema for the Citrix Broker Service.

## 语法

    Get-BrokerDBSchema -DatabaseName <String> [-ServiceGroupName <String>] [-ScriptType <DatabaseScriptType>] [-SID <String>] [-LocalDatabase] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets SQL scripts that can be used to create a new Citrix Broker Service database schema, add a new Broker service to an existing site, remove a Broker service from a site, or create a database server logon for a Broker service.

If no Sid parameter is provided, the scripts obtained relate to the currently selected Broker service instance, otherwise the scripts relate to Broker service instance running on the machine identified by the Sid provided. 获取 Evict 脚本时，必须提供一个 SID 参数。

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.

用于获取脚本的服务实例不必是站点成员，也不必配置了数据库连接。

数据库脚本仅支持 Microsoft SQL Server 或 SQL Server Express，并要求使用 Windows 集成身份验证。 可以使用 SQL Server SQLCMD 实用程序或通过将脚本复制到 SQL Server Management Studio (SSMS) 查询窗口并执行查询来运行它们。 如果使用 SSMS，必须以“SQLCMD 模式”执行查询。

The ScriptType parameter determines which script is obtained. If ScriptType is not specified, or is FullDatabase, the script contains:

o Creation of service schema o Creation of database server logon o Creation of database user o Addition of database user to Broker service roles

如果 ScriptType 是 Instance，则返回的脚本包含︰

o Creation of database server logon o Creation of database user o Addition of database user to Broker service roles

如果 ScriptType 是 Evict，则返回的脚本包含︰

o Removal of Broker service instance from database o Removal of database user

如果 ScriptType 是 Login，则返回的脚本包含︰

o Creation of database server logon only

ScriptType Database is deprecated, and FullDatabase should be used instead.

If the service uses two data stores they can exist in the same database.

You do not need to configure a database before using this command.

## 相关命令

- [Set-BrokerDBConnection](Set-BrokerDBConnection.html)
- [Test-BrokerDBConnection](Test-BrokerDBConnection.html)

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
      Specifies the name of the database into which the new Broker service schema is to be placed, or in which it already exists. 数据库本身不是由任何脚本类型创建；在运行脚本之前，它必须已存在。
    </td>
    
    <td>
      true
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
      Specifies the name of the service group to be used when creating the database schema. The service group is a collection of all the Broker services that share the same database instance and are considered equivalent; that is, all the services within a service group can be used interchangeably.
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
      指定返回的数据库脚本类型。 Available script types are:<br />-- FullDatabase<br />Creates a database schema for the Citrix Broker Service in a database instance that does not already contain one. 这在创建新站点时使用。 DatabaseName and ServiceGroupName are required parameters for this script type.<br />-- Instance<br />Adds a Broker Service instance to a database and so to the associated site. Appropriate database server logons and users are created to allow the service instance access to the required service schemas.<br />-- Evict<br />Removes a Broker Service instance from the database and so from the site. 对服务实例的所有引用都将从数据库中删除。 DatabaseName and Sid are required parameters for this script type.<br />-- Login<br />Adds a logon for the Broker Service instance to a database server. This is specifically for use when configuring SQL Server mirroring where the mirror server must have appropriate logons created for all service instances in the site.<br />-- Database<br />This is deprecated. FullDatabase should be used instead.
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
      Specifies the SID of the controller on which the Broker Service instance to remove from the database is running (only valid for a script type of Evict).
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
      无
    </td>
  </tr>
  
  <tr>
    <td>
      LocalDatabase
    </td>
    
    <td>
      指定是否要在与服务组中的其他服务相同的控制器上运行的数据库实例中使用数据库脚本。 Including this parameter ensures the script creates only the required permissions for local services to access the database schema for Broker services. 如果此参数指定不当，服务实例将无法连接到数据库。
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
      AdminAddress
    </td>
    
    <td>
      Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
      Localhost. Once a value is provided by any cmdlet, this value will become the default.
    </td>
  </tr>
</table>

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

A string containing the required SQL script for applying to a database.## Notes The scripts returned support Microsoft SQL Server Express Edition, Microsoft SQL Server Standard Edition, and Microsoft SQL Server Enterprise Edition databases only, and are generated on the assumption that integrated authentication will be used.  
If the ScriptType parameter is not included or set to 'FullDatabase', the full database script is returned, which will:  
Create the database schema.  
Create the user and the role (providing the schema does not already exist).  
Create the logon (providing the schema does not already exist).  
If the ScriptType parameter is set to 'Instance', the script will:  
Create the user and the role (providing the schema does not already exist).  
Create the logon (providing the schema does not already exist) and associate it with a user.  
If the ScriptType parameter is set to 'Login', the script will:  
Create the logon (providing the schema does not already exist) and associate it with a pre-existing user of the same name.  
ScriptType value of 'Database' is deprecated; 'FullDatabase' should be used instead.  
If the LocalDatabase parameter is included, the NetworkService account will be added to the list of accounts permitted to access the database. 仅当数据库在控制器上运行时需要。  
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

    C:\PS>Get-BrokerDBSchema -DatabaseName MySiteDB -ServiceGroupName  MyServiceGroup > C:\BrokerSchema.sql
    

Description  
\---\---\-----  
Gets a script to create the full database schema for the Citrix Broker Service and copies it to a file called "C:\BrokerSchema.sql"  
This script can be used to create the service schema in a database with name "MySiteDB", which must already exist, and must not already contain a Broker service schema.

### 示例 2

    C:\PS>Get-BrokerDBSchema -DatabaseName MySiteDB -ScriptType Login > C:\BrokerLogins.sql
    

Description  
\---\---\-----  
Gets a script to create the appropriate database server logon for the Broker service. This can be used when configuring a mirror server for use.