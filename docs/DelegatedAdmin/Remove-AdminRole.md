# Remove-AdminRole

Removes a role from the site.

## 语法

    Remove-AdminRole [-InputObject] <Role[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminRole [-Id] <Guid[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminRole [-Name] <String[]> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-AdminRole cmdlet deletes roles from the site.

You cannot remove built-in roles.

An error will be produced if the role being removed is currently assigned to an administrator unless you specify the -Force option. When -Force is specified, any rights that reference the role are also removed.

## 相关命令

- [New-AdminRole](New-AdminRole.html)
- [Get-AdminRole](Get-AdminRole.html)
- [Set-AdminRole](Set-AdminRole.html)
- [Rename-AdminRole](Rename-AdminRole.html)
- [Set-AdminRoleMetadata](Set-AdminRoleMetadata.html)
- [Remove-AdminRoleMetadata](Remove-AdminRoleMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the roles to remove (by role object).                                                                                                                        | true  | true (ByValue)        |                                       |
| ID           | Specifies the roles to remove (by role id).                                                                                                                            | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the roles to remove (by role name).                                                                                                                          | true  | true (ByPropertyName) |                                       |
| Force        | Allow removal of roles that are still in use.                                                                                                                          | false | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Role

You can pipe the roles to be deleted into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-AdminRole -Name Supervisor
    

Description  
\---\---\-----  
Remove the Supervisor role.

### 示例 2

    C:\PS> Get-AdminRole -BuiltIn $false | Remove-AdminRole
    

Description  
\---\---\-----  
Attempt to remove all custom roles. This fails if one of the roles is assigned to an administrator.