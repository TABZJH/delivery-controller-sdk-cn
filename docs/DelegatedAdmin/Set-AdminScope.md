# Set-AdminScope

Set the properties of a scope.

## 语法

    Set-AdminScope [-InputObject] <Scope[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminScope [-Id] <Guid[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminScope [-Name] <String[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-AdminScope command allows the description of scopes to be updated. You cannot modify the built-in 'All' scope.

To change the contents of a scope, use the Add-<noun>Scope and Remove-<noun>Scope cmdlets from the corresponding PowerShell snap-in.

To update the metadata associated with a scope, use the Set-AdminScopeMetadata and Remove-AdminScopeMetadata cmdlets.

## 相关命令

- [New-AdminScope](New-AdminScope.html)
- [Get-AdminScope](Get-AdminScope.html)
- [Remove-AdminScope](Remove-AdminScope.html)
- [Rename-AdminScope](Rename-AdminScope.html)
- [Set-AdminScopeMetadata](Set-AdminScopeMetadata.html)
- [Remove-AdminScopeMetadata](Remove-AdminScopeMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the scopes to update (by object).                                                                                                                            | true  | true (ByValue)        |                                       |
| ID           | Specifies the scopes to update (by id).                                                                                                                                | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the scopes to update (by name).                                                                                                                              | true  | true (ByPropertyName) |                                       |
| 说明           | Supplies the new description value.                                                                                                                                    | false | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Scope

You can pipe the scopes to be updated into this command.

## 返回值

### None or Citrix.DelegatedAdmin.Sdk.Scope

When you use the PassThru parameter, Set-AdminScope generates a Citrix.DelegatedAdmin.Sdk.Scope object. Otherwise, this cmdlet does not generate any output.

## 示例

### 示例 1

    C:\PS> Set-AdminScope -Name Sales -Description "Sales department desktops"
    

Description  
\---\---\-----  
Change the description of the 'Sales' scope.