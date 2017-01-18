# Get-BrokerAdminFolder

Get the admin folders in this site.

## 语法

    Get-BrokerAdminFolder [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerAdminFolder [[-Name] <String>] [-DirectChildAdminFolders <Int32>] [-DirectChildApplications <Int32>] [-FolderName <String>] [-LastChangeId <Guid>] [-Metadata <String>] [-ParentAdminFolderUid <Int32>] [-TotalChildApplications <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerAdminFolder cmdlet gets admin folders in this site.

Without parameters, Get-BrokerAdminFolder gets all the admin folders that have been created. You can also use the parameters of Get-BrokerAdminFolder to filter the results to just the folders you're interested in. You can also identify folders by their UIDs or their FolderNames.

\---\---\---\---\---\---\---\----- BrokerAdminFolder Object A folder for use in the administration console for organising other objects. E.g. BrokerApplication objects

    -- DirectChildAdminFolders (System.Int32)
       The number of admin folders with this folder as a direct parent
    
    -- DirectChildApplications (System.Int32)
       The number of applications in this admin folder (does not include any applications in child folders)
    
    -- FolderName (System.String)
       The simple name of this folder within any parent folder
    
    -- LastChangeId (System.Guid)
       A random GUID assigned whenever there is a change anywhere in the hierarchy of admin folders below this node; each change updates this value on the changed folder and all parents all the way up to the root folder. Note that nodes below any change do not have their LastChangeId value updated
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Holds any metadata associated with the admin folder
    
    -- Name (System.String)
       The full name of the folder including the full parent hierarchy separated by back-slash characters and including a trailing back-slash
    
    -- ParentAdminFolderUid (System.Int32)
       The UID of the parent admin folder; the root folder references itself (zero)
    
    -- TotalChildApplications (System.Int32)
       The number of applications in this admin folder (including any applications in child folders)
    
    -- Uid (System.Int32)
       The unique ID of the admin folder (the root folder has the value zero)
    

## 相关命令

- [New-BrokerAdminFolder](New-BrokerAdminFolder.html)
- [Remove-BrokerAdminFolder](Remove-BrokerAdminFolder.html)

## 参数

| 名称                      | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                     | Gets only the admin folder with the specified unique identifier.                                                                                                                 | true  | false |                                                                                        |
| 名称                      | Gets admin folders matching the specified name (if no trailing backslash is supplied, it is assumed).                                                                            | false | false |                                                                                        |
| DirectChildAdminFolders | Gets admin folders with the specified number of child folders.                                                                                                                   | false | false |                                                                                        |
| DirectChildApplications | Gets admin folders with the specified number of applications (excluding those in sub-folders).                                                                                   | false | false |                                                                                        |
| FolderName              | Gets only the admin folders matching the specified simple folder name.                                                                                                           | false | false |                                                                                        |
| LastChangeId            | Gets only the admin folders with the specified value for LastChangeId.                                                                                                           | false | false |                                                                                        |
| 元数据                     | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                        | false | false |                                                                                        |
| ParentAdminFolderUid    | Gets only admin folders with the specified parent admin folder UID value.                                                                                                        | false | false |                                                                                        |
| TotalChildApplications  | Gets admin folders with the specified number of applications (including those in sub-folders).                                                                                   | false | false |                                                                                        |
| ReturnTotalRecordCount  | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount          | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                      | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                  | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                     | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                      | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress            | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.AdminFolder

Returns admin folders.

## 示例

### 示例 1

    C:\PS> Get-BrokerAdminFolder
    

Description  
\---\---\-----  
Return all administration folders.

### 示例 2

    C:\PS> Get-BrokerAdminFolder -Uid 1
    

Description  
\---\---\-----  
Get the administration folder with Uid 1.