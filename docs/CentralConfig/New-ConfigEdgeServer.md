# New-ConfigEdgeServer

Creates a new edge server object

## 语法

    New-ConfigEdgeServer [-Name] <String> -MachineAddress <String> -Sid <String> -Uuid <Guid> [-Description <String>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

New-ConfigEdgeServer cmdlet creates a new edge server object.

An edge server is a machine which is running an agent service that performs a number of duties; these agent services are largely stateless and communicate back to the Citrix Workspace Cloud components in the cloud.

## 相关命令

- [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
- [Set-ConfigEdgeServer](Set-ConfigEdgeServer.html)
- [Rename-ConfigEdgeServer](Rename-ConfigEdgeServer.html)
- [Remove-ConfigEdgeServer](Remove-ConfigEdgeServer.html)

## 参数

| 名称             | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | --------------------------------------------------------------------- |
| 名称             | Specifies a name for the edge server. Each edge server must have a unique name.                                                                                        | true  | true (ByPropertyName) |                                                                       |
| MachineAddress | The address used when contacted by local components such as VDAs                                                                                                       | true  | true (ByPropertyName) |                                                                       |
| SID            | The Security Identifier value in tenant AD domain                                                                                                                      | true  | true (ByPropertyName) |                                                                       |
| Uuid           | The uuid used when being contacted from cloud components such as controllers                                                                                           | true  | true (ByPropertyName) |                                                                       |
| 说明             | Optional value to specify a description for the edge server                                                                                                            | false | true (ByPropertyName) |                                                                       |
| ZoneUid        | Specifies the Zone affinity for the edge server                                                                                                                        | false | true (ByPropertyName) | If no value is provided the edge server is placed in the Primary zone |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                       |
| AdminAddress   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。                                 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Configuration.Sdk.EdgeServer

The newly created edge server

## 示例

### 示例 1

    C:\PS> New-ConfigEdgeServer W2K12R2 -MachineAddress "EdgeSrv.address.com" -Sid 21-3623811015-3361044348-30300820
    

Description  
\---\---\-----  
This command creates an edge server