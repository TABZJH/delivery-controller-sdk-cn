# Set-ConfigZone

Set the description of the zone.

## 语法

    Set-ConfigZone [-InputObject] <Zone[]> [-NewUid <Guid>] [-Description <String>] [-ExternalUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigZone [-Uid] <Guid[]> [-NewUid <Guid>] [-Description <String>] [-ExternalUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigZone [-Name] <String[]> [-NewUid <Guid>] [-Description <String>] [-ExternalUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet allows you to change the description of a zone.

Controllers can be moved between zones using Set-ConfigService cmdlet. To mark zone as primary use Set-ConfigSite cmdlet.

To update the metadata associated with a zone, use the Set-ConfigZoneMetadata and Remove-ConfigZoneMetadata cmdlets.

To change the name of a zone use Rename-ConfigZone cmdlet.

## 相关命令

- [New-ConfigZone](New-ConfigZone.html)
- [Get-ConfigZone](Get-ConfigZone.html)
- [Rename-ConfigZone](Rename-ConfigZone.html)
- [Remove-ConfigZone](Remove-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Set-ConfigService](Set-ConfigService.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the zone to update (by zone object).                                                                                                                         | true  | true (ByValue)        |                                       |
| UID          | Specifies the zone to update (by Uid).                                                                                                                                 | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the zone to update (by name).                                                                                                                                | true  | true (ByPropertyName) |                                       |
| NewUid       | Specifies the new uid of the Zone object.                                                                                                                              | false | false                 |                                       |
| 说明           | Supplies the new description.                                                                                                                                          | false | false                 |                                       |
| ExternalUid  | Supplies the external Uid of the zone                                                                                                                                  | false | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.Zone

You can pipe the zones to be updated into this command.

## 返回值

### None or Citrix.Configuration.Sdk.Zone

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Zone object.

## 示例

### 示例 1

    C:\PS> Set-ConfigZone -Name 'Sydney' -Description 'Sydney branch office'
    

Description  
\---\---\-----  
Change the description of the 'Sydney' zone.