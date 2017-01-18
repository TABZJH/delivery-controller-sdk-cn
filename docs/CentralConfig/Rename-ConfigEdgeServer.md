# Rename-ConfigEdgeServer

Renames an edge server

## 语法

    Rename-ConfigEdgeServer [-InputObject] <EdgeServer> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-ConfigEdgeServer [-Uid] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-ConfigEdgeServer [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-ConfigEdgeServer cmdlet changes the name of an edge server. All edge servers in a site must have a unique name.

The following special characters are not allowed in the name: \ / ; : # . * ? = < > | \[ \] ( ) " ' `

## 相关命令

- [New-ConfigEdgeServer](New-ConfigEdgeServer.html)
- [Set-ConfigEdgeServer](Set-ConfigEdgeServer.html)
- [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
- [Remove-ConfigEdgeServer](Remove-ConfigEdgeServer.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the edge server to rename                                                                                                                                    | true  | true (ByValue)        |                                       |
| UID          | Specifies the UID of the edge server to rename                                                                                                                         | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the name of the edge server to rename                                                                                                                        | true  | true (ByPropertyName) |                                       |
| NewName      | Specifies the new name of the edge server                                                                                                                              | true  | false                 |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false                 | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.EdgeServer

You can pipe edge servers to Rename-ConfigEdgeServer.

## 返回值

### None or Citrix.Configuration.Sdk.EdgeServer

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Configuration.Sdk.EdgeServer object.

## 示例

### 示例 1

    C:\PS> Rename-ConfigEdgeServer -Name "Old name" -NewName "New Name"
    

Description  
\---\---\-----  
Renames the edge server with the name "Old name" to "New Name"

### 示例 2

    C:\PS>  Get-ConfigEdgeServer "Old name" | Rename-ConfigEdgeServer -NewName "New name"
    

Description  
\---\---\-----  
Renames the edge server with the name "Old name" to "New Name"