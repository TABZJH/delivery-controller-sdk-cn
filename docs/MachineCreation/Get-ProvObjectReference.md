# Get-ProvObjectReference

Returns the number of local objects holding references to objects from other services.

## 语法

    Get-ProvObjectReference [-HostingUnitUid <Guid[]>] [-IdentityPoolUid <Guid[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns for each hosting unit or identity pool GUID the number of references by provisioning schemes or by long running task. This check is done without regard for scoping of existing provisioning schemes, references by inaccessible schemes are also checked.

## 相关命令

## 参数

| 名称              | 说明                                                         | 是否必需？ | 管道输入                  | 默认值                                   |
| --------------- | ---------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| HostingUnitUid  | The identifiers of the hosting units(s) to be tested.      | false | true (ByPropertyName) |                                       |
| IdentityPoolUid | The identifiers of the identity pool(s) to be tested.      | false | true (ByPropertyName) |                                       |
| AdminAddress    | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### ObjectReferenceCount

An object which contain the input object identifier, its type, the type of referencing object and the number of references.## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    Get-ProvObjectReference -HostingUnitUid 5B66A060-85E1-4DBD-9D1B-BF79881D3BB1
    
    Count         : 1
    ObjectId      : 5b66a060-85e1-4dbd-9d1b-bf79881d3bb1
    Source        : ProvisioningScheme
    Target        : HostingUnit
    
    Count         : 0
    ObjectId      : 5b66a060-85e1-4dbd-9d1b-bf79881d3bb1
    Source        : Task
    Target        : HostingUnit
    

Description  
\---\---\-----  
This checks a single hosting unit for objects that have references to them; in this case we only have a single provisioning scheme that relates to it.