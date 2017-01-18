# Reset-BrokerServiceGroupMembership

Reloads the access permissions and configuration service locations for the Broker Service.

## 语法

    Reset-BrokerServiceGroupMembership [-ConfigServiceInstance] <PSObject[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables you to reload Broker Service access permissions and configuration service locations. The Reset-BrokerServiceGroupMembership command must be run on at least one instance of the service type (Broker) after installation and registration with the configuration service. Without this operation, the Broker services will be unable to communicate with other services in the XenDesktop deployment. 运行该命令时，如果配置服务未停止，向部署添加其他服务时，服务会更新。 The Reset-BrokerServiceGroupMembership command can be run again to refresh this information if automatic updates do not occur when new services are added to the deployment. 如果向命令传递多个配置服务实例，则使用符合预期服务类型要求的第一个实例。

## 相关命令

- [Get-BrokerServiceInstance](Get-BrokerServiceInstance.html)
- [Get-BrokerServiceStatus](Get-BrokerServiceStatus.html)

## 参数

| 名称                    | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| ConfigServiceInstance | 指定表示类型为“InterService”的服务实例（引用了部署的配置服务）的配置服务实例对象。                                                                                                                                | true  | true (ByValue) | LocalHost                                                                              |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress          | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Sdk.ServiceInstance[]

Service instances containing a ServiceInstance object that refers to the central configuration service interservice interface can be piped to the Reset-BrokerServiceGroupMembership command.

## 返回值

### Citrix.Broker.Sdk.ServiceInstance

Reset-BrokerServiceGroupMembership returns opaque objects containing Configuration Service instances that are used by the Broker Service instance.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
NoSuitableServiceInstance  
None of the supplied service instance objects were suitable for resetting service group membership.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-ConfigRegisteredServiceInstance -ServiceType Config | Reset-BrokerServiceGroupMembership
    

说明  
\---\---\-----  
为部署（在该部署中，配置了配置服务，且该配置服务已在服务所在计算机上运行）中的服务重置服务组成员身份。

### 示例 2

    c:\PS>Get-ConfigRegisterdServiceInstance -ServiceType Config -AdminAddress OtherServer.example.com | Reset-BrokerServiceGroupmembership
    

说明  
\---\---\-----  
为部署（在该部署中，配置了配置服务，且该配置服务已在名为“OtherServer.example.com”的计算机上运行）中的服务重置服务组成员身份。