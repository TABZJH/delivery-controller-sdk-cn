# Get-HypLocalizedString

Obtains human-readable and locale-aware status messages from a hosting connection.

## 语法

    Get-HypLocalizedString [-LiteralPath] <String> [-Locale] <String> [-Category] <String> [-AdminAddress <String>] [[-LookupKey] <String>] [<CommonParameters>]
    

## 详细说明

TODO

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                                                                      | 是否必需？ | 管道输入           | 默认值                                  |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------ |
| LiteralPath  | Specifies the path to the hypervisor connection whose strings are being queried. The path must be in one of the following formats: <drive>:\Connections\<connectionname> 或者 <drive>:\Connections\{<connection uid>} | true  | true (ByValue) |                                      |
| 区域设置         | The requested locale for the message, such as "en-US".                                                                                                                                                                  | true  | false          |                                      |
| 类别           | The category of the localized string.                                                                                                                                                                                   | true  | false          |                                      |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide a host name or an IP address.                                                                                | false | false          | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |
| LookupKey    | The lookup key or message ID.                                                                                                                                                                                           | false | false          |                                      |

## 输入类型

### System.string  
You can pipe a string that contains a path to Get-HypLocalizedString (LiteralPath parameter).

## 返回值

### Citrix.Host.Sdk.HypervisorString

Get-HypLocalizedString returns zero or more instances of the HypervisorString object, each of which contain the following properties:  
类别 <string> Specifies the category of the string, such as "Exception". LookupKey <string> Specifies the unique lookup key or message ID within the category. DisplayText <string> Specifies the locale-aware and human-readable text.## Notes In the case of failure, the following errors can be produced.  
错误代码  
\---\---\-----  
ConnectionsPathInvalid  
The path provided is not to an item in the Connections subdirectory of the host service provider.  
HypervisorConnectionObjectNotFound  
The path provided could not be resolved to an existing hypervisor connection. The name or GUID is invalid.  
HypervisorInMaintenanceMode  
The hypervisor for the connection is in maintenance mode.  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
An error occurred in the service while attempting a database operation. Communication with the database failed for  
various reasons.  
CommunicationError  
与服务通信时发生错误。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## 示例

### 示例 1

    c:\PS>Get-HypLocalizedString -LiteralPath XDHyp:\Connections\MyCloud -Category Exception -Locale "en-US" -LookupKey "MyCloud.InsufficientFreeIpSpace"
    
              Category             : Exception
              LookupKey            : MyCloud.InsufficientFreeIpSpace
              DisplayText          : There are not enough free IP addresses on the network {0}
    

Description  
\---\---\-----  
This command illustrates how a single error/exception message can be obtained for a hosting operation that failed (such as a provisioning operation). The caller specifies that they need to display the message in the en-US locale. They also specify a lookup key or message ID for the message, which will have been obtained as an exception code from the failed operation. The locale and key/ID are traded for a readable message, which also includes substitutions.