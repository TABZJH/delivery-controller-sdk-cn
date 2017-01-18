# Get-AppLibServiceInstance

Gets the service instance entries for the AppLibrary Service.

## 语法

    Get-AppLibServiceInstance [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns service interfaces published by instances of the AppLibrary Service. 服务的每个实例都会发布具有不同接口类型的多个接口，其中每个接口都表示为一个 ServiceInstance 对象。 服务实例可以用于向一个集中式配置服务注册服务，以便其他服务可以使用相应功能。

无需配置数据库连接，即可使用此命令。

## 相关命令

- [Get-AppLibServiceStatus](Get-AppLibServiceStatus.html)
- [Reset-AppLibServiceGroupMembership](Reset-AppLibServiceGroupMembership.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.ServiceInstance

The Get-AppLibServiceInstance command returns an object containing the following properties.  
ServiceGroupUid <guid>  
指定服务所属服务组的唯一标识符。  
ServiceGroupName <string>  
指定服务所属服务组的名称。  
ServiceInstanceUID <guid>  
指定已注册服务实例的唯一标识符，这些实例是由集中式配置服务拥有并从集中式配置服务获取的服务实例。 未注册的服务实例没有唯一标识符。  
ServiceType <string>  
Specifies the service instance type. For this service, the service instance type is always AppLib.  
地址  
指定服务实例的地址。 地址可以用于访问服务，在集中式配置服务中注册后，可由其他服务用于访问服务。  
Binding  
指定要与服务实例通信时必须使用的绑定类型。 在此版本的 XenDesktop 中，绑定类型始终是“wcf_HTTP_kerb”。 这表明服务提供一个结合使用 HTTP 绑定与集成身份验证的 Windows Communication Foundation 端点。  
版本  
指定服务实例的版本。版本号用于确保使用正确版本的服务进行通信。  
ServiceAccount <string>  
指定在其中运行服务实例的计算机的 Active Directory 帐户名称。 帐户名称用于提供有关进行服务间通信所需权限的信息。  
ServiceAccountSid <string>  
指定在其中运行服务实例的计算机的 Active Directory 帐户安全标识符。  
InterfaceType <string>  
指定接口类型。每个服务都可以提供多个服务实例，每个服务实例都有不同用途，而接口定义用途。可用接口包括︰  
SDK - 用于 PowerShell 操作  
InterService - 用于不同服务之间的操作  
Peer - 用于相同类型的服务之间的通信  
Metadata <Citrix.AppLibrary.Sdk.Metadata[]>  
与已注册服务实例关联的元数据集合，这些实例是由集中式配置服务拥有并从集中式配置服务获取的服务实例。 对于未注册的服务实例，不存储元数据。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
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
发生意外错误。有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-AppLibServiceInstance
    
    Address            : http://MyServer.com:80/Citrix/AppLibrary/PowerShellSdk
    Binding            : wcf_HTTP_kerb
    InterfaceType      : SDK
    Metadata           :
    MetadataMap        :
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-2406005612-3133289213-1653143164
    ServiceGroupName   : MyServiceGroup
    ServiceGroupUid    : a88d2f6b-c00a-4f76-9c38-e8330093b54d
    ServiceInstanceUid : 00000000-0000-0000-0000-000000000000
    ServiceType        : AppLib
    Version            : 1
    
    Address            : http://MyServer.com:80/Citrix/AppLibrary/AppLibraryApi
    Binding            : wcf_HTTP_kerb
    InterfaceType      : InterService
    Metadata           :
    MetadataMap        :
    ServiceAccount     : ENG\MyAccount
    ServiceAccountSid  : S-1-5-21-2406005612-3133289213-1653143164
    ServiceGroupName   : MyServiceGroup
    ServiceGroupUid    : a88d2f6b-c00a-4f76-9c38-e8330093b54d
    ServiceInstanceUid : 00000000-0000-0000-0000-000000000000
    ServiceType        : AppLib
    Version            : 1
    

Description  
\---\---\-----  
Get all instances of the AppLibrary Service running on the specified machine. 对于远程服务，请使用 AdminAddress 参数来定义需要接口的服务。 如果没有为运行空间指定 AdminAddress 参数，则返回本地计算机上运行的服务实例。