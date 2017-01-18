# Set-AdminRole

Set the properties of a role.

## 语法

    Set-AdminRole [-InputObject] <Role[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminRole [-Id] <Guid[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminRole [-Name] <String[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-AdminRole command allows the description of custom roles to be updated. You cannot modify built-in roles.

To modify the permissions of a role, use the Add-AdminPermission and Remove-AdminPermission cmdlets.

To update the metadata associated with a role, use the Set-AdminRoleMetadata and Remove-AdminRoleMetadata cmdlets.

## 相关命令

- [New-AdminRole](New-AdminRole.html)
- [Get-AdminRole](Get-AdminRole.html)
- [Remove-AdminRole](Remove-AdminRole.html)
- [Rename-AdminRole](Rename-AdminRole.html)
- [Set-AdminRoleMetadata](Set-AdminRoleMetadata.html)
- [Remove-AdminRoleMetadata](Remove-AdminRoleMetadata.html)
- [Add-AdminPermission](Add-AdminPermission.html)
- [Remove-AdminPermission](Remove-AdminPermission.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the roles to update (by object).                                                                                                                             | true  | true (ByValue)        |                                       |
| ID           | Specifies the roles to update (by id).                                                                                                                                 | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the roles to update (by name).                                                                                                                               | true  | true (ByPropertyName) |                                       |
| 说明           | Supplies the new description value.                                                                                                                                    | false | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Role

You can pipe the roles to be updated into this command.

## 返回值

### None or Citrix.DelegatedAdmin.Sdk.Role

When you use the PassThru parameter, Set-AdminRole generates a Citrix.DelegatedAdmin.Sdk.Role object. Otherwise, this cmdlet does not generate any output.

## 示例

### 示例 1

    C:\PS> Set-AdminRole -Name Supervisor -Description "Helpdesk supervisor role"
    

Description  
\---\---\-----  
Change the description of the 'Supervisor' role.