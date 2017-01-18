# Add-AdminRight

Grants a given right to the specified administrator.

## 语法

    Add-AdminRight -Scope <String> -Role <String> -Administrator <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AdminRight -Role <String> -Administrator <String> [-All] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AdminRight [-InputObject] <Right[]> -Administrator <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use the Add-AdminRight cmdlet to add rights (role and scope pairs) to an administrator.

For convenience, you can use the -All parameter to specify the 'All' scope.

Use the Get-AdminAdministrator cmdlet to determine what rights an administrator has.

## 相关命令

- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Get-AdminEffectiveRight](Get-AdminEffectiveRight.html)
- [Remove-AdminRight](Remove-AdminRight.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| InputObject  | Specifies the rights to add from Right objects.                                                                                                                        | true  | true (ByValue) |                                       |
| 作用域          | Specifies the scope name or scope identifier.                                                                                                                          | true  | false          |                                       |
| 角色           | Specifies the role name or role identifier.                                                                                                                            | true  | false          |                                       |
| 管理员          | Specifies the name or SID of the administrator.                                                                                                                        | true  | false          |                                       |
| 全部           | Specifies the 'All' scope. This parameter avoids localization issues or having to type the identifier of the 'All' scope.                                              | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Right

You can pipe the rights to be added into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-AdminRight -Role 'Help Desk Administrator' -Scope London -Administrator DOMAIN\Admin1
    

Description  
\---\---\-----  
Assigns the 'Help Desk Administrator' role and 'London' scope to the 'Admin1' administrator.

### 示例 2

    C:\PS> Add-AdminRight -Role 'Full Administrator' -All -Administrator DOMAIN\Admin1
    

Description  
\---\---\-----  
Assigns the 'Full Administrator' role and 'All' scope to the 'Admin1' administrator.

### 示例 3

    C:\PS> $admin = Get-AdminAdministrator -Name DOMAIN\ExistingAdmin
    C:\PS> Add-AdminRight -InputObject $admin.Rights -Administrator DOMAIN\NewAdmin
    

Description  
\---\---\-----  
Copies the administrator rights from 'ExistingAdmin' to 'NewAdmin'.