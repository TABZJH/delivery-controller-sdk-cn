# Get-AppLibAppDiskObjectReference

返回拥有对 AppDisk 的引用的对象数。

## 语法

    Get-AppLibAppDiskObjectReference -AppDiskUid <Guid> [-AdminAddress <String>] [<CommonParameters>]
    
    Get-AppLibAppDiskObjectReference [-AppDiskName] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

针对给定 AppDisk 名称或 UID，返回其他服务中的对象（例如 Broker 桌面组）拥有的引用数。

## 相关命令

- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| AppDiskName  | AppDisk 的名称。                                               | true  | false                 |                                       |
| AppDiskUid   | AppDisk 的唯一标识符。                                            | true  | true (ByPropertyName) |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDiskReferences  
此对象提供 AppDisk 的详细信息，并包含以下信息︰  
AppDiskUid <guid>  
AppDisk 的唯一标识符。  
AppDiskName <string>  
AppDisk 的名称。  
References <AppDiskUsage[]>  
指定引用类型的对象（例如 Broker 桌面组）和该类型对象拥有的引用数。

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
PartialData  
只返回了一部分可用数据。  
CouldNotQueryDatabase  
未定义用于获取数据库的查询。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与服务通信时发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Get-AppLibAppDiskObjectReference -AppDiskUid 7585f0de-192e-4847-a6d8-22713c3a2f42
    
              AppDiskUid    : 7585f0de-192e-4847-a6d8-22713c3a2f42
              AppDiskName   : Disk1
              References    : {Citrix.AppLibrary.Sdk.AppDiskUsage}
    

说明  
\---\---\-----  
返回通过 UID 引用的 AppDisk 引用。

### 示例 2

    C:\PS>Get-AppLibAppDiskObjectReference -AppDiskUid Disk1
    
              AppDiskUid    : 7585f0de-192e-4847-a6d8-22713c3a2f42
              AppDiskName   : Disk1
              References    : {Citrix.AppLibrary.Sdk.AppDiskUsage}
    

说明  
\---\---\-----  
返回通过名称引用的 AppDisk 引用。