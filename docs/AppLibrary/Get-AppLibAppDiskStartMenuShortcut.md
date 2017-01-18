# Get-AppLibAppDiskStartMenuShortcut

获取 AppLibrary Service 的 AppDisk 开始菜单快捷方式。

## 语法

    Get-AppLibAppDiskStartMenuShortcut [-StartMenuShortcutUid <Guid>] [-AppDiskUid <Guid>] [-AppDiskName <String>] [-CommandLineExecutable <String>] [-CommandLineArguments <String>] [-Description <String>] [-DisplayName <String>] [-ShortcutPath <String>] [-WorkingDirectory <String>] [-IconUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

返回 AppLibrary Service 已知的 AppDisk 快捷方式列表。

## 相关命令

- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [Get-AppLibAppDiskStartMenuIcon](Get-AppLibAppDiskStartMenuIcon.html)

## 参数

| 名称                     | 说明                                                                                            | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| StartMenuShortcutUid   | 要检查的特定快捷方式的标识符。                                                                               | false | false |                                       |
| AppDiskUid             | 要检查的特定 AppDisk 的标识符。                                                                          | false | false |                                       |
| AppDiskName            | 要检查的特定 AppDisk 的名称。                                                                           | false | false |                                       |
| CommandLineExecutable  | 要匹配的快捷方式指示的可执行项                                                                               | false | false |                                       |
| CommandLineArguments   | 要匹配的快捷方式的命令行参数字符串                                                                             | false | false |                                       |
| Description            | 要匹配的快捷方式的说明                                                                                   | false | false |                                       |
| DisplayName            | 要匹配的快捷方式的显示名称                                                                                 | false | false |                                       |
| ShortcutPath           | 要匹配的快捷方式的路径                                                                                   | false | false |                                       |
| WorkingDirectory       | 要匹配的快捷方式的工作目录                                                                                 | false | false |                                       |
| IconUid                | 要检查的特定图标的标识符。                                                                                 | false | false |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_AppLib_Filtering 了解详细信息。 | false | false | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                  | false | false | 250                                   |
| Skip                   | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                         | false | false |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。      | false | false | 默认排序顺序是按名称或唯一标识符。                     |
| Filter                 | 获取与 PowerShell 样式过滤表达式匹配的记录。请参阅 about_AppLib_Filtering 了解详细信息。                              | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                    | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDiskShortcut

此对象提供快捷方式的详细信息及其用途，并包含以下信息︰AppDiskUid <guid> 拥有 AppDisk 的标识符 AppDiskName <string> 拥有 AppDisk 的标识符 IconUid <guid> 图标的标识符（如果存在）CommandLineExecutable <string> 快捷方式可执行属性 CommandLineArguments <string> 快捷方式参数属性 Description <string> 快捷方式说明属性 DisplayName <string> 快捷方式显示名称属性 ShortcutPath <string> 快捷方式路径属性 WorkingDirectory <string> 快捷方式工作目录## 注意 如果命令失败，会发生以下错误。  
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
              AppDiskName              : MyAppDisk
              IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297
              CommandLineExecutable    : "C:\Program Files (x86)\Mozilla Firefox\firefox.exe"
              CommandLineArguments     :
              Description              :
              DisplayName              : Mozilla Firefox
              ShortcutPath             : "C:\Users\Public\Desktop\Mozilla Firefox.lnk"
              WorkingDirectory         : "C:\Program Files (x86)\Mozilla Firefox"
    
    
              AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e
              AppDiskName              : MyAppDisk
              ...
    

说明  
\---\---\-----  
获取 AppLDisk“MyAppDisk”的所有快捷方式。