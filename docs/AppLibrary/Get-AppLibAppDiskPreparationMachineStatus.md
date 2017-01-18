# Get-AppLibAppDiskPreparationMachineStatus

获取 AppDisk 正在使用的准备机的状态。

## 语法

    Get-AppLibAppDiskPreparationMachineStatus -AppDiskUid <Guid> [-AdminAddress <String>] [<CommonParameters>]
    
    Get-AppLibAppDiskPreparationMachineStatus [-AppDiskName] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

在一些 AppDisk 操作（包括创建和导入）期间，计算机目录中的计算机会暂时保留。 此 cmdlet 返回当前分配为给定 AppDisk 的准备机的计算机的计算机名称、电源状态和注册状态。 如果 AppDisk 没有关联的准备机，则将不会返回任何结果。

## 相关命令

- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [New-AppLibAppDisk](New-AppLibAppDisk.html)
- [Import-AppLibAppDisk](Import-AppLibAppDisk.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| AppDiskName  | AppDisk 的名称。                                               | true  | false                 |                                       |
| AppDiskUid   | AppDisk 的唯一标识符。                                            | true  | true (ByPropertyName) |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDiskPreparationMachineStatus  
此对象提供 AppDisk 准备机的详细信息，并包含以下信息：  
AppDiskUid <guid>  
AppDisk 的唯一标识符。  
AppDiskName <string>  
AppDisk 的名称。  
MachineName <string>  
准备机的名称。  
PowerState <Citrix.AppLibrary.Sdk.BrokerPowerState>  
计算机的当前电源状态。 可能的值包括：Unmanaged、Unknown、Unavailable、Off、  
On、Suspended、TurningOn、TurningOff、Suspending、Resuming。  
RegistrationState <Citrix.AppLibrary.Sdk.BrokerRegistrationState>  
指示计算机的注册状态。 可能的值包括：Unregistered、Initializing、  
Registered、AgentError。

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
尝试执行数据库操作时，服务发生错误 - 由于  
各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    PS C:\> Get-AppLibAppDiskPreparationMachineStatus -AppDiskName Disk1
    
    
    AppDiskName       : Disk1
    AppDiskUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42
    MachineName       : WWCO\Machine01
    PowerState        : On
    RegistrationState : Registered
    

说明  
\---\---\-----  
获取当前与给定 AppDisk 关联的准备机的状态。