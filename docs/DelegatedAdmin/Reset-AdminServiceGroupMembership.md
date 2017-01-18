# Reset-AdminServiceGroupMembership

Reloads the access permissions and configuration service locations for the DelegatedAdmin Service.

## 语法

    Reset-AdminServiceGroupMembership [-ConfigServiceInstance] <ServiceInstance[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables you to reload DelegatedAdmin Service access permissions and configuration service locations. The Reset-AdminServiceGroupMembership command must be run on at least one instance of the service type (Admin) after installation and registration with the configuration service. Without this operation, the DelegatedAdmin services will be unable to communicate with other services in the XenDesktop deployment. 运行该命令时，如果配置服务未停止，向部署添加其他服务时，服务会更新。 The Reset-AdminServiceGroupMembership command can be run again to refresh this information if automatic updates do not occur when new services are added to the deployment. 如果向命令传递多个配置服务实例，则使用符合预期服务类型要求的第一个实例。

## 相关命令

## 参数

| 名称                    | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| ConfigServiceInstance | 指定表示类型为“InterService”的服务实例（引用了部署的配置服务）的配置服务实例对象。                                                                                                                       | true  | true (ByValue) |                                       |
| LoggingId             | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress          | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.ServiceInstance[]  
Service instances containing a ServiceInstance object that refers to the central configuration service inter-service interface can be piped to the Reset-AdminServiceGroupMembership command.

## 返回值

### 

## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
NoSuitableServiceInstance  
提供的服务实例对象都不适合用于重置服务组成员身份。  
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
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-ConfigRegisteredServiceInstance -ServiceType Config | Reset-AdminServiceGroupMembership
    

说明  
\---\---\-----  
为部署（在该部署中，配置了配置服务，且该配置服务已在服务所在计算机上运行）中的服务重置服务组成员身份。

### 示例 2

    c:\PS>Get-ConfigRegisterdServiceInstance -ServiceType Config -AdminAddress OtherServer.example.com | Reset-AdminServiceGroupmembership
    

说明  
\---\---\-----  
为部署（在该部署中，配置了配置服务，且该配置服务已在名为“OtherServer.example.com”的计算机上运行）中的服务重置服务组成员身份。