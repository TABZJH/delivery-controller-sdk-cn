# Test-AdminAccess

Retrieves the scopes where the specified operation is permitted.

## 语法

    Test-AdminAccess [-Operation] <String[]> [-Annotate] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet evaluates what rights the current user has, and from these determines the scopes where the specified operation is permitted.

Operations are the indivisible unit of functionality that each XenDesktop service can perform, and usually correspond to individual cmdlets.

If you specify the -Annotate option or specify multiple operations to check, the resulting object is annotated with the operation the result relates to.

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| 操作           | The operation to query.                                    | true  | true (ByValue) |                                       |
| Annotate     | Annotates each result with the operation it relates to.    | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.DelegatedAdmin.Sdk.ScopeReference

The list of permissible scopes for the specified single operation.### PSObject The list of permissible scopes for each operation. This type of object is returned when the -Annotate option or multiple operations are specified.## Notes If the specified operation has unrestricted access a single object is returned representing the 'All' scope with a ScopeId of Guid.Empty (00000000-0000-0000-0000-000000000000).

## 示例

### 示例 1

    C:\PS> Test-AdminAccess -Operation 'Broker:GetCatalog'
    

Description  
\---\---\-----  
Queries the scopes where 'Broker:GetCatalog' is permitted.

### 示例 2

    C:\PS> Test-AdminAccess -Operation 'Broker:GetCatalog','Broker:GetMachine'
    

Description  
\---\---\-----  
Queries the scopes where 'Broker:GetCatalog' or 'Broker:GetMachine' are permitted.