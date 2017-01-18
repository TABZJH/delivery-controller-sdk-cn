# Test-ProvSchemeNameAvailable

Checks to ensure that the proposed name for a provisioning scheme is unused.

## 语法

    Test-ProvSchemeNameAvailable -ProvisioningSchemeName <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Checks to ensure that the proposed name for a provisioning scheme is unused. This check is done without regard for scoping of existing provisioning schemes, so the names of inaccessible schemes are also checked.

## 相关命令

- [New-ProvScheme](New-ProvScheme.html)
- [Rename-ProvScheme](Rename-ProvScheme.html)

## 参数

| 名称                     | 说明                                                            | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------------- | ------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| ProvisioningSchemeName | The name or names of the provisioning scheme(s) to be tested. | true  | true (ByValue, ByPropertyName) |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。    | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### NameAvailability

Pairs of name and the availability of the name## Notes In the case of failure, the following errors can result.  
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

    Test-ProvSchemeNameAvailable -ProvisioningSchemeName $NewSchemeName
    

Description  
\---\---\-----  
This tests whether the value of $NewSchemeName is unique or not, and can be used to create a new provisioning scheme or rename an existing one without failing. 如果名称正确，则返回 True。