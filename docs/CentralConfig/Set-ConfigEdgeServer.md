# Set-ConfigEdgeServer

Changes the properties of an edge server

## 语法

    Set-ConfigEdgeServer [-InputObject] <EdgeServer[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigEdgeServer [-Uid] <Guid[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ConfigEdgeServer [-Name] <String[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-ConfigEdgeServer cmdlet sets properties of an edge server or a set of edge servers. The edge server can be specified by name or by one or more edge server instances can be passed to the command either by piping or by using the -InputObject parameter

## 相关命令

- [New-ConfigEdgeServer](New-ConfigEdgeServer.html)
- [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
- [Rename-ConfigEdgeServer](Rename-ConfigEdgeServer.html)
- [Remove-ConfigEdgeServer](Remove-ConfigEdgeServer.html)

## 参数

| 名称             | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject    | Specifies the edge server objects to modify.                                                                                                                           | true  | true (ByValue)        |                                       |
| UID            | Identifies the edge server to modify by its UID property.                                                                                                              | true  | true (ByPropertyName) |                                       |
| 名称             | Identifies the edge server to modify by name.                                                                                                                          | true  | true (ByPropertyName) |                                       |
| 说明             | Supplies the new value of the Description property.                                                                                                                    | false | false                 |                                       |
| MachineAddress | Supplies the new value of the MachineAddress property.                                                                                                                 | false | false                 |                                       |
| SID            | Supplies the new value of the SID property.                                                                                                                            | false | false                 |                                       |
| Uuid           | Supplies the new value of the Uuid property.                                                                                                                           | false | false                 |                                       |
| ZoneUid        | Allows moving the edge server to a new zone                                                                                                                            | false | false                 |                                       |
| PassThru       | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.EdgeServer

You can pipe the edge servers to be updated into this command.

## 返回值

### None or Citrix.Configuration.Sdk.EdgeServer

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Configuration.Sdk.EdgeServer object.

## 示例

### 示例 1

    C:\PS> Set-ConfigEdgeServer EdgeSrv1 -ZoneUid d8fe27fa-f33c-47ee-b6b5-80241f536164
    

Description  
\---\---\-----  
Associates the edge server 'EdgeSrv1' to a zone specified by its UID