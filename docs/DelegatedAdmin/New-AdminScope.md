# New-AdminScope

Adds a new scope to the site.

## 语法

    New-AdminScope [-Name] <String> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

New-AdminScope adds a new scope object to the site.

A scope represents a collection of objects. Scopes are used to group objects in a way that is relevant to the organization; for example, the set of delivery groups used by the Sales team.

You can create objects in particular scopes by specifying the -Scope parameter of a New- cmdlet for an object that can be scoped. You can then modify the contents of a scope with Add-<noun>Scope and Remove-<noun>Scope cmdlets from the correpsonding PowerShell snap-ins.

To assign a scope to an administrator, combine it with a role and then assign this pair (also known as a 'right') to an administrator. See Add-AdminRight for further details.

The identifier of the new scope is chosen automatically.

## 相关命令

- [Get-AdminScope](Get-AdminScope.html)
- [Set-AdminScope](Set-AdminScope.html)
- [Rename-AdminScope](Rename-AdminScope.html)
- [Remove-AdminScope](Remove-AdminScope.html)
- [Set-AdminScopeMetadata](Set-AdminScopeMetadata.html)
- [Remove-AdminScopeMetadata](Remove-AdminScopeMetadata.html)
- [Add-AdminRight](Add-AdminRight.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| 名称           | Specifies the name of the scope. Each scope in a site must have a unique name.                                                                                         | true  | true (ByPropertyName) |                                       |
| 说明           | Specifies the description of the scope.                                                                                                                                | false | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.DelegatedAdmin.Sdk.Scope

The newly created scope.

## 示例

### 示例 1

    C:\PS> New-AdminScope -Name Sales -Description "Sales department scope"
    C:\PS> Add-HypHypervisorConnectionScope -HypervisorConnectionName XenServer2 -Scope Sales
    C:\PS> Add-AdminRight -Administrator DOMAIN\TestUser -Role Hosting -Scope Sales
    

Description  
\---\---\-----  
Creates a new scope called 'Sales', adds a hypervisor connection object to the scope, and then assigns the right to use the hosting role on the Sales scope to the 'TestUser' administrator.