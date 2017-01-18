# Unregister-ConfigRegisteredServiceInstance

Removes a service instance from the Configuration Service registry.

## 语法

    Unregister-ConfigRegisteredServiceInstance [-ServiceInstanceUid] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to remove a service instance from the Configuration Service registry. This does not remove any service groups (if all service instances for a Service Group are removed, an empty service group remains and must be removed using the Remove-ConfigServiceGroup command).

## 相关命令

- [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)

## 参数

| 名称                 | 说明                                                                                      | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------------ | --------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ServiceInstanceUid | The unique identifier for the service instance to be removed.                           | true  | true (ByPropertyName) |                                       |
| LoggingId          | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false                 |                                       |
| AdminAddress       | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                               | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.ServiceInstance  
An object with a parameter called 'ServiceInstanceUid' can be used to unregister service instances.

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes \---\---\----- ServiceInstanceObjectNotFound The service instance specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Get-ConfigRegisteredServiceInstance -ServiceType "Config" | Unregister-ConfigRegisteredServiceInstance
    

Description  
\---\---\-----  
Unregisters all the service instances that are for a service type of 'Config' from the Configuration Service instance register.