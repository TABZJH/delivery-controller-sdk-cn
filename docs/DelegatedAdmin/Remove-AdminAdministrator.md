# Remove-AdminAdministrator

Removes administrators from the site.

## 语法

    Remove-AdminAdministrator [-InputObject] <Administrator[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminAdministrator -Sid <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AdminAdministrator [-Name] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-AdminAdministrator cmdlet deletes administrators from the site.

## 相关命令

- [New-AdminAdministrator](New-AdminAdministrator.html)
- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Set-AdminAdministrator](Set-AdminAdministrator.html)
- [Set-AdminAdministratorMetadata](Set-AdminAdministratorMetadata.html)
- [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the administrators to delete.                                                                                                                                | true  | true (ByValue)        |                                       |
| 名称           | Specifies the name of the administrator to delete.                                                                                                                     | true  | true (ByPropertyName) |                                       |
| SID          | Specifies the SID of the administrator to delete.                                                                                                                      | true  | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Administrator

You can pipe the adminstrators to be deleted into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-AdminAdministrator DOMAIN\TestUser
    

Description  
\---\---\-----  
Remove the administrator called "DOMAIN\TestUser".

### 示例 2

    C:\PS> Get-AdminAdministrator -Enabled $false | Remove-AdminAdministrator
    

Description  
\---\---\-----  
Remove all disabled administrators.