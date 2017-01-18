# Remove-AdminRight

Removes rights from an administrator.

## 语法

    Remove-AdminRight -Scope <String> -Role <String> -Administrator <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminRight -Role <String> -Administrator <String> [-All] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminRight [-InputObject] <Right[]> -Administrator <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This command removes rights from the specified administrator.

For convenience, you can use the -All parameter to specify the 'All' scope.

Use the Get-AdminAdministrator cmdlet to determine what rights an administrator has.

## 相关命令

- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Get-AdminEffectiveRight](Get-AdminEffectiveRight.html)
- [Add-AdminRight](Add-AdminRight.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Specifies the rights to remove.                                                                                                                                        | true  | true (ByValue) |                                       |
| 作用域          | Specifies the scope name or scope identifier.                                                                                                                          | true  | false          |                                       |
| 角色           | Specifies the role name or role identifier.                                                                                                                            | true  | false          |                                       |
| 管理员          | Specifies the name or SID of the administrator.                                                                                                                        | true  | false          |                                       |
| 全部           | Specifies the 'All' scope. This parameter avoids localization issues or having to type the identifier of the 'All' scope.                                              | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Right

You can pipe the rights to be removed into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> RemoveAdminRight -Role 'Help Desk Administrator' -Scope London -Administrator DOMAIN\Admin1
    

Description  
\---\---\-----  
Removes the 'Help Desk Administrator' role and 'London' scope from user 'Admin1'

### 示例 2

    C:\PS> $admin = Get-AdminAdministrator -Name DOMAIN\Admin
    C:\PS> Remove-AdminRight -InputObject $admin.Rights -Administrator DOMAIN\Admin
    

Description  
\---\---\-----  
Removes all rights from administrator 'Admin'.