# Get-AdminScope

Gets scopes configured for this site.

## 语法

    Get-AdminScope [[-Name] <String>] [-Id <Guid>] [-BuiltIn <Boolean>] [-Description <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves scopes matching the specified criteria. If no parameters are specified this cmdlet enumerates all scopes.

There is one special built-in scope, the 'All' scope.

To determine what objects are currently in a scope, use the Get-<prefix>ScopedObject from each of the relevant PowerShell snap-ins.

See about_Admin_Filtering for information about advanced filtering options.

## 相关命令

- [New-AdminScope](New-AdminScope.html)
- [Set-AdminScope](Set-AdminScope.html)
- [Rename-AdminScope](Rename-AdminScope.html)
- [Remove-AdminScope](Remove-AdminScope.html)
- [Set-AdminScopeMetadata](Set-AdminScopeMetadata.html)
- [Remove-AdminScopeMetadata](Remove-AdminScopeMetadata.html)

## 参数

| 名称                     | 说明                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------ | ----- | ------------------------------ | ------------------------------------- |
| 名称                     | Gets scopes with the specified name.                                                                   | false | true (ByValue, ByPropertyName) |                                       |
| ID                     | Gets the scope with the specified identifier.                                                          | false | true (ByPropertyName)          |                                       |
| BuiltIn                | Gets scopes with the specified value of the BuiltIn flag.                                              | false | false                          |                                       |
| 说明                     | Gets scopes with the specified description.                                                            | false | false                          |                                       |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。              | false | false                          |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                 | false | false                          |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Admin_Filtering for details.      | false | false                          | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                           | false | false                          | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                  | false | false                          |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。               | false | false                          | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Admin_Filtering for details. | false | false                          |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.DelegatedAdmin.Sdk.Scope

Get-AdminScope returns an object for each matching scope.

## 示例

### 示例 1

    C:\PS> Get-AdminScope -Name *Sales*
    

Description  
\---\---\-----  
List all scopes that contain the word 'Sales'.

### 示例 2

    C:\PS> Get-AdminScope -Id 21862daf-e529-4553-ba6e-f7543217111e
    

Description  
\---\---\-----  
Gets the details of the scope with the specific id.