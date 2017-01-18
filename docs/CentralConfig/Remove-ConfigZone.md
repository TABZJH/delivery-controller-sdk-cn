# Remove-ConfigZone

Removes a zone from the site.

## 语法

    Remove-ConfigZone [-InputObject] <Zone[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ConfigZone [-Uid] <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ConfigZone [-Name] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet removes zones from a site.

You cannot remove a zone that is marked as primary or has associated controllers.

## 相关命令

- [Get-ConfigZone](Get-ConfigZone.html)
- [New-ConfigZone](New-ConfigZone.html)
- [Set-ConfigZone](Set-ConfigZone.html)
- [Rename-ConfigZone](Rename-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Set-ConfigService](Set-ConfigService.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the zone to remove (by zone object).                                                                                                                         | true  | true (ByValue)        |                                       |
| UID          | Specifies the zone to remove (by Uid).                                                                                                                                 | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the zone to remove (by Name).                                                                                                                                | true  | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.Zone

You can pipe the zones to be deleted into this command.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-ConfigZone -Name 'Sydney'
    

Description  
\---\---\-----  
Remove the zone specified by name. This fails if one of the zones has controllers associated.

### 示例 2

    C:\PS> Get-ConfigService | Set-ConfigService -Zone (Get-ConfigZone -IsPrimary $true)
    C:\PS> Get-ConfigZone -IsPrimary $false | Remove-ConfigZone
    

Description  
\---\---\-----  
Move all controllers to the primary zone. Remove all non-primary zones.