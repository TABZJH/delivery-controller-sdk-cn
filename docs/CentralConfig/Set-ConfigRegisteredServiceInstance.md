# Set-ConfigRegisteredServiceInstance

Updates a service instance.

## 语法

    Set-ConfigRegisteredServiceInstance -ServiceInstanceUid <Guid> -Address <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to change the address property of an existing service instance that is registered in the Configuration Service.

## 相关命令

- [Get-ConfigRegisteredServiceInstance](Get-ConfigRegisteredServiceInstance.html)
- [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
- [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)

## 参数

| 名称                 | 说明                                                                                                         | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------------ | ---------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ServiceInstanceUid | The unique identifier for the service instance to be updated.                                              | true  | true (ByPropertyName) |                                       |
| 地址                 | The new address for the service instance.                                                                  | true  | false                 |                                       |
| PassThru           | Defines whether or not the command returns a result showing the new state of the updated service instance. | false | false                 | true                                  |
| LoggingId          | Specifies the logging id of the high-level operation this cmdlet invocation is part of.                    | false | false                 |                                       |
| AdminAddress       | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                  | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Configuration.Sdk.ServiceInstance  
This represents a service instance and has the following parameters:  
ServiceGroupUid <guid>  
The unique identifier for the service group to which the service instance belongs.  
ServiceGroupName <string>  
The name of the service group to which the service instance belongs.  
ServiceInstanceUid <guid>  
The unique identifier for the service instance.  
ServiceType <string>  
The type of the service group.  
Address <string>  
The contact address for the service instance.  
Binding <string>  
The binding to use for connections to the service instance.  
Version <int>  
The version of the service instance.  
ServiceAccount <string>  
The AD computer account for the computer that is providing the service instance.  
ServiceAccountSid <string>  
The AD computer account SID for the computer that is providing the service instance.  
InterfaceType <string>  
The interface type for the service instance.  
Metadata <Citrix.Configuration.Sdk.Metadata[]>  
The metadata for the service instance.

## Notes In the case of failure, the following errors can result.  
Error Codes \---\---\----- ObjectToUpdateDoesNotExist The service instance specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Set-ConfigRegisteredServiceInstance -ServiceInstanceUid "9805f39d-99eb-44f0-8f63-9d8e3f1228e0" -Address "http://myServer.com/Citrix/sdkHostingUnitService"
    

Description  
\---\---\-----  
Update the service instance with the unique identifier of '9805f39d-99eb-44f0-8f63-9d8e3f1228e0' to use the new address.