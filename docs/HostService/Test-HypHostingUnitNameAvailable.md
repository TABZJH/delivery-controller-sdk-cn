# Test-HypHostingUnitNameAvailable

Checks to ensure that the proposed name for a hosting unit is unused.

## 语法

    Test-HypHostingUnitNameAvailable -HostingUnitName <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to check that the proposed name for a hosting unit is unused. This check is done without regard for scoping of the existing hosting unit, so the names of inaccessible hosting units are also checked.

## 相关命令

- [New-Item](New-Item.html)
- [Rename-Item](Rename-Item.html)

## 参数

| 名称              | 说明                                                         | 是否必需？ | 管道输入                           | 默认值                                   |
| --------------- | ---------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| HostingUnitName | The name or names of the hosting units(s) to be tested.    | true  | true (ByValue, ByPropertyName) |                                       |
| AdminAddress    | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### object[]

An array of PSObjects which pair the name and availability of the name## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for  
various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    Test-HypHostingUnitNameAvailable -HostingUnitName $NewHostingUnitName
    

Description  
\---\---\-----  
This tests whether the value of $NewHostingUnitName is unique or not, and can be used to create a new hosting unit or rename an existing one without failing. True is returned if the name is unique.