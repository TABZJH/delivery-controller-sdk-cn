# Get-AppLibAppDiskStartMenuIcon

获取 AppLibrary Service 的 AppDisk 开始菜单图标。

## 语法

    Get-AppLibAppDiskStartMenuIcon [-AppDiskUid <Guid>] [-AppDiskName <String>] [-IconUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

返回 AppLibrary Service 已知的 AppDisk 开始菜单图标列表。

## 相关命令

- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [Get-AppLibAppDiskStartMenuShortcut](Get-AppLibAppDiskStartMenuShortcut.html)

## 参数

| 名称                     | 说明                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AppDiskUid             | 要检查的特定 AppDisk 的标识符。                                      | false | false |                                       |
| AppDiskName            | 要检查的特定 AppDisk 的名称。                                       | false | false |                                       |
| IconUid                | 要检查的特定图标的标识符。                                             | false | false |                                       |
| ReturnTotalRecordCount | 请参阅 about_AppLib_Filtering 了解详细信息。                      | false | false | false                                 |
| MaxRecordCount         | 请参阅 about_AppLib_Filtering 了解详细信息。                      | false | false | false                                 |
| Skip                   | 请参阅 about_AppLib_Filtering 了解详细信息。                      | false | false |                                       |
| SortBy                 | 请参阅 about_AppLib_Filtering 了解详细信息。                      | false | false |                                       |
| Filter                 | 请参阅 about_AppLib_Filtering 了解详细信息。                      | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDiskShortcutIcon

此对象提供图标的详细信息及其用途，并包含以下信息︰IconUid <guid> 图标的标识符 IconData <string> 图标数据，以 Base-64 编码的字符串 AppDiskUid <guid> 拥有 AppDisk 的标识符## 注意 如果命令失败，会发生以下错误。  
错误代码  
\---\---\-----  
UnknownObject  
未找到其中一个指定的对象。  
PartialData  
只返回了一部分可用数据。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
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

    c:\PS>Get-AppLibStartMenuIcon -AppDiskName MyAppDisk
    
              AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e
              IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297
              IconData                 : "7Z3rc+I2EMC/d6b/A8PXBj94JTDAzJVLepnm1UDvMr25uQpbcCq2RCU5Cenc/1...."
    
              AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e
              IconUid                  : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6
              IconData                 : "s/HMKy5JzEtOVYAxPFNslVINE9NMDNPMdU0Sk5J0TYyT0nQtLFPTdFPNTRJTjQ...."
    
              ...
    

说明  
\---\---\-----  
获取 AppLDisk“MyAppDisk”的所有开始菜单图标。

### 示例 2

    c:\PS>Get-AppLibStartMenuIcon -IconUid "7b4c01c4-72fa-4c80-913d-c6df785f4297"
    
              AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e
              IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297
              IconData                 : "7Z3rc+I2EMC/d6b/A8PXBj94JTDAzJVLepnm1UDvMr25uQpbcCq2RCU5Cenc/1...."
    

说明  
\---\---\-----  
获取特定开始菜单图标“7b4c01c4-72fa-4c80-913d-c6df785f4297”。