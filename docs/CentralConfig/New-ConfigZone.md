# New-ConfigZone

Creates a new zone in the site.

## 语法

    New-ConfigZone [-Name] <String> [-Description <String>] [-ExternalUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creates a new zone in the site.

A Zone represents a subset of the site infrastructure residing in a particular geographical location.

By default any new zone will be marked as secondary. To specify the primary zone use the Set-ConfigSite cmdlet.

To associate controllers with a zone use the Set-ConfigService cmdlet.

## 相关命令

- [Get-ConfigZone](Get-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Set-ConfigService](Set-ConfigService.html)
- [Set-ConfigZone](Set-ConfigZone.html)
- [Rename-ConfigZone](Rename-ConfigZone.html)
- [Remove-ConfigZone](Remove-ConfigZone.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| 名称           | Specifies the name of the zone. Each zone in a site must have a unique name.                                                                                           | true  | true (ByPropertyName) |                                       |
| 说明           | Specifies the description of the zone.                                                                                                                                 | false | true (ByPropertyName) |                                       |
| ExternalUid  | Specifies the ExternalUid of the zone. This is used for cloud sites to link with the Citrix Resource Location.                                                         | false | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Configuration.Sdk.Zone

The newly created zone.

## 示例

### 示例 1

    C:\PS> $zone = New-ConfigZone -Name "London" -Description "London branch office"
    C:\PS> Set-ConfigSite -PrimaryZone $zone
    C:\PS> Set-ConfigService -Service "S-1-5-21-3384143951-2794580461-1950386216-8227" -Zone $zone
    

Description  
\---\---\-----  
Creates a new zone called 'London', marks it as the primary zone and moves a controller to that zone.