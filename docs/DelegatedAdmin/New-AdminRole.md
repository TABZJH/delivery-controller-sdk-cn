# New-AdminRole

Adds a new custom role to the site.

## 语法

    New-AdminRole [-Name] <String> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

New-AdminRole adds a new custom role object to the site. Once a new role has been created, you can add permissions to the role which define what operations the role conveys.

Roles represent a job function, such as 'help desk administrator', and contain a list of permissions that are required to perform that job function.

To assign a role to an administrator, you combine it with a scope which indicates what objects the role can operate on. This pair (also known as a 'right') can then be assigned to an administrator. See Add-AdminRight for further details.

The identifier of the new role is chosen automatically, and custom roles created with this cmdlet always have their BuiltIn flag set to false.

You cannot modify built-in roles, and only some license editions support custom roles.

## 相关命令

- [Get-AdminRole](Get-AdminRole.html)
- [Set-AdminRole](Set-AdminRole.html)
- [Rename-AdminRole](Rename-AdminRole.html)
- [Remove-AdminRole](Remove-AdminRole.html)
- [Set-AdminRoleMetadata](Set-AdminRoleMetadata.html)
- [Remove-AdminRoleMetadata](Remove-AdminRoleMetadata.html)
- [Add-AdminPermission](Add-AdminPermission.html)
- [Add-AdminRight](Add-AdminRight.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| 名称           | Specifies the name of the role. Each role in a site must have a unique name.                                                                                           | true  | true (ByPropertyName) |                                       |
| 说明           | Specifies the description of the role.                                                                                                                                 | false | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.DelegatedAdmin.Sdk.Role

The newly created role.## Notes Roles are created without any permissions. Use the Add-AdminPermission to add permissions.

## 示例

### 示例 1

    C:\PS> New-AdminRole -Name Supervisor -Description "My custom supervisor role"
    C:\PS> $list = Get-AdminRole 'Help Desk Administrator' | Select -Expand Permissions
    C:\PS> Add-AdminPermission -Role Supervisor -Permission $list
    C:\PS> Add-AdminPermission -Role Supervisor -Permission $extras
    C:\PS> Add-AdminRight -Administrator DOMAIN\TestUser -Role Supervisor -All
    

Description  
\---\---\-----  
Creates a new role called 'Supervisor', and then copies the permissions from the help desk role and adds some extras. Then gives this role (with the all scope) to user 'TestUser'.