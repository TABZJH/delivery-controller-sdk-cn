# Get-AppLibTask

Gets the task history for the AppLibrary Service.

## 语法

    Get-AppLibTask [[-TaskId] <Guid>] [-Type <JobType>] [-Active <Boolean>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a list of tasks that have run or are currently running within the AppLibrary Service.

## 相关命令

- [Remove-AppLibTask](Remove-AppLibTask.html)
- [Stop-AppLibTask](Stop-AppLibTask.html)
- [Switch-AppLibTask](Switch-AppLibTask.html)
- [Add-AppLibTaskMetadata](Add-AppLibTaskMetadata.html)
- [Remove-AppLibTaskMetadata](Remove-AppLibTaskMetadata.html)

## 参数

| 名称                     | 说明                                                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ----------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| TaskId                 | Specifies the task identifier to be returned.                                             | false | false |                                       |
| 类型                     | Specifies the type of task to be returned.                                                | false | false |                                       |
| 活动                     | Specifies whether currently running tasks only or completed tasks only are returned.      | false | false |                                       |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。 | false | false |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                    | false | false |                                       |
| ReturnTotalRecordCount | 请参阅 about_AppLib_Filtering 了解详细信息。                                                      | false | false | false                                 |
| MaxRecordCount         | 请参阅 about_AppLib_Filtering 了解详细信息。                                                      | false | false | false                                 |
| 跳过                     | 请参阅 about_AppLib_Filtering 了解详细信息。                                                      | false | false |                                       |
| SortBy                 | 请参阅 about_AppLib_Filtering 了解详细信息。                                                      | false | false |                                       |
| 过滤器                    | 请参阅 about_AppLib_Filtering 了解详细信息。                                                      | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                 | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes If the command fails, the following errors can result.  
Error Codes  
\---\---\-----  
UnknownObject  
One of the specified objects was not found.  
PartialData  
Only a subset of the available data was returned.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
CouldNotQueryDatabase  
The query required to get the database was not defined.  
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
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-AppLibTask -Active $false
    
    TaskId                   : cfe5b3a2-c471-443e-b05e-8658e672d10f
    Type                     : MyTask
    Host                     : NYSERVER
    Status                   : Finished
    CurrentOperation         :
    TaskProgress             : 100
    TaskExpectedCompletion   : 10/10/2012 15:28:12
    LastUpdateTime           : 10/10/2012 15:28:12
    ActiveElapsedTime        : 56
    DateFinished             : 10/10/2012 15:28:12
    TerminatingError         :
    ...
    

Description  
\---\---\-----  
Get all completed tasks for the AppLibrary Service.  
All tasks will publish at least the fields listed above, plus more related to the particular task being performed.