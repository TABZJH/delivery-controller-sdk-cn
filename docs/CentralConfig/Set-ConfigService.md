# Set-ConfigService

Associate a Service with a Zone.

## 语法

    Set-ConfigService [-InputObject] <Service[]> [-Zone] <Zone> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigService [-Uid] <Int32[]> [-Zone] <Zone> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigService [-MachineName] <String[]> [-Zone] <Zone> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet is used to change the association between Services (referred also as Controllers) and Zones. A Service can be associated with only one Zone. By default, all services are assigned to the primary Zone.

## 相关命令

- [Get-ConfigService](Get-ConfigService.html)
- [Get-ConfigZone](Get-ConfigZone.html)
- [New-ConfigZone](New-ConfigZone.html)
- [Set-ConfigSite](Set-ConfigSite.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | The service to associate with a Zone.  
The service can be referenced by Service object, Machine Name, Machine DNS Name, SID or UID.                                   | true  | true (ByValue)        |                                       |
| UID          | Allows specifiying Services by the Service Uid                                                                                                                         | true  | true (ByPropertyName) |                                       |
| MachineName  | Allows specifiying Services by the Machine Name                                                                                                                        | true  | true (ByPropertyName) |                                       |
| 区域           | Specifies the target Zone.  
Zone can be referenced by Zone object, Name or UID.                                                                                       | true  | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Fma.Sdk.CommonCmdlets.Service

You can pipe the Services to be associated with the Zone.

## 返回值

### 无

## Notes For historical reasons Service is also referred as Controller in FMA services.

## 示例

### 示例 1

    C:\PS> Set-ConfigService -InputObject "S-1-5-21-3384143951-2794580461-1950386216-8227" -Zone "London"
    

Description  
\---\---\-----  
Associate a Service identified by SID with a Zone identified by name.