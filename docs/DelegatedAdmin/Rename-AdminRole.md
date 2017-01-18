# Rename-AdminRole

Rename a role

## 语法

    Rename-AdminRole [-InputObject] <Role> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-AdminRole [-Id] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-AdminRole [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-AdminRole cmdlet changes the name of a role.

Role names must be unique, and you cannot modify the name of built-in roles.

## 相关命令

- [New-AdminRole](New-AdminRole.html)
- [Get-AdminRole](Get-AdminRole.html)
- [Set-AdminRole](Set-AdminRole.html)
- [Remove-AdminRole](Remove-AdminRole.html)
- [Set-AdminRoleMetadata](Set-AdminRoleMetadata.html)
- [Remove-AdminRoleMetadata](Remove-AdminRoleMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the role to rename (by object).                                                                                                                              | true  | true (ByValue)        |                                       |
| ID           | Specifies the role to rename (by id).                                                                                                                                  | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the role to rename (by name).                                                                                                                                | true  | true (ByPropertyName) |                                       |
| NewName      | Specifies the new name of the role.                                                                                                                                    | true  | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Role

You can pipe the role to be renamed into this command.

## 返回值

### None or Citrix.DelegatedAdmin.Sdk.Role

When you use the PassThru parameter, Rename-AdminRole generates a Citrix.DelegatedAdmin.Sdk.Role object. Otherwise, this cmdlet does not generate any output.

## 示例

### 示例 1

    C:\PS> Rename-AdminRole -Name Supervisor -NewName HelpDeskLead
    

Description  
\---\---\-----  
Renames the 'Supervisor' role to 'HelpDeskLead'.