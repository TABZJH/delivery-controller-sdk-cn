# Set-AdminAdministrator

Sets the properties of an administrator.

## 语法

    Set-AdminAdministrator [-InputObject] <Administrator[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministrator -Sid <String[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministrator [-Name] <String[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-AdminAdministrator cmdlet is used to enable or disable an existing administrator.

You can specify the administrators to modify in a number of ways, by piping in existing objects, by passing existing objects with the InputObject parameter, or by specifying the names or SIDs explicitly.

## 相关命令

- [New-AdminAdministrator](New-AdminAdministrator.html)
- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Remove-AdminAdministrator](Remove-AdminAdministrator.html)
- [Set-AdminAdministratorMetadata](Set-AdminAdministratorMetadata.html)
- [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the administrators to modify.                                                                                                                                | true  | true (ByValue)        |                                       |
| 名称           | Specifies the names of the administrators to modify.                                                                                                                   | true  | true (ByPropertyName) |                                       |
| SID          | Specifies the SIDs of the administrators to modify.                                                                                                                    | true  | true (ByPropertyName) |                                       |
| 已启用          | Specifies the new value for the Enabled property.                                                                                                                      | false | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.DelegatedAdmin.Sdk.Administrator

You can pipe the adminstrators to be modified into this command.

## 返回值

### None or Citrix.DelegatedAdmin.Sdk.Administrator

When you use the PassThru parameter, Set-AdminAdministrator generates a Citrix.DelegatedAdmin.Sdk.Administrator object. Otherwise, this cmdlet does not generate any output.

## 示例

### 示例 1

    C:\PS> Get-AdminAdministrator -Enabled $false | Set-AdminAdministrator -Enabled $true
    

Description  
\---\---\-----  
Enable all administrators that are currently disabled.

### 示例 2

    C:\PS> Set-AdminAdministrator -Name DOMAIN\TestUser1,DOMAIN\TestUser2 -Enabled $true
    

Description  
\---\---\-----  
Enable two specific users specified by name (TestUser1 and TestUser2).