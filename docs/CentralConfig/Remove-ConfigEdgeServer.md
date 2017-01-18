# Remove-ConfigEdgeServer

Removes edge servers from the site

## 语法

    Remove-ConfigEdgeServer [-InputObject] <EdgeServer[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ConfigEdgeServer [-Uid] <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ConfigEdgeServer [-Name] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove edge servers from the site

## 相关命令

- [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
- [New-ConfigEdgeServer](New-ConfigEdgeServer.html)
- [Set-ConfigEdgeServer](Set-ConfigEdgeServer.html)
- [Rename-ConfigEdgeServer](Rename-ConfigEdgeServer.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| InputObject  | Specifies the edge server objects to delete                                                                                                                            | true  | true (ByValue)        |                                       |
| UID          | Specifies the UID of the edge server to delete                                                                                                                         | true  | true (ByPropertyName) |                                       |
| 名称           | Specifies the name of the edge server to delete                                                                                                                        | true  | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.EdgeServer

You can pipe the edge servers to be deleted to Remove-ConfigEdgeServer.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-ConfigEdgeServer -Name W2K12R1
    

Description  
\---\---\-----  
Removes an edge server with the specified name

### 示例 2

    C:\PS> Get-ConfigEdgeServer -ZoneName Secondary | Remove-ConfigEdgeServer
    

Description  
\---\---\-----  
Removes all edge servers from the zone named Secondary