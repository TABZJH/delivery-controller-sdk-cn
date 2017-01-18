# Rename-ConfigZone

Rename a zone.

## 语法

    Rename-ConfigZone [-InputObject] <Zone> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-ConfigZone [-Uid] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-ConfigZone [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet renames a zone.

All zone names must be unique.

## 相关命令

- [New-ConfigZone](New-ConfigZone.html)
- [Set-ConfigZone](Set-ConfigZone.html)
- [Get-ConfigZone](Get-ConfigZone.html)
- [Remove-ConfigZone](Remove-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Set-ConfigService](Set-ConfigService.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the zone to rename (by zone object).                                                                                                                         | true  | true (ByValue)        |                                       |
| UID          | Specifies the zone to rename (by Uid).                                                                                                                                 | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the zone to rename (by name).                                                                                                                                | true  | true (ByPropertyName) |                                       |
| NewName      | Specifies the new name of the zone.                                                                                                                                    | true  | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.Zone

You can pipe the zone to be renamed into this command.

## 返回值

### None or Citrix.Configuration.Sdk.Zone

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the zone with new name.

## 示例

### 示例 1

    C:\PS> Rename-ConfigZone -Name 'New York' -NewName 'Manhattan'
    

Description  
\---\---\-----  
Renames the 'New York' zone to 'Manhattan'.