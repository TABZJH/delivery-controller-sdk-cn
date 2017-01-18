# Remove-AdminScope

Removes a scope from the site.

## 语法

    Remove-AdminScope [-InputObject] <Scope[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminScope [-Id] <Guid[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminScope [-Name] <String[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-AdminScope cmdlet deletes scopes from the site.

You cannot remove the built-in 'All' scope.

An error will be produced if the scope being removed is currently assigned to an administrator unless you specify the -Force option. When -Force is specified, any rights that reference the scope are also removed.

## 相关命令

- [New-AdminScope](New-AdminScope.html)
- [Get-AdminScope](Get-AdminScope.html)
- [Set-AdminScope](Set-AdminScope.html)
- [Rename-AdminScope](Rename-AdminScope.html)
- [Set-AdminScopeMetadata](Set-AdminScopeMetadata.html)
- [Remove-AdminScopeMetadata](Remove-AdminScopeMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the scopes to remove (by scope object).                                                                                                                      | true  | true (ByValue)        |                                       |
| ID           | Specifies the scopes to remove (by scope id).                                                                                                                          | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the scopes to remove (by scope name).                                                                                                                        | true  | true (ByPropertyName) |                                       |
| Force        | Allow removal of scopes that are still in use.                                                                                                                         | false | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Scope

You can pipe the scopes to be deleted into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-AdminScope -Name Sales
    

Description  
\---\---\-----  
Remove the Sales scope.

### 示例 2

    C:\PS> Get-AdminScope -BuiltIn $false | Remove-AdminScope
    

Description  
\---\---\-----  
Attempt to remove all scopes (excluding the built-in 'All' scope). This fails if one of the scopes is assigned to an administrator.