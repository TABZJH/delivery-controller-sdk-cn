# Get-AppLibAppDisk

获取 AppDisk 列表。

## 语法

    Get-AppLibAppDisk [[-AppDiskName] <String>] [-AppDiskUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于检索定义的 AppDisk 列表。

## 相关命令

## 参数

| 名称                     | 说明                                                        | 是否必需？ | 管道输入  | 默认值                                  |
| ---------------------- | --------------------------------------------------------- | ----- | ----- | ------------------------------------ |
| AppDiskName            | AppDisk 的名称。                                              | false | false |                                      |
| AppDiskUid             | AppDisk 的唯一标识符。                                           | false | false |                                      |
| ScopeId                | 仅获取作用域匹配指定作用域标识符的结果。                                      | false | false |                                      |
| ScopeName              | 仅获取作用域匹配指定作用域名称的结果。                                       | false | false |                                      |
| ReturnTotalRecordCount | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false | false                                |
| MaxRecordCount         | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false | false                                |
| Skip                   | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| SortBy                 | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| Filter                 | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDisk  
此对象提供 AppDisk 的详细信息，并包含以下信息︰  
AppDiskUid <guid>  
AppDisk 的唯一标识符。  
AppDiskName <string>  
AppDisk 的名称。  
Description <string>  
AppDisk 的说明。  
HostingUnitUid <guid>  
架构使用的托管单元（来自托管单元 PowerShell 管理单元）的唯一标识符。  
HostingUnitName <string>  
架构使用的托管单元（来自托管单元 PowerShell 管理单元）的名称。  
VirtualDiskID <datetime>  
AppDisk 的 MCS 磁盘标识符。  
TaskId <guid>  
为 AppDisk 运行的任何当前任务的标识符。  
DiskLocalUid <guid>  
磁盘的 AppDNA 标识符。  
DiskLocalVersion <guid>  
磁盘的 AppDNA 版本指定符。  
Scopes <ScopeReference[]>  
AppDisk 所在的 Delegated Administration 作用域  
Task <Task<  
为 AppDisk 运行的任何当前任务的状态。  
State <appdiskstate>  
AppDisk 的整体生命周期状态  
StateString <string>  
字符串形式的 AppDisk 的整体生命周期状态  
AppDNAState <appdnastate>  
AppDisk 的 AppDNA 生命周期状态  
AppDNAStateString <string>  
字符串形式的 AppDisk 的 AppDNA 生命周期状态  
NewVersionCreationInProgress <bool>  
指示当前是否正在创建此 AppDisk 的新版本

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

    C:\PS>Get-AppLibAppDisk
    
    
              AppDiskUid                  : 7585f0de-192e-4847-a6d8-22713c3a2f42
              AppDiskName                 : Disk1
              Description                 : Microsoft Office 2013
              MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16
              MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79
              HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              HostingUnitName             : HostUnit1
              TaskId                      : 00000000-0000-0000-0000-000000000000
              DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6
              DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6
              DiskParentVersion           :
              Scopes                      :
              Task                        :
              State                       : Ready
              StateString                 : Ready
              AppDNAState                 : NoData
              AppDNAStateString           : NoData
    
              AppDiskUid                  : 43d82099-1fd7-4617-93f0-25b160813905
              AppDiskName                 : Disk2
              Description                 : Finance Suite
              MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16
              MasterDiskID                : 022cd6e4-34cb-3f7c-e02a-44ac404483b4
              HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              HostingUnitName             : HostUnit1
              TaskId                      : 00000000-0000-0000-0000-000000000000
              DiskLocalUid                : 5713AB4B-A021-4D9D-A04C-D80BB1126C19
              DiskLocalVersion            : 72967010-CA6F-467B-9D46-499EF595F02B
              DiskParentVersion           :
              Scopes                      :
              Task                        :
              State                       : Ready
              StateString                 : Ready
              AppDNAState                 : NoData
              AppDNAStateString           : NoData
    

说明  
\---\---\-----  
返回所有可用 AppDisk。

### 示例 2

    C:\PS>Get-AppDisk -AppDiskName Disk[0-1]
    
    
              AppDiskUid                  : 7585f0de-192e-4847-a6d8-22713c3a2f42
              AppDiskName                 : Disk1
              Description                 : Microsoft Office 2013
              MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16
              MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79
              HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              HostingUnitName             : HostUnit1
              TaskId                      : 00000000-0000-0000-0000-000000000000
              DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6
              DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6
              Scopes                      :
              Task                        :
              State                       : Ready
              StateString                 : Ready
              AppDNAState                 : NoData
              AppDNAStateString           : NoData
    

说明  
\---\---\-----  
返回名称为“Disk0”或“Disk1”的所有 AppDisk。