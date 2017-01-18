# New-AdminAdministrator

Adds a new administrator to the site.

## 语法

    New-AdminAdministrator [-Name] <String> [-Enabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AdminAdministrator -Sid <String> [-Enabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

New-AdminAdministrator creates a new administrator object in the site. Once a new administrator has been created you can assign rights (role and scope pairs) to the administrator.

Administrator objects are used to determine what rights, and therefore what permissions a particular Active Directory user has through the various SDKs and consoles of the site.

When the Enabled flag of an administrator is set to false, any rights of the administrator are ignored by the system when performing permission checks.

## 相关命令

- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Set-AdminAdministrator](Set-AdminAdministrator.html)
- [Remove-AdminAdministrator](Remove-AdminAdministrator.html)
- [Set-AdminAdministratorMetadata](Set-AdminAdministratorMetadata.html)
- [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| 名称           | Specifies the user or group name in Active Directory that this administrator corresponds to.                                                                           | true  | true (ByPropertyName) |                                       |
| SID          | Specifies the SID (security identifier) of the user in Active Directory that this administrator corresponds to.                                                        | true  | true (ByPropertyName) |                                       |
| 已启用          | Specifies whether the new administrator starts off enabled or not.                                                                                                     | false | true (ByPropertyName) | True                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.DelegatedAdmin.Sdk.Administrator

The newly created administrator.

## 示例

### 示例 1

    C:\PS> New-AdminAdministrator -Name DOMAIN\TestUser
    

Description  
\---\---\-----  
Creates a new administrator object for user "DOMAIN\TestUser". It defaults to enabled.

### 示例 2

    C:\PS> New-AdminAdministrator -Sid S-1-2-34-1234567890-1234567890-1234567890-123
    

Description  
\---\---\-----  
Creates a new administrator object for user with SID "S-1-2-34-1234567890-1234567890-1234567890-123". It defaults to enabled.